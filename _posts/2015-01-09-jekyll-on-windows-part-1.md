---
layout: post
title: Jekyll on Windows (part 1)
---

[Jekyll](http://http://jekyllrb.com)
is a simple blog-aware static website generator written in
[Ruby](https://www.ruby-lang.org)
in which you can author your content in
[Markdown](http://daringfireball.net/projects/markdown/)
and host your site in
[GitHub Pages](https://pages.github.com).

<del>
  [Windows](http://windows.microsoft.com) is the penultimate operating system tour de force.
</del>

<div class="message">
  Whoa! That's great <em>Tod</em> but you're way ahead of yourself as is usual for you...
</div>

So maybe I got a little ahead of myself there so let's go back to the beginning.

## History

I've been telling myself for the better part of ten years that I _need_ to have a blog.
Why?
Because
[all](http://www.hanselman.com)
[the](https://signalvnoise.com/writers/dhh)
[cool](http://blog.cleancoder.com)
[kids](http://haacked.com/)
[are](http://weblog.west-wind.com)
[doing](http://blog.davidebbo.com)
[it](http://zedshaw.com)
(and have been for ten years now).

But in all seriousness I told myself "Tod, you absolutely must":

<div style="text-align: center;">
  <img style="display: inline-block" src="{{ site.baseurl }}public/images/posts/2015-01-09/blog-all-the-things.jpg"
       alt="BLOG ALL THE THINGS" />
</div>

## Selecting a Blogging Engine

I spend a lot of my time giving free (and paid) advice to people on how to build software.
One maxim I find myself coming back to repeatedly is:

> List your requirements in order of priority and then draw a line under the
> [Minimum Viable Product](http://en.wikipedia.org/wiki/Minimum_viable_product) (MVP).
> Once you know what your MVP is plan the most pragmatic solution you can
> (keeping in mind the things under the line).

So because I know I should
[dog food](http://en.wikipedia.org/wiki/Eating_your_own_dog_food)
my own advice here are the list of requirements I came up with:

- Must generate a static site (I don't see the point of a webapp for static content).
- Must be able to host for free (what can I say? I'm a cheapskate).
- Must allow me to design (or modify) my own theme (I'm web developer after all so I want to be able to show what I can do).
- Must be able to "backup" and "track changes" to posts (I'd really hate to loose anything and I want to be able to revert).
- Must provide feed-software integration (so people might read what I have to say).
- Must provide social media integration (so I can level up my personal brand).
- Must be able to forward-date posts for future release (so I can release on a regular schedule).

## Options Considered

Based on this list and considering my technological comfort and appetite for disruption (which you should always do)
here is a list of some of the blogging engines I considered:

- [Ghost](https://ghost.org) built on [Node.js](http://nodejs.org)
  the result of a [Kickstarter](https://www.kickstarter.com) I was watching.
  It has a great [WYSIWYG](http://en.wikipedia.org/wiki/WYSIWYG) blog authoring tool which is compelling.
  You can host yourself "for free" or you can pay for [SaaS](http://en.wikipedia.org/wiki/Software_as_a_service) hosting.
- [Medium](https://medium.com) a blog-publishing platform that blurs the lines between regular blogging and
  [social journalism](http://en.wikipedia.org/wiki/Social_journalism).
- [Snow](https://github.com/Sandra/Sandra.Snow) a Jekyll inspired static site generation tool
  which was recommended by my colleague [Filip Ekberg](http://filipekberg.se/2014/05/21/goodbye-wordpress-hello-snow/).



Cum sociis natoque penatibus et magnis <a href="#">dis parturient montes</a>, nascetur ridiculus mus. *Aenean eu leo quam.* Pellentesque ornare sem lacinia quam venenatis vestibulum. Sed posuere consectetur est at lobortis. Cras mattis consectetur purus sit amet fermentum.

> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

Etiam porta **sem malesuada magna** mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.

## Inline HTML elements

HTML defines a long list of available inline tags, a complete list of which can be found on the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

- **To bold text**, use `<strong>`.
- *To italicize text*, use `<em>`.
- Abbreviations, like <abbr title="HyperText Markup Langage">HTML</abbr> should use `<abbr>`, with an optional `title` attribute for the full phrase.
- Citations, like <cite>&mdash; Mark otto</cite>, should use `<cite>`.
- <del>Deleted</del> text should use `<del>` and <ins>inserted</ins> text should use `<ins>`.
- Superscript <sup>text</sup> uses `<sup>` and subscript <sub>text</sub> uses `<sub>`.

Most of these elements are styled by browsers with few modifications on our part.

## Heading

Vivamus sagittis lacus vel augue rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.

### Code

Cum sociis natoque penatibus et magnis dis `code element` montes, nascetur ridiculus mus.

{% highlight js %}
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function("a", "b", "return a + b");

// Call the function
adder(2, 6);
// > 8
{% endhighlight %}

Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa.

### Gists via GitHub Pages

Vestibulum id ligula porta felis euismod semper. Nullam quis risus eget urna mollis ornare vel eu leo. Donec sed odio dui.

{% gist 5555251 gist.md %}

Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Nullam quis risus eget urna mollis ornare vel eu leo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec sed odio dui. Vestibulum id ligula porta felis euismod semper.

### Lists

Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.

* Praesent commodo cursus magna, vel scelerisque nisl consectetur et.
* Donec id elit non mi porta gravida at eget metus.
* Nulla vitae elit libero, a pharetra augue.

Donec ullamcorper nulla non metus auctor fringilla. Nulla vitae elit libero, a pharetra augue.

1. Vestibulum id ligula porta felis euismod semper.
2. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
3. Maecenas sed diam eget risus varius blandit sit amet non magna.

Cras mattis consectetur purus sit amet fermentum. Sed posuere consectetur est at lobortis.

<dl>
  <dt>HyperText Markup Language (HTML)</dt>
  <dd>The language used to describe and define the content of a Web page</dd>

  <dt>Cascading Style Sheets (CSS)</dt>
  <dd>Used to describe the appearance of Web content</dd>

  <dt>JavaScript (JS)</dt>
  <dd>The programming language used to build advanced Web sites and applications</dd>
</dl>

Integer posuere erat a ante venenatis dapibus posuere velit aliquet. Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Nullam quis risus eget urna mollis ornare vel eu leo.

### Images

Quisque consequat sapien eget quam rhoncus, sit amet laoreet diam tempus. Aliquam aliquam metus erat, a pulvinar turpis suscipit at.

![placeholder](http://placehold.it/800x400 "Large example image")
![placeholder](http://placehold.it/400x200 "Medium example image")
![placeholder](http://placehold.it/200x200 "Small example image")

### Tables

Aenean lacinia bibendum nulla sed consectetur. Lorem ipsum dolor sit amet, consectetur adipiscing elit.

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Upvotes</th>
      <th>Downvotes</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Totals</td>
      <td>21</td>
      <td>23</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Alice</td>
      <td>10</td>
      <td>11</td>
    </tr>
    <tr>
      <td>Bob</td>
      <td>4</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Charlie</td>
      <td>7</td>
      <td>9</td>
    </tr>
  </tbody>
</table>

Nullam id dolor id nibh ultricies vehicula ut id elit. Sed posuere consectetur est at lobortis. Nullam quis risus eget urna mollis ornare vel eu leo.

-----

Want to see something else added? <a href="https://github.com/poole/poole/issues/new">Open an issue.</a>
