---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}


+ [Journal Papers](#Journal Papers)
+ [Conference papers](#Conference papers)
+ [Patents](#Patents)

{% for post in site.journalpapers reversed %}
  <p>{{ forloop.length }} co-authored journal papers have been published/accepted.</p>
{% endfor %}

{% for post in site.conferencepapers reversed %}
  <p>{{ forloop.length }} co-authored conference papers have been published/accepted.</p>
{% endfor %}


# Journal Papers


{% for post in site.journalpapers reversed %}
  {% include my-archive-single.html %}
{% endfor %}

# Conference papers

{% for post in site.conferencepapers reversed %}
  {% include my-archive-single.html %}
{% endfor %}

# Patents

+ hello world!

