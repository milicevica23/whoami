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
An educational repository to learn about memory usage in data libraries using the memray profiler. It includes examples of loading and processing data with libraries like DuckDB, Apache Arrow, and Delta Lake, as well as the data interchange between them.

This project started as an attempt to improve dbt-duckdb integration with Delta tables by understanding memory consumption while interchanging data between DuckDB and the Delta writer via Arrow format.
A nice visualization of memory allocation while transferring data between DuckDB and Delta Lake via Arrow format can be found [here](https://github.com/duckdb/dbt-duckdb/pull/332#discussion_r1511158975).

## Learnings
- dbt just sends SQL commands to the database, and the queries are not always optimized for memory efficiency
- Arrow is very useful, and DuckDB has to provide it as an iterator to the caller because the buffer manager can exchange memory blocks and this is why fixed pointers don't work
- Changes to an open source project have to be small and incremental to be accepted. I invested a lot of time but was unable to ensure backward compatibility and therefore my PR was not accepted
- Memray is excellent, and its graph representation helps visualize memory usage and understand what you're doing wrong in your program
- Understanding ram memory usage is important for performance of a data application

## Related tweets
{{< x user="milicevica23" id="1764628415800332500" >}}
{{< x user="milicevica23" id="1761876903172923560" >}}


 


