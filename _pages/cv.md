---
layout: archive
title: "Curriculum Vitae"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

+ [Education](#Education)
+ [Project Experience](#ProjectExperience)
+ [Publications](#Publications)
+ [Invited Talks](#InvitedTalks)
+ [Awards & Honors](#AwardsAndHonors)
+ [Skills](#Skills)

# <a name="Education"></a>Education

* B.S. in GitHub, GitHub University, 2012
* M.S. in Jekyll, GitHub University, 2014
* Ph.D in Version Control Theory, GitHub University, 2018 (expected)
  

# <a name="ProjectExperience"></a>Project Experience

  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
 


# <a name="Publications"></a>Publications

*Journal Papers*
------
  <ul>{% for post in site.journalpapers reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
 
*Conference Papers*
------
  <ul>{% for post in site.conferencepapers reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
*Patents*
------
  <ul>{% for post in site.patents reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
  
# <a name="InvitedTalks"></a>Invited Talks

 <ul>{% for post in site.talks reversed%}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>
  
 
# <a name="AwardsAndHonors"></a>Awards & Honors

* Skill 1
* Skill 2
  * Sub-skill 2.1
  * Sub-skill 2.2
  * Sub-skill 2.3
* Skill 3


# <a name="Skills"></a>Skills

* Skill 1
* Skill 2
  * Sub-skill 2.1
  * Sub-skill 2.2
  * Sub-skill 2.3
* Skill 3
