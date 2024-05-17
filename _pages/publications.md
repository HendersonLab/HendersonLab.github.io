---
layout: page
permalink: /publications/
title: Publications
description:
years: [2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015, 2013, 2012, 2011, 2010, 2009, 2008, 2007, 2006, 2005, 2004, 2003]
nav: true
importance: 3
---
<!-- _pages/publications.md -->

<div class="publications">

{% assign months = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec" | split: "," %}
{% assign month_numbers = "01,02,03,04,05,06,07,08,09,10,11,12" | split: "," %}

{%- for y in page.years %}
  <h2 class="year">{{ y }}</h2>
  
  {% assign year_entries = site.papers | where: "year", y %}
  {% assign sorted_entries = "" %}

  {%- for month_number in month_numbers %}
    {% assign monthly_entries = year_entries | where: "month", month_number %}
    {% for entry in monthly_entries %}
      {% assign sorted_entries = sorted_entries | append: entry | append: "," %}
    {% endfor %}
  {%- endfor %}

  {% assign sorted_entries = sorted_entries | split: "," | where: "size", ">", 0 %}
  {% for entry in sorted_entries %}
    {% bibliography -f papers -q @{{ entry }} %}
  {% endfor %}
  
{%- endfor %}

</div>
