---
layout: page
title: "MAGIC Privacy Guides Fund"
---

MAGIC Grants is pleased to host the [Privacy Guides](https://privacyguides.org) project with the MAGIC Privacy Guides Fund. Privacy Guides the leading resource for independent, criteria-focused product recommendations and general knowledge in the privacy space. Please make sure to familiarize yourself with the important Fund details:

* [Privacy Guides Fund Document](/funds/privacy_guides/privacy_guides_fund)
* [MAGIC Grants Policies](/about/documentation)

## Donate

To donate to the MAGIC Privacy Guides Fund, please email us at [info@magicgrants.org](mailto:info@magicgrants.org). We accept donations with credit card, bank transfer, and cryptocurrency. A new donation platform to make donating easier will be deployed soon.

## Committee Members

The MAGIC Privacy Guides Fund is governed by a committee that is composed of the five original [Privacy Guides team members](https://www.privacyguides.org/en/about/#our-team). They are:

* Jonah Aragon
* Niek de Wilde
* Daniel Gray (dngray)
* Freddy
* Olivia

Currently, committee members are appointed and removed by the committee. There is no election process.

## MAGIC Privacy Guides Fund Vision and Goals

* To maintain the best privacy educational resources.
* To foster a privacy community.
* To remain free of advertisements and affiliate links.

## Committee Minutes

<ul class="post-list">
{% assign privacyguidesfundminutes = site.privacyguidesfundminutes | sort: 'date' | reverse %}
{% for minute in privacyguidesfundminutes limit:5 %}
  <li><article><a href="{{ site.url }}{{ minute.url }}"><div class="post-entry-title">{{ minute.title }}</div></a></article></li>
  <hr>
{% endfor %}
</ul>

[Archive of older minutes](https://github.com/MAGICGrants/MagicGrants.org/tree/master/posts/_privacyguidesfundminutes)
