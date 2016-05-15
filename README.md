# reveal.js - Slide Show (S9) Template Pack

## Live Preview

See [`slides.html`](http://slideshow-templates.github.io/slideshow-reveal.js/slides.html).

For testing see
[`test.html`](http://slideshow-templates.github.io/slideshow-reveal.js/test.html) and
[`test.demo.html`](http://slideshow-templates.github.io/slideshow-reveal.js/test.demo.html).


## What's Slide Show (S9)?

A Ruby gem that lets you create slide shows and author slides in plain text
using a wiki-style markup language that's easy-to-write and easy-to-read.
More [Slide Show (S9) Project Site »](http://slideshow-s9.github.io)

## Intro

The [reveal.js](https://github.com/hakimel/reveal.js) package by Hakim El Hattab
bundled up into a Slide Show (S9) template pack.

Note, the package is configured to use the following headers in `slides.html`:

    author: Your Name Here
    title: Your Slide Show Title Here
    theme:  ribbon|material


## Try It Yourself - How To Use the Template Pack

If you want to try it yourself, install (fetch) the new template pack. Issue the command:

    $ slideshow install reveal.js

Or as an alternative clone the template pack using `git`. Issue the commands:

    $ cd ~/.slideshow/templates
    $ git clone https://github.com/slideshow-templates/slideshow-reveal.js.git

To check if the new template got installed, use the `list` command:

    $ slideshow list

Listing something like:

    Installed templates include:
       reveal.js (~/.slideshow/templates/reveal.js/reveal.js.txt)

Now you're ready to use it using the `-t/--template` switch. Example:

    $ slideshow build welcome.txt -t reveal.js

That's it.


## Questions? Comments?

Send them along to the [wwwmake forum/mailing list](http://groups.google.com/group/wwwmake).
Thanks!
