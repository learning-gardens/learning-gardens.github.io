#### Learning Gardens Website
###### Django-templated static website

—

Hi, this is a temporary holding pattern and sketch of [learning-gardens.co](learning-gardens.co).

—

#### Contents

###### Directories and Root files

- `/build` — build files, all of the actually edited components of this site
- `/labs.edouard.us` — ignore this
- `/posts` — blog posts and writings are located here
- `/static` - static assets (images, css, scripts, etc.)
- Don't mind the root files for now, everything that matters is in the `/build` directory.

###### Build files

If you'd like to modify or change how this site looks, pay attention.

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
  {% include 'nav-index.html' %}
  {% include 'groups.html' %}
  {% include 'posts.html' %}
{% endblock content %}
```

This is all to say that Django is pretty great for making re-usable component structures.
