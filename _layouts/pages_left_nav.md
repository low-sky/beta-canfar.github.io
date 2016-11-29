---
layout: default
---

{% include _page_header.html %}

<div class="container-fluid">
  <div class="row">
    <div id="sidebar_nav" role="navigation" class="col-sm-3 col-md-2 sidebar">
      <h3>{{ tmenu[page.namespace].name }}</h3>
      <ul class="nav nav-sidebar">
        {% for sidenav_menu in site.data.menudata[page.namespace] %}
        {% assign sidenav_mm = sidenav_menu[0] %}
        {% assign sidenav_tm = tmenu[page.namespace][sidenav_mm] %}
        {% capture sidenav_tm_uri %}{% if sidenav_tm.uri contains 'http' %}{{ sidenav_tm.uri }}{% else %}{{ page_lang_link }}{{ tmenu[page.namespace].uri }}{{ sidenav_tm.uri }}{% endif %}{% endcapture %}
        <li><a href="{{ sidenav_tm_uri }}">{{ sidenav_tm.name }}</a></li>
        {% if site.data.menudata[page.namespace][sidenav_mm].size > 0 %}
            {% for sidenav_submenu in site.data.menudata[page.namespace][sidenav_mm] %}
              {% assign sidenav_smm = sidenav_submenu[0] %}
              {% assign sidenav_stm = sidenav_tm[sidenav_smm] %}
              {% capture sidenav_stm_uri %}{% if sidenav_stm.uri contains 'http' %}{{ sidenav_stm.uri }}{% else %}{{ page_lang_link }}{{ tmenu[page.namespace].uri }}{{ sidenav_tm.uri }}{{ sidenav_stm.uri }}{% endif %}{% endcapture %}
              <li><a href="{{ sidenav_stm_uri }}" class="menu-item-indent-2">{{ sidenav_stm.name }}</a></li>
            {% endfor %}
        {% endif %}
        {% endfor %}
        <li role="separator" class="divider"></li>
        <li><a href="{{ page_lang_link }}{{ tmenu[page.namespace].uri }}">{{ tmenu[page.namespace].name }}</a></li>
      </ul>
    </div>
    <div role="main" class="col-sm-9 col-sm-offset-3 col-md-10 col-md-offset-2 main">
      <div class="inner">
        <section id="main_content">
          <h2><a id="canfar-beta" class="anchor" href="#canfar-beta" aria-hidden="true">
            {% if page.id %}
                <span aria-hidden="true" class="octicon octicon-link"></span></a>{{ tmenu[page.namespace][page.id].name }} <a class="btn btn-sm btn-warning" href="{{site.github.repository_url}}/blob/gh-pages/{{page.path}}"><span class="glyphicon glyphicon-pencil"></span> Improve this page</a></h2>
            {% else %}
                <span aria-hidden="true" class="octicon octicon-link"></span></a>{{ tmenu[page.namespace].name }} <a class="btn btn-sm btn-warning" href="{{site.github.repository_url}}/blob/gh-pages/{{page.path}}"><span class="glyphicon glyphicon-pencil"></span> Improve this page</a></h2>
            {% endif %}
          {{ content }}
        </section>
      </div>
    </div>
  </div>
</div>
{% include _page_footer.html %}
