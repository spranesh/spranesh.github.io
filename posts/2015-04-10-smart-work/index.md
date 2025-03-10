# The busyness of work


Consider renting a house in a competitive and busy area. Imagine someone who
drives around many neighbourhoods looking for "To Let" signs. On finding one,
he notes down the contact number, revisits it during business hours after
scheduling an appointment, only to find that the house has a carpeted floor
which does not suit his allergies. He repeats the process over a few weeks
until he finds one suitable to his tastes and budget.

Now imagine someone spending a few hours on craigslist filtering to find three
houses fitting her budget and tastes. She sets up appointments with them over
the phone, and has a place to herself in less than a few working days.

While both our imaginary characters worked toward the same end goal, one went
about it a smarter way. Now, you are thinking to yourself, "What an absurdly
contrived example! No one would ever do this in real life".

I assure you it happens all the time - spending multiple minutes on a manual
end-to-end sanity check each edit-compile-test cycle as opposed to first
spending some time to build a unit test suite[^1].  Storing the result of every
sales call in an email as opposed to tracking coversions on a spreadsheet[^2].
Building features straight away as opposed to first user testing them with
mocks.  Improving the performance of a soon to be deprecated platform / API as
opposed to letting it run itself to oblivion[^3].  Sometimes, in fact, doing
nothing at all may be the best thing to do.

It has never been easier to do so much with such less effort and time. Our
primitive brains on the other hand, still tend to associate work done with time
and energy spent. This is especially true when we have to judge work that we do
not fully understand. Hearing how long it took someone to build a product often
convinces us of the difficulty involved. And conversely, the better we
understand the nature of work involved, the better our ability to avoid this
trap. As an example, hearing how short someone's commute is does not make us
think any higher of their driving skills!

As the lever of technology continues to entrench our lives, we continue to get
increasingly productive with the same amount of effort using tools, methods and
abstractions that an ever smaller set of people are familiar with.  If we do
not explicitly avoid the priming in our heads, we can very easily fall prey to
judging work by the busyness of it. While this is not the right thing to do, it
is often the easy thing to do.

How, then, can we overcome this? Choosing the right metrics is often an answer.
In the house hunting scenario, maybe we would like to measure the total time to
close, or how good the deal is. In the edit-compile-test scenario, the total
time to complete a task could be a good metric.

Metrics are only a psuedo-indicator though. The success of certain roles (such
as many engineering ones) is to prevent downstream mistakes, bugs, and "work"
from arising in the first place. Only a downward trend (assuming all other
things constant) can be measured, not the actual number of issues avoided or
dollars saved due to prudence.

In the end, familiarity with the kind of work is often the best way to judge
work. Otherwise, it's all too easy to fall into the "busy"ness pit.

[^1]: If the task is infrequently performed, the cost of automation may not be the worth it. XKCD has a fantastic [strip](http://xkcd.com/1205/) on this.

[^2]: Both of which take arguably the same time but the latter lends itself to future analysis. 

[^3]: Now, don't get me wrong. I'm not saying that doing it the latter way is always better. There are often very good reasons to doing things the harder way. For example, building a prototype first if the value of the product lies in user delight which a mock can never accomplish. Sometimes the harder way may be preferable since it can be more enjoyable. Choosing the harder way is okay as long as it is a deliberate one having weighed the pros and cons.  

