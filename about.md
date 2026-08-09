---
layout: page
title: about
permalink: /about/
order: 1
---

<!-- TODO: replace with your real bio -->

Placeholder bio — a couple of paragraphs about your background, what you work on, and what you care about.

## Awards & Honors

<!-- Add/remove entries by adding a file to _awards/ — see existing ones for
     the front matter fields. Category order and per-category award order
     are set in _data/awards_order.yml. Star + highlight an entry by adding
     its filename to _data/starred_awards.yml. -->

{% for category_entry in site.data.awards_order %}
  {% assign category = category_entry[0] %}
  {% assign slugs = category_entry[1] %}
  <div class="award-group">
    <h3 class="mb-1">{{ category }}</h3>
    {% for slug in slugs %}
      {% assign matches = site.awards | where_exp: "item", "item.path contains slug" %}
      {% assign award = matches | first %}
      {% if award %}
        {% assign is_starred = false %}
        {% if site.data.starred_awards contains slug %}
          {% assign is_starred = true %}
        {% endif %}
        {% if award.link %}
        <a class="award-item no-underline{% if is_starred %} award-item-starred{% endif %}" href="{{ award.link }}" target="_blank" rel="noopener noreferrer">
        {% else %}
        <div class="award-item{% if is_starred %} award-item-starred{% endif %}">
        {% endif %}
          <div class="award-header">
            <h4 class="award-title mb-0">{% if is_starred %}<span class="award-star">★</span> {% endif %}{{ award.title }}{% if award.link %} <span class="award-link-icon">↗</span>{% endif %}</h4>
            <span class="award-date">{{ award.year }}</span>
          </div>
          <div class="award-org">{{ award.organization }}</div>
          {% if award.description %}
          <p class="award-description mb-0">{{ award.description }}</p>
          {% endif %}
        {% if award.link %}
        </a>
        {% else %}
        </div>
        {% endif %}
      {% endif %}
    {% endfor %}
  </div>
{% endfor %}
