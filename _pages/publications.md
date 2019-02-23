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


+ [Journal Papers](#JournalPapers)
+ [Conference papers](#ConferencePapers)
+ [Patents](#Patents)


{% for post in site.journalpapers reversed %}
  {% if forloop.last %}
  <p>{{ forloop.length }} co-authored journal papers have been published/accepted.</p>
  {% endif %}
{% endfor %}


{% for post in site.conferencepapers reversed %}
  {% if forloop.last %}
  <p>{{ forloop.length }} co-authored conference papers have been published/accepted.</p>
  {% endif %}
{% endfor %}


{% for post in site.patents reversed %}
  {% if forloop.last %}
  <p>{{ forloop.length }} co-held patents have been published.</p>
  {% endif %}
{% endfor %}


# <a name="JournalPapers"></a>Journal Papers


{% for post in site.journalpapers reversed %}
  {% include my-archive-single.html %}
{% endfor %}

# <a name="ConferencePapers"></a>Conference Papers

{% for post in site.conferencepapers reversed %}
  {% include my-archive-single.html %}
{% endfor %}

# <a name="Patents"></a>Patents

{% for post in site.patents reversed %}
  {% include my-archive-single.html %}
{% endfor %}

