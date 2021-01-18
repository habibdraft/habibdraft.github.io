---
layout: post
title: What data engineers actually do, part 2
---

#OLTP (Online transaction processing)

It's useful to think of a transaction as a specific event happening in the world at a specific time. For our purposes, assume a transaction has a timestamp and a location stamp (latitude-longitude coordinates) along with anything else relevant about the event that we chose to record.

Why are we recording this event? What relevant information are we preserving? 

#OLAP (Online analytical processing)

Aggregating and applying aggregate-level queries to transactions 

This is the insight-generation part of the pipeline. 
