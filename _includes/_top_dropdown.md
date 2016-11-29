<a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">{{ include.name }} <span class="caret"></span></a>
<ul class="dropdown-menu list-unstyled">
  {% for item in include.nav %}
  {% if item.uri == 'fixme' %}
  <li class="active">
  {% else %}
  <li>
  {% endif %}
    <a href="{{ item.uri }}" class="menu-item-indent-{{ include.indent }}">
      {{ item.name }}
    </a>
  </li>
  {% if include.t[item].items %}
  {% assign indent = indent | plus: 1 %}
  {% include _top_dropdown.md nav=item.items name=item indent=indent %}
  {% endif %}
  {% endfor %}
</ul>