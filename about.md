---
layout: page
title: about
permalink: /about/
order: 1
---

## Bio
{: .awards-heading}

I'm an incoming sophomore at MIT majoring in Course 6-4 (AI & Decision Making) with a minor in Course 18 (Mathematics). My technical research interests mainly span AI security and related topics such as monitoring, controllability, and safety. Some of my specific research interests are detailed [here](/thoughts/#my-research-interests), though I am very open to exploring other directions as well. I'm also quite interested in how (technical) AI governance affects the large-scale adoption of such practices in the real world and in critical contexts.

Now seems like a pretty important point in time where AI development could fork into several paths, and I want to do everything in my power to steer us towards the path where AI causes the least amount of net damage. I come from a cybersecurity-heavy background, so I tend to approach these problems from the perspective of ensuring AI is used by humans with good intentions to perform good actions. I believe this will always be a top priority regardless of what crazy changes happen in capabilities and AGI/ASI timelines: unless we go extinct, malicious human actors will always pose a threat, and weaponzied human determination and creativity can go a long way in causing harm even when AI becomes more capable than us. However, I've also realized that AI models themselves are becoming a critical threat actor, and this risk has materialized much faster than I expected. As a result, I've started looking into oversight and control-related topics as well because I think it's important that we won't be completely helpless if we reach a point that calls for urgent restrictions or shutdown.


## Awards & Recognitions
{: .awards-heading}

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
