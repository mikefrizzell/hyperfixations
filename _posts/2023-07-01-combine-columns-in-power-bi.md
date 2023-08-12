---
title: How to combine columns in Power BI
category: ["how to", "data analysis", "Power BI"]
layout: post
author: Michael Frizzell
---
I finally solved a problem I've had with Power BI over the past few months, so I thought I would put it in writing just in case anyone else is having the same issue. One of the my jobs is to monitor user productivity in my department, and I do that by using Microsoft Forms, Excel, and Power BI. Forms, for the users to input their numbers.[^1] Excel, to store the data. And Power BI to report out to my bosses.

For one of the reports, we have two categories, A and B, and under each of those are multiple subcategories (1,2,3, etc). A user selects which category and subcategory they are entering data in for. The end result is a spreadsheet that has a column for A, a column for a values inputted for A, a column for B, and a column for all values inputted for B. This all works out just fine most of the time, but occasionally I would like for all subcategories under A and B to be in one column and their values next to it. 

Basically, I want the data to be stored in both ways, so I can visualize it in multiple ways. I understand this is a problem of my own making and that I'm trying to have my cake and eat it too, but that's just life.

Anyway, my solution to this self-inflicted wound is to create a new combined table (Modeling > New table) and use the following DAX code:

```DAX

Combined Table = 
UNION(
   SELECTCOLUMNS(Table1, "Type", [category_a], "Number", [number_done_a]),
   SELECTCOLUMNS(Table1, "Type", [category_b], "Number", [number_done_b])
)

```

This allows me to create a table visualization that shows a list of all subcategories in A and B and their corresponding numbers.

[^1]: We have automated reporting, but it doesn't give us enough specificity, so we have to manually track some things. It's not perfect, but unless our software vendor implements our very specific requirements, we're stuck with it.
