---
layout: page
title: Reading Log
permalink: /book-log/
---
<div>
    {% for item in site.data.reading_log %}
    <div>
        ## Currently Reading
        {% if item.status == "reading" %}
        <figure>
            <imag alt="book cover" src="{{item.cover_url}}">
            <figcaption>{{item.title}}</figcaption>
        </figure>
        {% endif %}
    </div>
    <div>
        ## {{item.year}}
            {{ entry.books | size }} books
        <ul>
             {% for book in entry.books %}
             <li>{{book.title}} by {{book.author}}</li>
             {% endfor %}
        </ul>    
    </div>
    {% endfor %}
</div>