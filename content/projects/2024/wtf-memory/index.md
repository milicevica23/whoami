---
title: WTF Memory - Exploring Memory Usage
summary: An educational repository to learn about memory usage patterns in data applications using memray profiler.
date: 2024-06-01
authors:
  - aleks
tags:
  - Exploration Project
  - Python
  - Memory Profiling
  - DuckDB
  - Apache Arrow
  - Delta Lake
  - Education
links:
  - icon: brands/github
    name: repository
    url: "https://github.com/milicevica23/wtf-memory"
---
## Overview
An educational repository to learn about memory usage in data libraries using the memray profiler. It includes examples of loading and processing data with libraries like DuckDB, Apache Arrow, and Delta Lake and the interchanges between them.

This project started as a try to improve dbt-duckdb integration with delta tables by understanding memory consumption while interchange data between duckdb and delta writer via arrow format.
A nice visualisation of memory allocation while transfering data between duckdb and delta lake via arrow format [here](https://github.com/duckdb/dbt-duckdb/pull/332#discussion_r1511158975)


## Learnings
- dbt is just sending SQL commands towards database and the queries are not always optimized for memory efficiency
- arrow is a very nice thing and that duckdb has to give it as iterator to the caller because buffer manager can excahange the memory blocks and this is why fixed pointers doesnt work
- change on a open source project has to be small and incremental to be accepted. I invested a lot of time to not beeing able to assure backward compatibility.
-  memray is very nice and graph representation is very nice to visualize memory usage and helps to understand what you are doing wrong in your program
- ram memory usage is important

## Related tweets
{{< x user="milicevica23" id="1764628415800332500" >}} 
{{< x user="milicevica23" id="1761876903172923560" >}} 






 


