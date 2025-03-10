# From Jekyll to Hugo


I've always used static generators to run my website. They are performant to
serve, and a good one can provide both flexibility and simplicity at the same
time. 

My first website (on my [alma mater's](http://www.cse.iitm.ac.in) 20MB hosting
space for every student) used a bunch of perl scripts to shove templates and
content together. A couple of years ago, when I was forced to move off my
department's hosting, I stumbled upon Jekyll.

### Why Hugo?

Jekyll is quite fantastic with flexibility, but the setup leaves a lot to be
desired.  One needs to have the right ruby gems, the correct python packages,
and if you use a theme like [minimal
mistakes](https://mademistakes.com/work/minimal-mistakes-jekyll-theme/), you'll
also need Grundle, Rake, and LESS.

In order to avoid managing multiple setups, I only ever set it up in one place
and writing posts had to be done by SSHing into a box. I know that there are
ways to automate and streamline the setup, but I did not have the time to learn
one more piece of indirection and layering.  The downside to this was two fold:

1. Writing is already a difficult task to begin with, and having to SSH into a
box meant even more activation energy.

2. I was very dependent on one box.

Earlier this year, I found out about [hugo](http://gohugo.io), another static
generator, but written in Go. It has one **enormous** advantage - the binary is
statically linked with no dependencies. This meant that running hugo was as
simple as downloading the latest release. No setups. No machine dependecies!

Written in Go, Hugo was also supposed to be super fast. Of course, all of this
came at the cost of the kind of hyper flexibility that Jekyll offered. Still, I
was immediately interested.

### Challenges (or what Jekyll does really well)

There were three challenges with moving to Hugo:

1. The minimal mistakes theme had not been ported. I would have to either find
an alternate theme or port the theme myself.

2. Jekyll automatically figures out related content by using a cosine similarity
metric between post word vectors. Hugo does not support this and it's still an [open
discussion](https://discuss.gohugo.io/t/show-a-list-of-related-content/1488).

3. Hugo does not allow categories to be part of the
[permalink](http://gohugo.io/extras/permalinks). In Jekyll, my posts would have
URLs like /category/post-name. I would break URLs going forward.

#### Soultion: The theme

After browsing a lot of [themes](http://themes.gohugo.io/) and not finding
anything suitable, I decided to port the Minimal Mistakes theme to hugo.
Minimal Mistakes is a huge theme, and I only ported the parts I use. I started
off by downloading the raw HTML page from my Jekyll site, and then working
backwards, replacing just the content and variables I needed.

I created partial templates for the header, navbar, banner, author bio and the
footer, and used these to write the following templates:

* index.html: for the [home](/) page with recent posts.
* _default/single.html: for [about](/about/), [projects](/projects/) and [latticework](/latticework/))
* section/post.html: for the [archive](/post/)
* post/single.html: for individual blog posts such as this one.

The latest version of Hugo (0.18) treats everything as a PAGE. This helped a
lot in my migration, since I did not have to special case frontmatter metadata
for non post pages.

I am quite satisfied with the final look. I plan to open source my port of the
theme after adding an example site.

#### Solution: Related posts

A solution was to patch the hugo source to add cosine similarity and support
related content. But this would mean customising the binary, and losing the
main benefit of the move to Hugo.

I eventually settled with using tags **and** categories to find related
content. The code to do this ended up relatively simple:

~~~html
{{ if index .Params "showrelated" | default true -}}
<small><b>You might also enjoy</b></small>
  <ul>
  {{ $page_link := .Permalink -}}
  {{ $categories := .Params.categories -}}
  {{ $tags := .Params.tags -}}
  {{ range .Site.Pages -}}
      {{ $has_common_tags := intersect $tags .Params.tags | len | lt 0 -}}
      {{ $has_common_cats := intersect $categories .Params.categories | len | lt 0 -}}
      {{ $page := . -}}
      {{ if (and (or $has_common_tags $has_common_cats) (ne $page_link $page.Permalink)) -}}
          <li><a href="{{ $page.Permalink }}">{{ $page.Title }}</a></li>
      {{ end -}}
  {{ end -}}
  </ul>
<hr />
{{ end -}}
~~~

If there was no other post with overlapping categories or posts, no related
posts would be rendered, but the `<ul>` tag would still be shown. To fix this
edge case, I added a post level param `showrelated` that I could set to false
to hide the whole section.

#### Solution: Keeping popular URLs

While Hugo does not allow for category in the permalink, it does allow for
[post aliases](https://gohugo.io/extras/aliases/). Using this was fairly straightforward:

~~~md
----
title: "..."
aliases:
- /old-category/old-name/
----
~~~

This enabled me to keep around links of my most popular posts
([example](/data/intuitive-axes)).

### Summary

Moving the site to Hugo took me the better part of 2 days, with the majority of
the time going into porting the theme. It's now easier to deploy, and much
easier to write. Time will tell about the robustness of this setup. Currently,
I <i class="fa fa-heart" aria-hidden="true"></i> Hugo!

