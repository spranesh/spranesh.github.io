# The joys of unique_ptr


C++11 introduces
[`unique_ptr`](http://en.cppreference.com/w/cpp/memory/unique_ptr) a wonderful
way to manage the most common pointer use cases without losing sanity. While
any pointer can point only to one object at a time, the `unique_ptr` construct
further enforces only one pointer to the object at any point of time; i.e, a
bijective mapping between pointers and objects. For example,

~~~cpp
std::unique_ptr<Foo> foo_ptr(new Foo());
~~~

is equivalent to saying that `foo_ptr` is the only pointer that points to the
object we passed into the constructor. The dereference and member access
methods are overriden so that `foo_ptr` looks like, sounds like and behaves
like a normal pointer. One can say `*foo_ptr` and `foo_ptr->method()` as
expected.  Also being consistent with denoting ownership, a `unique_ptr`, it
cannot be copied, only moved.[^1]

[^1]: None of this is radically new. `auto_ptr` was the first attempt at thinking about RIAA pointer semantics, but it did not work well with containers. C++11 fixes this with the addition of move semantics.

In short, a `unique_ptr` is

* cheap since it has very minimal overhead 
* lightweight as it does not need to reference count (an object can only have
  one valid unique pointer at any point of time) 
* and avoids memory leaks since it automatically frees the owned raw pointer when it goes
  out of scope via the destructor.

Even more useful, I think, is that they constrain ownership thereby avoiding the
reader to reference count[^2] as she reads through the code.

[^2]: I've often joked that readers of programs have to have execution models simultaneously operating in their heads. With programming languages that do not automatically manage memory such as C / C++, they also need to reference count pointers and references. IMO, this is the source of the increased programmer productivity that Spolsky refers to in his [API War](http://www.joelonsoftware.com/articles/APIWar.html) post.

### Return values work as expected

The trick to using, understanding and writing effective code with `unique_ptr`s
is to realize that a lot of moving happens under the hood. Copying or assigning
a unique pointer is disallowed, but (roughly speaking), the new C++11 move
semantics automatically kick in for rvalue copys.

As a result, returning unique pointers work as expected since C++ move
semantics converts the rvalue copy into a move:

~~~cpp
unique_ptr<Foo> FooFactory(ConfigObject C) {
      unique_ptr<Foo> foo_ptr;
      foo_ptr.reset(new Foo());
      // read config object
      // set desired properties on Foo
      return foo;
}

int main() {
  unique_ptr<Foo> foo_ptr = FooFactory(ConfigObject()); // Works!
}
~~~

### Ownership is made explicit

When a function accepts a pointer, questions of ownership arise. For
instance, imagine a function

~~~cpp
void ColorifyFoo(Foo* uncolored_foo);
~~~

Without peeking into the definition of ColorifyFoo, it is difficult to say if
ColorifyFoo were to own the pointer. It gets even more difficult to predict if
this were a class:

~~~cpp
class FooColorifier{
        FooColorifier(Foo *uncolored_foo); // Is uncolored_foo owned?
};
~~~

It is almost impossible to tell whether the FooColorifier class owns foo
without looking into what the class does with it. This is where unique pointers
shine. They explicitly prohibit such call sites! Trying to call a
unique_pointer version of the above function:

~~~cpp
void ColorifyFoo(unique_ptr<Foo> uncolored_foo);
~~~

in a manner like the following:

~~~cpp
unique_ptr<Foo> foo_ptr(new Foo());
ColorifyFoo(foo_ptr);  // compiler error!
~~~

would throw up a compiler error! One would have to explicitly move the pointer by calling it such:

~~~cpp
ColorifyFoo(move(foo_ptr));  // works!
// now foo_ptr is NULL
~~~

This makes ownership clear to the reader! Of course, if you only wanted to pass a reference to ColorifyFoo so that the pointer is not moved, you should, as you guessed right, pass a reference:

~~~cpp
void ReferenceVersionOfColorifyFoo(const Foo& uncolored_foo);

// callsite like the following:
unique_ptr<Foo> foo_ptr(new Foo());
ReferenceVersionOfColorifyFoo(*(foo_ptr));
~~~

### Usage with containers

Allowing containers to use pointers to their data rather than objects
themselves can significantly increase the speed of move-heavy operations like
sorting[^4]. However, just using containers with raw pointers is unsafe in
terms of memory. For instance, passing said containers around leads to keeping
track of who owns the container to appropriately manage said memory.

[^4]: And by a smaller amount, even lookup operations like searches due to cache coherence.

Due to rvalue references and move semantics, C++11 enables `unique_ptr` to be
effortlessly used with containers. This is where they go above and beyond
`auto_ptr`. Their usage with containers is as expected:

~~~cpp
vector<unique_ptr<Foo>> vector_of_foos;
unique_ptr<Foo> foo_ptr = new Foo();

vector_of_foos.push_back(foo_ptr);  // Throws compiler error!

vector_of_foos.push_back(move(foo_ptr));  // Works!
vector_of_foos.emplace_back(new Foo());  // Also works!
~~~

Move-heavy operations like `sort`, `shuffle` and `reverse` can really benefit
(sometimes even upto
[10x](http://eli.thegreenplace.net/2012/06/20/c11-using-unique_ptr-with-standard-library-containers))
via a judicious use of `unique_ptr`.


### The headfake

In reality, the `unique_ptr` is actually a very good
[headfake](http://en.wikipedia.org/wiki/Head_fake). Sure, they help manage
memory, but their real benefit is for the reader[^3]! Consistent usage of
`unique_ptr` makes ownership extremely clear.

Pointers have historically been semantically overloaded to handle both
ownership as well as cheap read copies.  Separating the two use cases by the
usage of `unique_ptr`[^5] to serve ownership and the usage of const references
to allow for cheap read copies removes the ambiguity and improves
programmer-read time. Programmer-read time is, of course, the most important time
constraint of all!

[^3]: One of the most frequently recurring readers is often a future version of the author!

[^5]: And it's sibling `shared_ptr` for the multiple ownership case.

