---
layout: post
title: Jekyll on Windows
description: |
  Jekyll is a simple blog-aware static website generator written in
  Ruby in which you can author your content in Markdown
  and host your site in GitHub Pages.
  In this post I provide a "by the seat of your pants"
  no-frills guide to Jekyll on Windows.
---

![Get Started With Jekyll]({{ site.baseurl }}public/images/posts/1/jekyll.jpg)

[Jekyll](http://http://jekyllrb.com)
is a simple blog-aware static website generator written in
[Ruby](https://www.ruby-lang.org)
in which you can author your content in
[Markdown](http://daringfireball.net/projects/markdown/)
and host your site in
[GitHub Pages](https://pages.github.com).

[Windows](http://windows.microsoft.com) is the operating system _tour de force_.

> _Whoa! That's great <span style="font-style: normal; font-weight: bold;">Tod</span>
> but you're way ahead of yourself as is usual for you..._

So maybe I got a little ahead of myself there so let's go back to the beginning.

> If you like you can [jump straight to](#installing-prerequisites) the installation guide.

## History

I've been telling myself for the better part of ten years that I **need** to have a blog.
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

I told myself "Tod, you absolutely must!".

<div style="text-align: center;">
  <img style="display: inline-block;"
       src="{{ site.baseurl }}public/images/posts/1/blog-all-the-things.jpg"
       alt="BLOG ALL THE THINGS" />
</div>

And I might have something interesting to say one day and nowhere to say it.

## Selecting a Blogging Engine

I spend a lot of my time giving free (and paid) advice to people on how to build software.
One maxim I find myself coming back to repeatedly is:

> List your requirements in order of priority and then draw a line under the
> [Minimum Viable Product](http://en.wikipedia.org/wiki/Minimum_viable_product).
> Once you know what your <abbr title="Minimum Viable Product">MVP</abbr> is plan the most pragmatic solution you can
> while keeping in mind the things under the line.

So because I know I should
[dog food](http://en.wikipedia.org/wiki/Eating_your_own_dog_food)
my own advice here are my requirements.

1. _Must generate a static site._<br />
I don't see the point in hosting a web application for a static site.

2. _Must be able to host for free._<br />
What can I say? I'm a cheapskate!

3. _Must allow me to design (or modify) my own theme._<br />
I'm a web developer (after all) so I want to be able to show what I can do.

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
here is a list of some of the blogging engines I considered.

- _[Ghost](https://ghost.org)_ built on [Node.js](http://nodejs.org)
the result of a [Kickstarter](https://www.kickstarter.com) I was watching.
It has a great [WYSIWYG](http://en.wikipedia.org/wiki/WYSIWYG) blog authoring tool which is compelling.
You can host yourself "for free" or you can pay for [SaaS](http://en.wikipedia.org/wiki/Software_as_a_service) hosting.

- _[Medium](https://medium.com)_ a blog-publishing platform that blurs the lines between regular blogging and
[social journalism](http://en.wikipedia.org/wiki/Social_journalism).

- _[Sandra.Snow](https://github.com/Sandra/Sandra.Snow)_ a Jekyll-inspired static site generation tool
which comes recommended by my colleague [Filip Ekberg](http://filipekberg.se/2014/05/21/goodbye-wordpress-hello-snow/).

In the end (as you already know) I selected Jekyll and here's why:

1. _Must generate a static site._<br />
It's designed to generate a static site.

2. _Must be able to host for free._<br />
You can host for free on GitHub Pages.

3. _Must allow me to design (or modify) my own theme._<br />
There are [themes](http://jekyllthemes.org) that you can easily modify to suit your requirements.

4. _Must be able to "backup" and "track changes" to posts._<br />
Everything required to generate the static pages is plain text (no databases) and
it is simple to commit to a [Git](http://git-scm.com) repository and push that to [GitHub](https://github.com).

5. _Must provide feed-software integration._<br />
Generates an ```atom.xml``` file in the root directory conforming to the
_[Atom Syndication Format](en.wikipedia.org/wiki/Atom_(standard))_
which is a good choice for syndicating your blog to readers.

6. _Must provide social media integration._<br />
I found a simple guide to [Twitter](https://twitter.com) and [Disqus](https://disqus.com/) integration
[here](http://joshualande.com/jekyll-github-pages-poole/) and Jekyll
has [plugins](http://jekyllrb.com/docs/plugins/) that extend it's functionality in interesting ways.

7. _Must be able to forward-date posts for future release._<br />
Jekyll has the concept of working with [drafts](http://jekyllrb.com/docs/drafts/)
and you can forward-date posts using Git branches and just merge them when you want to release a new post.

So **all is well** regarding the requirements. _Next step: get it going on Windows_.

## Installing Prerequisites

There are quite a few prerequisites required to get to the point where we can install Jekyll,
so here is my **by the seat of your pants** guide to installing all the prerequisites.
I assume a reasonable proficiency with computers here so if you get into trouble feel free to
[email me at _tod@todthomson.com_](mailto:tod@todthomson.com)
or
[ask me on _Twitter_](https://twitter.com/todthomson).

> What follows is heavily sourced from **Julian Thilo's [guide](http://jekyll-windows.juthilo.com)**.

### Git and GitHub (for Windows)

Because we are going to version our source code and content with Git,
"backup" our site to GitHub and host our site on GitHub Pages,
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

> If you use Node.js make sure to add it to your _[path](http://en.wikipedia.org/wiki/PATH_%28variable%29)_.

### Python and Pygments

If you are a software developer you will probably want to include code snippets in your blog posts.
GitHub Pages runs Jekyll in ```--safe``` mode which means that your only option today is
to use [Pygments](http://pygments.org) the [Python](https://www.python.org) generic syntax highlighter
which is included "out of the box" on GitHub Pages.

1. [Download](https://www.python.org/downloads/) and install Python 2.7.x
(make sure to add Python to your _path_ as part of the installation).

2. Open a new command prompt (so you will get Python in your _path_) and run
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

> Here we will use Git Shell ([MINGW32](http://en.wikipedia.org/wiki/MinGW)) that comes with GitHub for Windows providing the
```which``` command.
If you don't have something that provides the ```which``` command you won't be able to complete these steps.

1. Open (or close and reopen) Git Shell.

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

6. Now run ```jekyll build``` and you should see the following output.

<div style="text-align: center;">
  <img style="display: inline-block" src="{{ site.baseurl }}public/images/posts/1/jekyll-build.png"
       alt="Jekyll Build Output" />
</div>

## Testing Jekyll

Next we are going to test to make sure that our blog scaffold generated correctly
and that we can preview our blog locally.

Run ```jekyll serve``` to recompile the blog and host it in the [WEBrick](http://en.wikipedia.org/wiki/WEBrick)
web server.

<div style="text-align: center;">
  <img style="display: inline-block" src="{{ site.baseurl }}public/images/posts/1/jekyll-serve.png"
       alt="Jekyll Serve Output" />
</div>

Browse to ```http://localhost:4000``` and you should be able to see your blog.

<div style="text-align: center;">
  <img style="display: inline-block" src="{{ site.baseurl }}public/images/posts/1/jekyll-example.png"
       alt="Jekyll Example Page" />
</div>

> You will need to ```CTRL+C``` to send the [SIGINT](http://en.wikipedia.org/wiki/Control-C) signal to close the process.

## Pygments vs Rouge

As I have already talked about Pygments is the default syntax highlighter used in GitHub Pages
and if we weren't hosting our blog on GitHub Pages we could use the pure-Ruby syntax highlighter Rouge.

The default ```_config.yml``` generated when you run ```jekyll new .``` looks like this.

{% highlight yaml %}
# Site settings
title: Your awesome title
email: your-email@domain.com
description: ""
baseurl: ""
url: "http://yourdomain.com"
twitter_username: jekyllrb
github_username:  jekyll

# Build settings
markdown: kramdown
highlighter: rouge
{% endhighlight %}

As you can see Jekyll now defaults to ```highlighter: rouge```.
We will need to change that to ```highlighter: pygments``` for our blog to work on GitHub Pages.

> You can delete ```c:\BlogTest``` now you have confirmed Jekyll is working.

## Hosting on GitHub Pages

Now you have the basic skeleton of a blog you can set up hosting on GitHub Pages.

1. Run ```gem install bundler``` to install [Bundler](http://bundler.io) the package bundle manager.

2. Run ```gem install github-pages``` to install the support package.

3. Run ```gem install redcarpet``` to install [Redcarpet](https://github.com/vmg/redcarpet) a Ruby Markdown-parser.

4. Follow these [instructions](https://pages.github.com) to set up a repository and hosting for your new blog.

5. Check your site is working at ```http://username.github.io```.

> It may take up to 30 minutes to become live so you might need to move on and come back to this step later...

## Update "All the Things"!

There are some known bugs (on Windows) in some packages we're dependant upon
so you might like to run ```gem update``` to make sure all your packages are up to date before continuing.
You will need to be very patient as this will take an eternity.

> If you get the following error then keep re-running ```gem update``` until it completes successfully.

<pre>
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    bad response Service Unavailable 503
    (https://api.rubygems.org/api/v1/dependencies?gems=rake)
</pre>

## Level up your Blog with Poole and Hyde

> _That's great <span style="font-style: normal; font-weight: bold;">Tod</span>
> but I want my blog to look awesome..._

So you want your blog to look a little better than just the default Jekyll theme?
As I mentioned earlier there are
[loads](http://jekyllthemes.org)
[of](https://github.com/jekyll/jekyll/wiki/Themes)
[cool](http://themeforest.net/category/static-site-generators/jekyll)
[themes](https://mademistakes.com/work/jekyll-themes/)
[out](http://themes.jekyllbootstrap.com)
[there](https://www.jekyllthemes.net)
you can choose from.
It didn't take me long to find something that I really liked that should be easy to modify to suit my needs.

[Poole](http://getpoole.com) was _designed and developed by
[@mdo](https://twitter.com/mdo) to provide a clear and concise foundational setup for any Jekyll site.
It does so by furnishing a full vanilla Jekyll install with example templates, pages, posts, and styles._

[Hyde]() is a _brazen two-column Jekyll theme that pairs a prominent sidebar with uncomplicated content based on Poole._

All you need to do to get going to start with an empty folder and clone either Poole or Hyde into it.
Then you just hack away at the template partials and CSS etc until you get something you're happy with.

The layout and styling you see here is based on Hyde.

## Coda

**I really hope** you find this blog post useful.
It might seem at first that there is a lot to do to get your blog set up with Jekyll,
but it's worth it as the end product is very transparent and easy to hack on.

Feel free to drop me a
[line](mailto:tod@todthomson.com)
or a
[tweet](https://twitter.com/todthomson)
if you have any feedback, suggestions or if anything doesn't work for you as described.
I'm more than happy to help.

Until next time.... _[Make Mine Jekyll](http://en.wikipedia.org/wiki/Comic_book_letter_column)!_
