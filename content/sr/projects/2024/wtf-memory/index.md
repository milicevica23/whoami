---
title: WTF Memory - Istraživanje korišćenja memorije
summary: Edukativni repozitorijum za učenje o obrascima korišćenja memorije u data aplikacijama koristeći memray profiler.
date: 2024-06-01
authors:
  - aleks
tags:
  - Istraživački Projekat
  - Python
  - Profilisanje Memorije
  - DuckDB
  - Apache Arrow
  - Delta Lake
  - Edukacija
links:
  - icon: brands/github
    name: repozitorijum
    url: "https://github.com/milicevica23/wtf-memory"
---
## Pregled
Edukativni repozitorijum za učenje o korišćenju memorije u data bibliotekama koristeći memray profiler. Uključuje primere učitavanja i obrade podataka sa bibliotekama kao što su DuckDB, Apache Arrow i Delta Lake, kao i razmenu podataka između njih.

Ovaj projekat je počeo kao pokušaj da se poboljša dbt-duckdb integracija sa Delta tabelama razumevanjem potrošnje memorije tokom razmene podataka između DuckDB-a i Delta writer-a putem Arrow formata.
Lepa vizualizacija alokacije memorije tokom prenosa podataka između DuckDB-a i Delta Lake-a putem Arrow formata može se pronaći [ovde](https://github.com/duckdb/dbt-duckdb/pull/332#discussion_r1511158975).

## Naučene lekcije
- dbt samo šalje SQL komande bazi podataka, a upiti nisu uvek optimizovani za efikasnost memorije
- Arrow je veoma koristan, a DuckDB mora da ga obezbedi kao iterator pozivaocu jer buffer manager može da razmenjuje blokove memorije i zato fiksni pokazivači ne rade
- Promene u open source projektu moraju biti male i inkrementalne da bi bile prihvaćene. Uložio sam mnogo vremena ali nisam mogao da osiguram kompatibilnost unazad i zato moj PR nije prihvaćen
- Memray je odličan i njegova grafička reprezentacija pomaže da se vizualizuje korišćenje memorije i razume šta radite pogrešno u programu
- Razumevanje korišćenja RAM memorije je važno za performanse data aplikacije

## Povezani tvitovi
{{< x user="milicevica23" id="1764628415800332500" >}}
{{< x user="milicevica23" id="1761876903172923560" >}}
