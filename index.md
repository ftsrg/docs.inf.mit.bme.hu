---
layout: page
title: FTSRG
tagline: Fault Tolerant Systems Research Group
---

[Fault Tolerant Systems Research Group – Homepage](https://inf.mit.bme.hu/en/)

## Organizations

{% assign organizations = site.data.catalog.organizations %}
{% for organization in organizations %}* [{{ organization.name }}](https://github.com/{{organization.name}}): {{ organization.purpose }}
{% endfor %}

## General

{% assign repositories = site.data.catalog.general %}
{% for repository in repositories %}* [{{ repository.name }}](https://github.com/FTSRG/{{ repository.repository }}): {{ repository.content }}
{% endfor %}

## Courses

{% assign courses = site.data.catalog.courses %}
{% for course in courses %}* [{{ course.name }}](https://github.com/FTSRG/{{ course.repository }}): {{ course.content }}
{% endfor %}

## Projects

{% assign projects = site.data.catalog.projects %}
{% for project in projects %}
#### {{ project.name }}

Homepage: [{{ project.name }}]({{ project.homepage }})

  {% for repository in project.repositories %}* [{{ repository.name }}](https://github.com/FTSRG/{{ repository.repository }}): {{ repository.description }}
  {% endfor %}

{% endfor %}

## Papers

{% assign papers = site.data.catalog.papers %}
{% for paper in papers %}* [{{ paper.title }}](https://github.com/FTSRG/{{paper.repository}})
{% endfor %}

## Templates

{% assign templates = site.data.catalog.templates %}
{% for template in templates %}* [{{ template.content }}](https://github.com/FTSRG/{{template.repository}})
{% endfor %}
