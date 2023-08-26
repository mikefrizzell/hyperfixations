---
layout: page
title: Reading Log
permalink: /book-log/
---

<div>
  <h3>Currently Reading</h3>
  <div>
    <ul class="book-grid">
      {% for book in site.data.reading_log.books %}
        {% if book.status == "reading" %}
          <li class="book-grid-item">
            <img class="book-cover" src="{{ book.cover_url }}" alt="{{ book.title }} by {{ book.author }}">
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
  
  <h3>Books Read</h3>
  <div>
    {% assign books_by_year = site.data.reading_log.books | group_by: "year" %}
    {% for entry in books_by_year %}
      <h4>{{ entry.name }}</h4>
      <ul>
        {% for book in entry.items %}
          {% if book.status == "finished" %}
          <li><cite>{{ book.title }}</cite> by {{ book.author }}</li>
          {% endif %}
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
</div>
