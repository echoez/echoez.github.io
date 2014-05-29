---
layout: post
title: "My first DB Query in Oracle"
date: 2014-05-28 01:36:29 -0400
comments: true
categories: [SQL, Oracle, Database]
---


Today i've accomplished something so small yet so significant in my industry. I created my first query.
Though i dabbled in MySQL when installing CMS for clients in the past, I never really been hands on with anything DB related.

This query ive made in oracle pulls a set amount of shipments from three joined tables and displays them in a neat concatenated statement.

In absence of INNER JOIN, i used aliases as attributes to columns to join them.


{% codeblock Oracle SQL lang:sql %}

SELECT 'Did you know Shipment (#'|| es.shipment_id||') is a '|| ewt.work_type|| ' work type which printed in Export Batch (#'|| es.exporting_batch_id ||'). This was exported on '||es.date_exported
FROM exporting_shipments es, exporting_flags ef, exporting_work_type ewt
WHERE  es.shipment_id = ef.shipment_id AND ef.work_type_id = ewt.id
and es.shipment_id < 04339740 AND es.shipment_id > 04339700
{% endcodeblock %}