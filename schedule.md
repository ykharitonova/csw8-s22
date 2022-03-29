---
layout: page
title: Schedule
nav_order: 4
description: The weekly schedule.
---

# Weekly Schedule

See the [Schedule and Roadmap]({{site.url}}/{{site.baseurl}}/success/#time-management-and-scheduling) suggestions for organizing your time. 

Use the same Zoom link for lab and office hours as you use for lecture.

You can also [schedule a meeting with Prof. K using this link](https://calendar.google.com/calendar/u/0/selfsched?sstoken=UUFjZExlYWxLMkdRfGRlZmF1bHR8NTZmMGZmY2IyYjFmZTVmMmNmNWQ0YmUxZjQ2MWUwOGY).

{% for schedule in site.schedules %}
{{ schedule }}
{% endfor %}
