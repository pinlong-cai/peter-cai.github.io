---
layout: archive
title: "Journalpapers"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

Journal Papers
-----------

{% for post in site.journalpapers reversed %}
  {% include my-archive-single.html %}
{% endfor %}

Conference papers
---------
+ hello world!

Patents
-----------

+ hello world!

