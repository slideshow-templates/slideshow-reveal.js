

# Missing Features from reveal.js Templates by Adolfo Villafiorita

See <https://github.com/avillafiorita/slideshow-reveal.js/blob/95617d67102b333463bebabcfc95344c9650027d/doc/s9-reveal.textile>

- [ ] vertical slides - up/down missing
- [ ] theme support with property missing
- [ ] and some more

```
 <link rel="stylesheet" href="reveal.js/css/reveal.min.css">
    <% if @headers['theme'] =~ /theme not found/ %>
      <link rel="stylesheet" href="reveal.js/css/theme/default.css" id="theme">
    <% else %>
      <link rel="stylesheet" href="reveal.js/css/theme/<%= @headers['theme'] %>.css" id="theme">
    <% end %>
    
 ...

<!-- For syntax highlighting -->
    <link rel="stylesheet" href="reveal.js/lib/css/zenburn.css">

    <!-- If the query includes 'print-pdf', include the PDF print sheet -->
    <script>
     if( window.location.search.match( /print-pdf/gi ) ) {
       var link = document.createElement( 'link' );
       link.rel = 'stylesheet';
       link.type = 'text/css';
       link.href = 'css/print/pdf.css';
       document.getElementsByTagName( 'head' )[0].appendChild( link );
     }
    </script>
    
<div class="reveal">

      <!-- Any section element inside of this container is displayed as a slide -->
      <div class="reveal">
        <div class="slides">
          <% @slides.each do |slide| %>
            <% if slide.classes.include?("down-open") %>
              <section class="<%= slide.classes %>">
                <% elsif slide.classes.include?("down-close") %>
              </section>
            <% else %>
              <section "<%= slide.classes %>">
                <%= slide.content %>
              </section>
            <% end %>
          <% end %>
        </div>
      </div>
    </div>    
    
 // Full list of configuration options available here:
     // https://github.com/hakimel/reveal.js#configuration
     Reveal.initialize({
       controls: true,
       progress: true,
       history: true,
       center: true,
       theme: Reveal.getQueryHash().theme, // available themes are in /css/theme
       transition: Reveal.getQueryHash().transition || 'default', // default/cube/page/concave/zoom/linear/fade/none
       // Parallax scrolling
       // parallaxBackgroundImage: 'https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg',
       // parallaxBackgroundSize: '2100px 900px',
       // Optional libraries used to extend on reveal.js
       dependencies: [
         { src: 'reveal.js/lib/js/classList.js', condition: function() { return !document.body.classList; } },
         { src: 'reveal.js/plugin/markdown/marked.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },
         { src: 'reveal.js/plugin/markdown/markdown.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },
         { src: 'reveal.js/plugin/highlight/highlight.js', async: true, callback: function() { hljs.initHighlightingOnLoad(); } },
         { src: 'reveal.js/plugin/zoom-js/zoom.js', async: true, condition: function() { return !!document.body.classList; } },
         { src: 'reveal.js/plugin/notes/notes.js', async: true, condition: function() { return !!document.body.classList; } }
       ]
     });
```



original reamde/notes (in textile):

