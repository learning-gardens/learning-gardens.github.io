#### Learning Gardens Website
###### Django-templated static website

—

Hi, this is a temporary holding pattern and sketch of [learning-gardens.co](learning-gardens.co).

—

#### Contents

###### Directories and Root files

- `/_build` — (not live) build files, all of the actually edited components of this site
  - `/.build` — Ignore this completely, Cactus uses it.
  - `/pages` — This is likely to be our most-edited directory. Markdown posts are located in `/pages/posts/...`, and all of the html components are simply in the root of this directory. `index.html`, which is the first-land page, can be seen to house nothing but components, which are compiled into the static `index.html`. This process occurs with each 'main' page.
  - `/plugins` — Django is a python-based framework, so python plugins go here. These haven't been edited thus far.
  - `/static` — All static assets should go in here, including css, fonts, images, and javescript. Right now fonts and javascript won't be found here, since we're inlining javascript within `base.html` and using Google Fonts.
  - `/templates` — This houses `base.html` and `post.html`, which form the wrappers of the base page (including scripts, meta tags, and css references), and the posts page(s). These probably won't get edited often, unless we redesign the entire site.
  - `config.json` — Ignore this completely, Cactus uses it.  
- `/posts` — (live) blog posts and writings are located here
- `/static` - (live) static assets (images, css, scripts, etc.)
- Don't mind the root files for now, everything that matters development-wise is in the `/_build` directory.

###### Build files — Overview

**If you'd like to modify or change how this site looks, *pay attention*.**

This site is built using a neat static site generator called [Cactus](). Cactus make building websites fast and easy and quickly previewable. I'm not sure if it's a good tool for building sites that will scale, but it is nice for sketching and prototyping stuff. 

Cactus uses the [Django](https://docs.djangoproject.com/en/1.10/topics/templates/#the-django-template-language) templating method, which I'm 90% sure is similar to how Jekyll works, in the sense that it allows you to create a small component such as `nav-index.html`, which might look like this:

```html
<section class="fl w-100">
  <div class="fl w-100 w-50-m w-25-l pa3-m pv2-l ph4-l">
    <p class="f4 lh-copy measure">
      Learning Gardens is a meta-organization to support grassroots non-institutional learning, exploration, and community-building.<br><br>
      At its simplest, it is advice on how to start a reading group. At its most complex, you and your friends can achieve nirvana.
    </p>
  </div>
  <div class="fl w-100 w-50-m w-25-l pa3-m pv2-l ph4-l">
    <p class="f4 lh-copy measure">
      <!-- <a class="link" href="https://lg-slack-automate.herokuapp.com/">Join our slack</a><br> -->
      <a class="link dim blue" href="{% url '/info.html' %}">Learn more</a><br>
      <a class="link dim blue" href="{% url '/join.html' %}">Join our slack</a><br>
      <a class="link dim blue" href="https://github.com/learning-gardens" target="_blank">Visit our github</a><br>
      <!-- <a class="link dim blue" href="support.html">Support Learning Gardens</a><br> -->
      <a class="link dim blue" href="mailto:hello@learning-gardens.co">Send us a message</a><br>
    </p>
  </div>
  <div class="fl w-100 w-50-m w-25-l pa3-m pv2-l ph4-l"></div>
  <div class="fl w-100 w-50-m w-25-l pa3-m pv2-l ph4-l">
    <p class="f4 lh-copy measure">
      “Étudiants sans Frontières”
    </p>
  </div>
</section>
```
and reference it super, quickly in another file, such as this `index.html`:

```html
{% extends "base.html" %}

{% block content %}
  {% include 'nav-index.html' %} <-- this thing represents that big chunk above
  {% include 'groups.html' %}
  {% include 'posts.html' %}
{% endblock content %}
```

This is all to say that Django is pretty great for making re-usable component structures.

At the moment, Learning Gardens has five primary sections which would be of importance in its information architecture:

- Index
- Info
- Join
- Resources
- Posts

Each of these sections are composed of multiple html components, which are arranged into the core section file.

###### Build files — CSS

For the sake of getting this site built quickly and in a structurally-sound manner, I've used a neat methodology-as-tooling called [Tachyons](http://tachyons.io/), which follows a line of thinking known as ['Functional CSS'](http://www.jon.gold/2015/07/functional-css/), which seeks to eradicate many of the problems one may deal with while writing CSS.

On first look, this site's HTML files may look insane with their seemingly bloated `class="so much shit going on in here"` designations, but I highly encourage anyone who wants to contribute to this project site read though [these components](http://tachyons.io/components/) and [this documentation](http://tachyons.io/docs/) to get a quick sense of how rad this system is. As someone who hates fucking with CSS, this framework is quite the godsend.

