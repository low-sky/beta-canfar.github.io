---
layout: pages_left_nav

namespace: resources
id: services
lang: en
permalink: /en/resources/services/
---

<!-- Content starts -->

{% assign all_services = site.data.menudata[page.namespace][page.id] %}
{% assign t_serv_menu = site.data.translations[page.lang]['menu'][page.namespace][page.id] %}

<div class="row">
  <div class="col-sm-6">
    <div class="list-group list-group-services">
      {% for s in all_services %}
        {% assign mod = forloop.index | modulo: 2 %}
        {% if mod == 0 %}
          {% assign service_key = s[0] %}
          {% capture t_serv_uri %}{% if t_serv_menu[service_key].uri contains 'http' %}{{ t_serv_menu[service_key].uri }}{% else %}{{ page_lang_link }}{{ site.data.translations[page.lang]['menu'][page.namespace].uri }}{{ t_serv_menu[service_key].uri }}{% endif %}{% endcapture %}
          <div class="list-group-item">
            <h3 class="list-group-item-heading"><a href="{{ t_serv_uri }}">{{ t_serv_menu[service_key].name }}</a> <a class="btn btn-lg" href="{{ t_serv_menu[service_key].doclink }}"> <span class="glyphicon glyphicon-info-sign" aria-hidden="true"></span></a></h3>
            <p class="list-group-item-text">Lorem ipsum</p>
          </div>
        {% endif %}
      {% endfor %}
    </div>
  </div>
  <div class="col-sm-6">
    <div class="list-group list-group-services">
      {% for s2 in all_services %}
        {% assign mod = forloop.index | modulo: 2 %}
        {% if mod == 1 %}
          {% assign service_key = s2[0] %}
          {% capture t_serv_uri %}{% if t_serv_menu[service_key].uri contains 'http' %}{{ t_serv_menu[service_key].uri }}{% else %}{{ page_lang_link }}{{ site.data.translations[page.lang]['menu'][page.namespace].uri }}{{ t_serv_menu[service_key].uri }}{% endif %}{% endcapture %}
          <div class="list-group-item">
            <h3 class="list-group-item-heading"><a href="{{ t_serv_uri }}">{{ t_serv_menu[service_key].name }}</a> <a class="btn btn-lg" href="{{ t_serv_menu[service_key].doclink }}"> <span class="glyphicon glyphicon-info-sign" aria-hidden="true"></span></a></h3>
            <p class="list-group-item-text">Lorem ipsum</p>
          </div>
        {% endif %}
      {% endfor %}
    </div>
  </div>
</div>

<!-- Content ends -->
