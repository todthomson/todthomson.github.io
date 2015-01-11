---
layout: post
title: Jekyll on Windows
---

[Jekyll](http://http://jekyllrb.com)
is a simple blog-aware static website generator written in
[Ruby](https://www.ruby-lang.org)
in which you can author your content in
[Markdown](http://daringfireball.net/projects/markdown/)
and host your site in
[GitHub Pages](https://pages.github.com).

[Windows](http://windows.microsoft.com) is the penultimate operating system tour de force.

> _Whoa! That's great <span style="font-style: normal; font-weight: bold;">Tod</span>
> but you're way ahead of yourself as is usual for you..._

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
  <img style="display: inline-block" src="{{ site.baseurl }}public/images/posts/1/blog-all-the-things.jpg"
       alt="BLOG ALL THE THINGS" />
</div>

## Selecting a Blogging Engine

I spend a lot of my time giving free (and paid) advice to people on how to build software.
One maxim I find myself coming back to repeatedly is:

> List your requirements in order of priority and then draw a line under the
> [Minimum Viable Product](http://en.wikipedia.org/wiki/Minimum_viable_product).
> Once you know what your <abbr title="Minimum Viable Product">MVP</abbr> is plan the most pragmatic solution you can
> (keeping in mind the things under the line).

So because I know I should
[dog food](http://en.wikipedia.org/wiki/Eating_your_own_dog_food)
my own advice here are the list of requirements I came up with:

1. _Must generate a static site._<br />
I don't see the point of a webapp for static content.

2. _Must be able to host for free._<br />
What can I say? I'm a cheapskate.

3. _Must allow me to design (or modify) my own theme._<br />
I'm web developer after all so I want to be able to show what I can do.

4. _Must be able to "backup" and "track changes" to posts._<br />
I'd really hate to loose anything and I want to be able to revert back.

5. _Must provide feed-software integration._<br />
I want to increase the likelihood that people might read what I have to say.

6. _Must provide social media integration._<br />
I want to level up my personal brand and trigger discussions.

7. _Must be able to forward-date posts for future release._<br />
I want to be able to release on a regular schedule.

### Options Considered

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

In the end (as you already know) I selected Jekyll and here's why:

1. _Must generate a static site._<br />
It's designed to generate a static site.

2. _Must be able to host for free._<br />
You can host for free on _GitHub Pages_.

3. _Must allow me to design (or modify) my own theme._<br />
There are loads of [themes](http://jekyllthemes.org) that you can easily modify to suit your requirements.

4. _Must be able to "backup" and "track changes" to posts._<br />
Everything required to generate the static pages is plain text (no databases) and
it is simple to commit to a [git](http://git-scm.com) repository and push that to [GitHub](https://github.com).

5. _Must provide feed-software integration._<br />
Generates an ```atom.xml``` file in the root directory conforming to the
_[Atom Syndication Format](en.wikipedia.org/wiki/Atom_(standard))_
which is a good choice for syndicating your blog to readers.

6. _Must provide social media integration._<br />
I found a simple guide to [Twitter](https://twitter.com) and [Disqus](https://disqus.com/) integration
[here](http://joshualande.com/jekyll-github-pages-poole/) and Jekyll
has heaps of [plugins](http://jekyllrb.com/docs/plugins/) that extend it's functionality in interesting ways.

7. _Must be able to forward-date posts for future release._<br />
Jekyll has the concept of working with [drafts](http://jekyllrb.com/docs/drafts/)
and you can forward-date posts using git branches and just merge them when you want to release a new post.

So **all is well** regarding the requirements. _Next step: get it going on Windows._

## Installing Prerequisites

There are quite a few prerequisites required to get to the point where we can install Jekyll,
so here is a _by the seat of your pants_ guide to installing all the prerequisites.
I assume a reasonable proficiency with computers here so if you get into trouble feel free to
[email me at tod@todthomson.com](mailto:tod@todthomson.com)
or
[ask me on Twitter](https://twitter.com/todthomson).

> What follows is heavily inspired by Julian Thilo's [guide](http://jekyll-windows.juthilo.com).

### Git and GitHub (for Windows)

Because we are going to version our source code and content with _Git_,
"backup" our site to _GitHub_ and host our site on _GitHub Pages_,
we need to have some elementary understanding of Git and GitHub.
Please read [a beginner's guide to using Git on Windows](http://gitbyexample.org)
and the [GitHub Guide "Hello World"](https://guides.github.com/activities/hello-world/)
if you are not familiar with both.

> I really like [GitHub for Windows](https://windows.github.com) (and you might like it too)
> so if you don't currently have a Git environment installed go ahead and install this now.

### Node.js

If you want to be able to use [CoffeeScript](http://coffeescript.org)
for your scripts then you will need to download and install [Node.js](http://nodejs.org)
as Jekyll will use Node.js to compile your ```.coffee``` script files.
If you don't want CoffeeScript support then you can skip this step.

> Make sure to add Node.js to you [path](http://en.wikipedia.org/wiki/PATH_%28variable%29).

### Python and Pygments

If you are a software developer you will probably want to include code snippets in your blog posts.
GitHub Pages runs Jekyll in ```--safe``` mode which means that your only option today is
to use [Pygments](http://pygments.org) the [Python](https://www.python.org) generic syntax highlighter
which is included "out of the box" on GitHub Pages.

1. [Download](https://www.python.org/downloads/) and install Python 2.7.x
(make sure to add python to your PATH as part of the installation).

2. Open a new command prompt (so you will get Python in your PATH) and run
```python -m pip install Pygments``` which will install the syntax highlighter.

> Do not use Python 3.x as it is known not to work with Pygments.

If you are hosting on your own server or will pre-generate your "compiled" blog locally
and push the completed product to GitHub then you could use the pure-Ruby generic syntax highlighter
[Rouge](https://github.com/jneen/rouge).
Just check the
[list of supported languages and lexers](https://github.com/jneen/rouge/wiki/List-of-supported-languages-and-lexers)
if you are planning to blog about archaic or fringe languages.

### Ruby and the Ruby DevKit

Jekyll is written in Ruby so you will need Ruby if you want to do Jekyll.
The Ruby DevKit is required as Jekyll has dependencies that are
[wrappers](http://en.wikipedia.org/wiki/Wrapper_library)
around [C](http://en.wikipedia.org/wiki/C_%28programming_language%29) programs.

1. [Download](http://rubyinstaller.org/downloads/) and install the latest RubyInstaller for your version of Windows.<br />
I installed ```rubyinstaller-2.1.5-x64.exe``` as I'm on [64-bit](http://en.wikipedia.org/wiki/64-bit_computing) Windows.

2. [Download](http://rubyinstaller.org/downloads/) the Ruby DevKit matching the version of Ruby
you installed above.<br />
I downloaded ```DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe```.

3. Extract ```DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe``` to ```C:\RubyDevKit```.

4. Locate the ```Ruby 2.0.0-p598-x64``` folder in the Windows Start Menu and open ```Start Command Prompt with Ruby```.

5. ```cd c:\RubyDevKit``` and run ```ruby dk.rb init``` which will create the DevKit configuration file
```config.yml``` which you will use to point the DevKit at your Ruby installation.

6. Edit ```C:\RubyDevKit\config.yml``` adding ```- C:/Ruby21-x64``` to the last line of that file.
Yes the ```/``` should be a forward slash.

7. Run ```ruby dk.rb install``` which will install the DevKit.

But before we try to install Jekyll let's make sure everything is working.

### Confirm Prerequisites

To avoid problems down the road we are going to confirm that all the prerequisites have installed correctly.

> Here we will use _Git Shell_ ([MINGW32](http://en.wikipedia.org/wiki/MinGW)) that comes with _GitHub for Windows_ providing the
```which``` command.
If you don't have something that provides ```which``` you won't be able to complete these steps.

1. Open (or close and reopen) _Git Shell_.

2. Confirm Node.js is installed and is in your _path_ by running ```which node```
which should produce ```/c/Program Files/nodejs/node```.

3. Confirm Python is installed and is in your _path_ by running ```which python```
which should produce ```/c/Python27/python```.

4. Confirm Ruby is installed and is in your _path_ by running ```which ruby```
which should produce ```/c/Ruby21-x64/bin/ruby```.

If any of the above steps didn't yield the expected results then you will need to work out what has gone wrong before continuing.
Feel free to
[email me at tod@todthomson.com](mailto:tod@todthomson.com)
or
[ask me on Twitter](https://twitter.com/todthomson)
if you get really stuck.

## Installing Jekyll

OK so we are (finally) up to the point where we can actually install Jekyll! ***Huzzah***

> If you try to ```gem install jekyll``` now you will notice that you get an [SSL](http://en.wikipedia.org/wiki/SSL) error.
> To fix that error follow the steps described
> [here](https://gist.github.com/luislavena/f064211759ee0f806c88#manual-solution-to-ssl-issue).

1. You should now be able to ```gem install jekyll``` successfully.
Please be patient as it will look like nothing is happening for a very long time.

2. Navigate to ```C:\Ruby21-x64\lib\ruby\gems\2.1.0\gems\jekyll-2.5.3\lib\site_template``` and edit ```_config.yml```
adding ```highlighter: pygments``` to the bottom of that file.

3. Run ```gem install wdm``` to install the [Windows Directory Monitor](https://rubygems.org/gems/wdm) package.
This package will allow you to watch your blog post files for changes and recompile them automatically.
The command ```gem``` is used to interact with [RubyGems](http://en.wikipedia.org/wiki/RubyGems)
the package management system for Ruby.

4. Create a temporary directory ```c:\BlogTest```.
We will use that directory to test that Jekyll is working.
Run ```cd c:\BlogTest``` to change to that directory.

5. Next run ```jekyll new .``` which should
[scaffold](http://en.wikipedia.org/wiki/Scaffold_%28programming%29)
a basic Jekyll site for you.

6. Now run ```jekyll build``` and you should see output looking like the following:

<div style="text-align: center;">
  <img style="display: inline-block" src="{{ site.baseurl }}public/images/posts/1/jekyll-build.png"
       alt="Jekyll Build Output" />
</div>

> There is a known issue with Pygments (0.6.0) on Windows producing the warning
> ```cannot close fd before spawn``` which can safely be ignored.

### Don't ignore errors... Fix them! :D

TODO (CONTINUE FROM HERE)

## Testing Jekyll

> You can check ```http://localhost:4000``` for a [WEBrick](http://en.wikipedia.org/wiki/WEBrick) web server directory listing when running the ```serve``` command. If you see the empty directory listing 

> You can delete that directory (e.g. c:\BlogTest') after confirming it's all working correctly.

> You will need to ```CTRL+C``` to send the [SIGINT](http://en.wikipedia.org/wiki/Control-C) signal to close the process.











# other things...

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
