---
title: Praćenje hrane i analiza uticaja na zdravlje
summary: Lični sistem analitike zdravlja koji prati unos hrane i povezuje sastojke/alergene sa zdravstvenim ishodima.
date: 2025-12-24
authors:
  - aleks
tags:
  - Projekat
  - Data Engineering
  - Dagster
  - dbt
  - DuckDB
  - Analitika Zdravlja
links:
  - icon: brands/github
    name: repozitorijum
    url: "https://github.com/milicevica23/food-tracking"
  - name: unos-podataka
    url: "https://docs.google.com/forms/d/e/1FAIpQLSc0_qS9dJ4lBwpG3ThMBWqbUr8Fe__Wrn2b6xy4aDTdctWlBA/viewform"
  - name: vizualizacija-podataka
    url: "https://milicevica23.github.io/food-tracking-serving/"

---
## Pregled
Pre nekoliko godina, shvatio sam da se nakon jela određene hrane ponekad osećam loše, imam glavobolje ili postajem veoma pospan. Nakon razgovora sa kolegom, savetovao me je da počnem da pratim unos hrane i kako se osećam. Prvih nekoliko nedelja sam to radio u Excel-u, a onda odlučio da iskoristim svoje znanje i napravim nešto zabavno. Ovaj projekat služi da bolje razumem uticaj hrane na moje zdravlje, a takođe i kao igralište za nove tehnologije, procese i arhitekture (npr. prvi put sam probao da kodiram uz pomoć AI-a - Claude Code).

Nadam se da ovaj projekat može pomoći vama kao što je pomogao meni. Radostan sam da primim povratne informacije i ideje.

**Možete isprobati ako želite, ali budite svesni da su podaci javno dostupni i nisu pravilno obezbeđeni niti bekapovani.**

## Arhitektura
Ideja je veoma jednostavna: prikupite podatke putem korisničkog interfejsa, sačuvajte podatke u bazu podataka, obogatite podatke, vizualizujte i izvucite uvide.

(Dobrodošli u data inženjering :)

## Komponente
### [Anketa za prikupljanje hrane](https://docs.google.com/forms/d/e/1FAIpQLSc0_qS9dJ4lBwpG3ThMBWqbUr8Fe__Wrn2b6xy4aDTdctWlBA/viewform)
Možete uneti onoliko unosa koliko imate obroka dnevno. Jedina lična informacija koja je potrebna je email, koji možete lažirati ako želite da ostanete anonimni.
Obično šaljem novi unos samo sa imenom hrane i slikom, zatim nakon 1-2 sata dodajem samoprocenu uticaja na zdravlje. Dobićete email potvrdu nakon prvog slanja i možete ga kasnije urediti.

#### Pravila koja pratim
- Zabeležite svu hranu konzumiranu u jednom obroku u jednom redu
- Dodajte samoprocenu 1-2 sata nakon obroka
- Izbegavajte jedenje druge hrane najmanje 3-4 sata nakon obroka

### [Vizualizaciona kontrolna tabla](https://milicevica23.github.io/food-tracking-serving/)
Vaš email je heširan i možete pronaći svoj heš sa sledećom naredbom
```
SELECT sha256('123@gmail.com') as user_hash_id;
```
Zatim možete pretražiti svog korisnika i kliknuti u tabeli da dođete do svoje lične kontrolne table.

Kontrolna tabla treba malo više pažnje i uskoro će je dobiti.

## Status
Ovde ću s vremena na vreme ažurirati status i pravac projekta.

### 2025-12-24 - Init
#### Generalno
Opšta ideja je bila da se postavi početni UI za prikupljanje podataka, osnovna Dagster, dbt i MotherDuck integracija (poznajem Dagster i dbt sa posla), i da imam osnovnu kontrolnu tablu sa nekoliko metrika i vizualizacija.
Imao sam nekoliko stvari na umu koje sam hteo da naučim sa prvom iteracijom:
- Kako koristiti Google Forms kao UI za prikupljanje podataka (bio sam iznenađen out-of-the-box funkcionalnostima poput čuvanja i uređivanja unosa u Google Sheets-u i slanja email potvrda)
- Probati kodiranje uz pomoć AI-a - Claude Code me je nekoliko puta oduševio
- Deployovati Dagster na self-hosted Kubernetes klaster sa self-hosted runner-om (bilo je teže nego što sam očekivao)
- Povezati i istražiti MotherDuck jer sam hteo da se vratim DuckDB-u
- Naučiti novi alat za vizualizaciju (odlučio sam se za Evidence jer je već imao Dagster integraciju, iako sada mislim da nije dovoljno zreo i treba mu poboljšanje kojem ću pokušati da doprinjem)

#### Naučene lekcije
- Proces oko izgradnje Docker image-a i deployment-a sa self-hosted GitHub runner-ima na self-hosted Kubernetes klasteru zahteva mnogo znanja koje često uzimamo zdravo za gotovo kada imamo DevOps kolege
- Počinjanje jednostavno sa vidljivom poslovnom vrednošću je važnije od sofisticiranog alata. Na primer, sada koristim Google Forms za prikupljanje podataka umesto da gradim prilagođeni UI u Rust-u (počeo sam i stao najmanje 3 puta)
- Imati funkcionalno end-to-end rešenje prvi put je bilo veoma motivišuće i pomaže da ga dalje proširujem i poboljšavam
- Teško je prikupljati podatke i biti precizan. Šta tačno sadrži obrok? Kako se zaista osećate na skali od 1 do 10?

#### Sledeći koraci
- Kreirati više kontrolnih tabli i vizualizacija iz postojećih podataka
- Obogatiti prikupljene podatke AI-generisanim sastojcima iz imena hrane i slike
- Pronaći više prijatelja koji su voljni da ovo isprobaju
- Probati SOPS za tajne i FluxCD za Kubernetes deployment
- Pokušati poboljšati Dagster-Evidence komponentnu integraciju
- Napraviti da se osvežavanja automatski pokreću po rasporedu