```
title: S9 Reveal theme
author: Adolfo Villafiorita
description: How to use the reveal theme with S9
date: 2013-08-09

!SLIDE
h1. Heads Up

* reveal is a S9 template to output reveal.js slides.
* reveal.js is a framework for easily creating beautiful presentations using HTML. You'll need a browser with support for CSS 3D transforms to see it in its full glory.
* with the template you get all the advantages of S9 + most (if not all) the advantages of S9.

<aside class="notes">
  Oh hey, these are some notes. They'll be hidden in your presentation, but you can see them if you open the speaker notes window (hit 's' on your keyboard).
</aside>


!SLIDE down-open

h2. S9 Advantages

* metadata
* slides are written in a markup language (e.g., Textile or Markdown), simplifying reuse and collaborative editing and isolating content from rendering.
* S9 supports ERB (Embedded Ruby), meta-tags, plugins, and code highlighting
* S9 templating system is relatively easy

h2. Metadata

Just add directives at the beginning (?) of your presentation:

<pre>
title: S9 Reveal theme
author: Adolfo Villafiorita
description: How to use the reveal theme with S9
date: 2013-08-09
</pre>

h2. ERB

With S9 you can execute Ruby code, using ERB markup.

Try:

<pre>
  < %= 2 * 5 %>
</pre>

The result is: <%= 2 * 5 %>

h2. Plugins

Plugins exist to extend S9 functions.

Custom helpers can be also defined.  Have a look at "S9 plugins":http://slideshow-s9.github.io/plugins.html for more details.

*Notice that some (e.g., two columns and incremental display) do not seem to work.  Use fragments for incremental display.*

h2. Comments

S9 allows one to comment lines using the percent sign:

* A line starting with the % sign is ignored.
* A percent sign in any other position is passed literally

!SLIDE down-close

!SLIDE down-open

h2. Vertical Slides

Slides can be nested inside of other slides, try pressing <a href="#" class="navigate-down">down</a>.

<a href="#" class="image navigate-down">
   <img width="178" height="238" src="https://s3.amazonaws.com/hakim-static/reveal-js/arrow.png" alt="Down arrow">
</a>

Use the special markup:

<pre>
  !SLIDE down-open
  ...
  !SLIDE down-close
</pre>

to mark the slides which develop vertically, rather than horizontally.

h2. Basement Level 1

Press down or up to navigate.

h2. Basement Level 2

Cornify

<a class="test" href="http://cornify.com">
  <img width="280"
       height="326"    
       src="https://s3.amazonaws.com/hakim-static/reveal-js/cornify.gif" 
       alt="Unicorn">
</a>

h2. Basement Level 3

That's it, time to go back up.

<a href="#/2" class="image">
   <img width="178" height="238" 
        src="https://s3.amazonaws.com/hakim-static/reveal-js/arrow.png"
        alt="Up arrow" style="-webkit-transform: rotate(180deg);">
</a>

!SLIDE down-close

!SLIDE down-open

h2. Reveal Features

Using the reveal template allows one to use several features of reveal, among which:

* vertical slides (well, you know it by now)
* point of views
* transition styles
* themes
* fragments
* export to PDF
* pauses
* responsiveness

h2. Point of Views

Press *ESC* to enter the slide overview.

Hold down alt and click on any element to zoom in on it using "zoom.js":http://lab.hakim.se/zoom-js. Alt + click anywhere to zoom back out.

h2. Transition Styles</h2>

You can select from different transitions, like: <br>

<a href="?transition=cube#/transitions">Cube</a> -
<a href="?transition=page#/transitions">Page</a> -
<a href="?transition=concave#/transitions">Concave</a> -
<a href="?transition=zoom#/transitions">Zoom</a> -
<a href="?transition=linear#/transitions">Linear</a> -
<a href="?transition=fade#/transitions">Fade</a> -
<a href="?transition=none#/transitions">None</a> -
<a href="?#/transitions">Default</a>

(TODO: assign ID to slide)

h2. Themes

Reveal.js comes with a few themes built in: <br>

<a href="?theme=sky#/themes">Sky</a> -
<a href="?theme=beige#/themes">Beige</a> -
<a href="?theme=simple#/themes">Simple</a> -
<a href="?theme=serif#/themes">Serif</a> -
<a href="?theme=night#/themes">Night</a> -
<a href="?#/themes">Default</a>

(TODO: assign ID to slide)

<small>
 * Theme demos are loaded after the presentation which leads to flicker. In production you should load your theme in the <code>&lt;head&gt;</code> using a <code>&lt;link&gt;</code>.
</small>

h2. Fragmented Views

 Hit the next arrow...

 <p class="fragment">... to step through ...</p>
 <ol>
   <li class="fragment"><code>any type</code></li>
   <li class="fragment"><em>of view</em></li>
   <li class="fragment"><strong>fragments</strong></li>
</ol>

<aside class="notes">
  This slide has fragments which are also stepped through in the notes window.
</aside>


h2. Fragment Styles

There's a few styles of fragments, like:

p(fragment grow). grow

p(fragment shrink). shrink

p(fragment roll-in). roll-in

p(fragment fade-out). fade-out

p(fragment highlight-red). highlight-red

p(fragment highlight-green). highlight-green

p(fragment highlight-blue). highlight-blue

h2. Export to PDF

Presentations can be "Exported to PDF":https://github.com/hakimel/reveal.js#pdf-export below is an example that's been uploaded to SlideShare.

<iframe id="slideshare" 
        src="http://www.slideshare.net/slideshow/embed_code/13872948" 
        width="455" height="356" 
        style="margin:0;overflow:hidden;border:1px solid #CCC;border-width:1px 1px 0;margin-bottom:5px" 
        allowfullscreen> 
</iframe>
<script>
 document.getElementById('slideshare').attributeName = 'allowfullscreen';
</script>

h2. Take a Moment

Press b or period on your keyboard to enter the 'paused' mode. This mode is helpful when you want to take distracting slides off the during a presentation.

h2. Works in Mobile Safari

Try it out! You can swipe through the slides and pinch your way to the overview.

!SLIDE down-close

h2. Markup

Some examples of markup are included in the next slides.

h2. Marvelous Unordered List

* No order here
* Or here
* Or here
* Or here
		
h2. Fantastic Ordered List

# One is smaller than...
# Two is smaller than...
# Three!

h2. Clever Quotes

These guys come in two forms, inline: <q cite="http://searchservervirtualization.techtarget.com/definition/Our-Favorite-Technology-Quotations"> &ldquo;The nice thing about standards is that there are so many to choose from&rdquo;</q> and block:

bq.  &ldquo;For years there has been a theory that millions of monkeys typing at random on millions of typewriters would reproduce the entire works of Shakespeare. The Internet has proven this theory to be untrue.&rdquo;

h2. Pretty Code

<pre>
<code data-trim contenteditable class="javascript">
function linkify( selector ) {
  if( supports3DTransforms ) {

    var nodes = document.querySelectorAll( selector );

    for( var i = 0, len = nodes.length; i &lt; len; i++ ) {
      var node = nodes[i];

      if( !node.className ) ) {
        node.className += ' roll';
      }
    };
  }
}
</code>
</pre>

... courtesy of "highlight.js":http://softwaremaniacs.org/soft/highlight/en/description/

h2. Code Highlighting

S9 also provides code highlighting.

<% coderay :lang => 'ruby', :line_numbers => :inline do %> 
  puts 'Hallo Welt!   
<% end %> 

One advantage is that source code can be read from a file.

See http://slideshow.rubyforge.org/code.html or http://pragdave.blogs.pragprog.com/pragdave/2008/05/our-take-on-pre.html for more details.

h2. Horizontal Rulers

A sequence of "-" generates an horizontal ruler:

------------------------------------------------------------------------------

h2. Intergalactic Interconnections

You can link between slides internally, <a href="#/2/3">like this</a>.

h2. Spectacular image!

<a class="image" href="http://lab.hakim.se/meny/" target="_blank">
 <img width="320" height="299"      
      src="http://s3.amazonaws.com/hakim-static/portfolio/images/meny.png" 
      alt="Meny">
</a>

h2. Global State

Set <code>data-state="something"</code> on a slide and <code>"something"</code> will be added as a class to the document element when the slide is open. This lets you apply broader style changes, like switching the background.

h2. Todo

Still missing:

* Assigning IDs to slides (to generate internal links)
* Examples of S9 and Reveal links between slides
* Support for data- markup (e.g., to exploit S9 background and transitions).  It should be supported by S9, btw.


% <section data-state="customevent">
%   <h2>Custom Events</h2>
% Additionally custom events can be triggered on a per slide basis by binding to the <code>data-state</code> name.
%  <pre><code data-trim contenteditable style="font-size: 18px; margin-top: 20px;">
% Reveal.addEventListener( 'customevent', function() {
% 	console.log( '"customevent" has fired' );
% } );
%  </code></pre>
% </section>

% !SLIDE down-open

% !SLIDE data-background="#007777"
% <h2>Slide Background</h2>

% Set <code>data-background="#007777"</code> on a slide to change the full page background
% to the given color. All CSS color formats are supported.
%  <a href="#" class="image navigate-down">
%    <img width="178" height="238" 
%         src="https://s3.amazonaws.com/hakim-static/reveal-js/arrow.png" 
%         alt="Down arrow">
%  </a>

% <section data-background="https://s3.amazonaws.com/hakim-static/reveal-js/arrow.png">
%   <h2>Image Backgrounds</h2>
%   <pre><code>&lt;section data-background="image.png"&gt;</code></pre>
% </section>

%  <section data-background="https://s3.amazonaws.com/hakim-static/reveal-js/arrow.png"
% data-background-repeat="repeat" 
% data-background-size="100px">
%   <h2>Repeated Image Backgrounds</h2>

%   <pre>
%   <code style="word-wrap: break-word;">
%     &lt;section data-background="image.png" data-background-repeat="repeat" data-background-size="100px"&gt;
%   </code>
%   </pre>
%  </section>

%  <section data-transition="linear"
%           data-background="#4d7e65" 
%           data-background-transition="slide">
%    <h2>Background Transitions</h2>

%   Pass reveal.js the <code>backgroundTransition: 'slide'</code> config argument to make backgrounds slide rather than fade.
%  </section>

%  <section data-transition="linear" 
%           data-background="#8c4738"
%           data-background-transition="slide">
%  <h2>Background Transition Override</h2>

%  You can override background transitions per slide by using <code>data-background-transition="slide"</code>.

%  </section>

% !SLIDE down-close
```
