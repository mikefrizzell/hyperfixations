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
       {% assign finished_books = site.data.reading_log.books | where: "status", "finished" | sort: "year" | reverse %}
    {% assign previous_year = "" %}
    {% for book in finished_books %}
      {% if book.year != previous_year %}
        <h3>{{ book.year }}</h3>
        {% assign previous_year = book.year %}
      {% endif %}
      <ul>
        <li>{{ book.title }} by {{ book.author }}</li>
      </ul>
    {% endfor %}
  </div>
</div>
