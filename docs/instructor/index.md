---
layout: slideshow
reveal-theme: /css/theme/sky.css
style: /css/slideshow.css
---

<section markdown="1">

# {{ site.title }}
{:style="text-transform: none;"}

Lesson {{ site.lesson }} with *{{ site.instructor }}*

</section>

{% for sorted in site.slide_sorter %}
{% capture id %}/slides/{{ sorted }}{% endcapture %}
{% assign hslide = site.slides | where: "id", id | first %}
<section>
{% assign vslides = hslide.content | split: "<p>===</p>" %}
{% for vslide in vslides %}
<section{% if hslide.background %} data-background="{{ site.baseurl }}{{ hslide.background }}"{% endif %}{% if hslide.class %} class="{{ hslide.class }}"{% endif %}>
{{ vslide }}
</section>
{% endfor %}
</section>
{% endfor %}
