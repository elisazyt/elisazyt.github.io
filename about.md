---
layout: page
title: about
permalink: /about/
order: 1
---

## Bio
{: .awards-heading}

I'm an incoming sophomore at MIT majoring in Course 6-4 (AI & Decision Making) with a minor in Course 18 (Mathematics). My technical interests mainly span AI security and related topics such as monitoring, controllability, and safety. Some of my specific research interests are outlined [here](/thoughts/#my-research-interests), though I am very open to exploring other directions as well. I'm also quite interested in how (technical) AI governance affects the large-scale adoption of such principles and practices in critical real-world contexts.

Much of my research experience centers around ML and agentic AI for software security and trustworthiness: this includes automated patch detection and generation, generating synthetic data to train malware classifiers, explainability for blackbox and glassbox models, and more. Detailed information about my previous work and publications can be found [here](/experience/).

I'd like to continue down my current path: now seems like an important point in time where AI development could fork into several paths, and I want to do research that will steer us towards the path where AI causes the minimal possible amount of damage. I have a cybersecurity-heavy background, so I tend to approach these problems from the perspective of ensuring AI is used by humans with good intentions to perform good actions. I believe this will remain a top priority regardless of what crazy changes happen in capabilities and AGI/ASI timelines: malicious human actors will always pose a threat, and weaponized human determination and creativity can go a long way in causing harm even when AI becomes more capable than us. However, I've also realized that AI models themselves are becoming a critical threat actor, and this risk has unfortunately materialized much faster than I expected. As a result, I've started looking into oversight and control. I think it's important to be as prepared as possible so that humans won't be completely helpless if we reach a point that calls for urgent restriction or shutdown.


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
            <h4 class="award-title mb-0">{% if is_starred %}<span class="award-star">★</span> {% endif %}{{ award.title }}{% if award.link %} <span class="award-link-icon">↗&#xFE0E;</span>{% endif %}</h4>
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
