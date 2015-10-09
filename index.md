---
layout: minimal
---
# Table of Contents
<ul>
  <li><a href="#tools">Tools</a></li>
{% for tool in site.data.tools %}
  {% assign link = tool[1].display_name | split: ' ' | join: '-' %}
  {% if tool[1].plugins %}<li><a href="#{{link | downcase}}">{{tool[1].display_name}} Plugins</a></li>{%endif%}
{% endfor %}
</ul>

# Tools
Useful tools when writing Puppet.

<table>
  <thead>
  <tr>
    <th>Tool Link</th>
    <th>Description</th>
  </tr>
  </thead>
  <tbody>
  {% for tool in site.data.tools %}
  {% if tool[1].url %}
  <tr>
    {% if tool[1].display_name %}
    {% assign display_name = tool[1].display_name %}
    {% else %}
    {% assign display_name = tool[1].name %}
    {% endif %}
    <td><a href="{{tool[1].url}}">{{ display_name }}</a></td>
    <td>{{tool[1].description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
  </tbody>
</table>

{% for tool in site.data.tools %}
{% if tool[1].plugins %}
# {{ tool[1].display_name }}
{% if tool[1].description %}{{tool[1].description}}{%endif%}
<table>
  <thead>
  <tr>
    <th>Plugin Link</th>
    <th>Description</th>
  </tr>
  </thead>
  <tbody>
  {% assign sorted_plugins = tool[1].plugins | sort: 'name' %}
  {% for plugin in sorted_plugins %}
  <tr>
    <td><a href="{{plugin.url}}">{{plugin.name}}</a></td>
    <td>{{plugin.description}}</td>
  </tr>
  {% endfor %}
  </tbody>
</table>
{% endif %}
{% endfor %}
