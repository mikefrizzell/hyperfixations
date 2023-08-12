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
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
  
  <h2>Books Read</h2>
  <div>
    {% for entry in site.data.reading_log.books %}
      <h4>{{ entry.year }}</h4>
      <p>{{ entry.books | size }} books</p>
      <ul>
        {% for book in entry.books %}
          <li>{{ book.title }} by {{ book.author }}</li>
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
</div>
