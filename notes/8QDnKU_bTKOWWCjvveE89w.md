---
title: The Path Forward for Vaxx.tw 1.0
tags: vaccine,COVID-19,
---
# The Path Forward for Vaxx.tw 1.0

## Mission
To help everyone in Taiwan get vaccinated against COVID-19. 

## The Story So Far

Vaxx.tw was a project that was hacked together primarily to support the self-paid vaccination program that the Taiwanese government was running at the time. There were only 31 hospitals, and in the weeks that the program ran, we eventually grew to cover the majority (16/31) of the hospitals in Taiwan offering self-paid vaccinations with real-time, by-the-minute data. 

### How Vaxx.tw works
*People who understand crawling should feel free to skip this section*
* When you visit a website, the server sends your browser text and your browser interprets it in a certain way. 
* For example, if the browser sends down `<p>Hello</p>`, your browser knows to display a 'paragraph' (denoted by `<p>`) containing the word 'Hello'.
* If we machine-read what these servers that hospital appointment websites send down, we can pull apart the text to look for whether a hospital has appointments. This technique of machine-reading websites looking for data is called scraping. 
* 

## Challenges
* While only 31 hospitals in Taiwan offered self-paid vaccinations, a whopping 395 hospitals offer government-paid vaccinations. Not all of these hospitals have online appointment systems. 

## Stage 1: Clean Data
* For the over 395 hospitals offering government-paid vaccinations, we need to know if they have online booking. 

Release: Easily searchable list of hospitals and clear steps to book appointments. Live appointment data for hospitals we already have crawlers for (16). 

## Stage 2: API 
* Currently, we rely on scrapers written in Python to let us know if appointments are available. 

Release: