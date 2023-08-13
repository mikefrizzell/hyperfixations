---
layout: page
title: Reading Log
permalink: /book-log/
---

<div>
  <h2>Currently Reading</h2>
  <div>
    <ul class="book-grid">
      {% for book in site.data.reading_log.books %}
        {% if book.status == "reading" %}
          <li class="book-grid-item">
            <img class="book-cover" src="{{ book.cover_url }}" alt="{{ book.title }} by {{ book.author }}">
            <p>{{ book.title }} by {{ book.author }}</p>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
  
  <h2>Books Read</h2>
  <div>
    {% assign books_by_year = site.data.reading_log.books | group_by: "year" %}
    {% for entry in books_by_year %}
      <h4>{{ entry.name }}</h4>
      <ul>
        {% for book in entry.items %}
          <li>{{ book.title }} by {{ book.author }}</li>
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
</div>
