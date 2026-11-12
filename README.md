# Aufmerksamkeitsstrukturen im Gaza-Diskurs - Eine soziale Netzwerkanalyse deutscher Leitmedien-Journalist:innen auf X/Twitter seit dem 7. Oktober 2023

Analysecode zur Masterarbeit im Masterstudiengang Journalismus an der Universität Leipzig.

- **Autor:in:** Julia Mayer
- **Betreuung:** Dr. Uwe Krüger, Jun.-Prof. Dr. Vera Katzenberger
- **Abgabe:** 12. November 2026

## Zusammenfassung

Die deutsche Berichterstattung zum Gaza-Krieg steht seit dessen Beginn in der Kritik: Debattiert wird insbesondere, welche Perspektiven und Akteur:innen journalistisch Gehör finden. Diese Arbeit untersucht daran anschließend, auf welche Accounts deutsche Leitmedien-Journalist:innen auf X ihre Aufmerksamkeit richten. Auf Grundlage der Indexing-Hypothese wird analysiert, wie ihr Interaktionsnetzwerk strukturiert ist, welche Akteur:innen und Akteur:innengruppen besonders viel Aufmerksamkeit erhalten und wie sich die Aufmerksamkeitsstrukturen zwischen ausgewählten Aktivitätsphasen unterscheiden. Mittels sozialer Netzwerkanalyse werden die thematisch relevanten Bezugnahmen von 139 Journalist:innen aus acht deutschen Leitmedien zwischen dem 7. Oktober 2023 und dem 24. April 2026 untersucht. Das Analysenetzwerk umfasst 18.744 Retweets, @Mentions, Quote-Tweets und Replies. Die Aufmerksamkeit ist dabei stark ungleich verteilt. Wenige Journalist:innen erzeugen einen großen Teil der Bezugnahmen, zugleich überschneiden sich ihre Adressat:innenkreise nur geringfügig. Unter den zentralen adressierten Accounts dominieren Medien und Journalist:innen. Institutionelle Eliten werden von vielen Journalist:innen, meist aber nur vereinzelt, adressiert. Im explorativen Vergleich verschiedener Aktivitätsphasen zeigen sich zudem Unterschiede darin, welche institutionellen Akteur:innen im Zentrum der Aufmerksamkeit stehen. Insgesamt sprechen die Befunde nicht für eine durchgehend gemeinsame Orientierung an einem festen Kreis institutioneller Eliten. Indexing auf X könnte sich vielmehr darin zeigen, dass je nach Ereignislage unterschiedliche institutionelle Akteur:innen Aufmerksamkeit erhalten.

**Schlüsselwörter:** Indexing-Hypothese · journalistische Aufmerksamkeit · soziale Netzwerkanalyse · X (Twitter) · Gaza-Krieg · politische Kommunikation

## Abstract

Since the beginning of the war in Gaza, German media coverage has faced criticism over which perspectives and actors are given a voice. Against this backdrop, this study examines which accounts journalists at leading German news outlets direct their attention to on X. Drawing on the indexing hypothesis, it analyzes their interaction network, which actors and groups receive the most attention, and how attention structures differ across selected periods of heightened activity. Social network analysis examines Gaza-related interactions by 139 journalists from eight leading German news outlets between October 7, 2023, and April 24, 2026. The network comprises 18,744 retweets, @mentions, quote tweets, and replies. Attention is highly unevenly distributed. A small number of journalists account for a large share of interactions, while the accounts they address overlap little. Media outlets and journalists dominate among the most addressed accounts. Institutional elites receive attention from many journalists, but mostly sporadically. An exploratory comparison of activity periods also reveals differences in which institutional actors are at the center of attention. The findings do not indicate a sustained, shared orientation toward a fixed set of institutional elites. Instead, indexing on X may involve shifts in attention toward different institutional actors as events unfold.

**Keywords:** Indexing hypothesis · journalistic attention · social network analysis · X (Twitter) · Gaza war · political communication

## Forschungsfragen

- FF1: Welche Aufmerksamkeitsstrukturen zeigen sich im Interaktionsnetzwerk deutscher Leitmedien-Journalist:innen auf X im Gaza-Diskurs seit dem Angriff der Hamas am 7. Oktober 2023?
- FF1.1: Welche strukturellen Eigenschaften weist das Netzwerk auf?
- FF1.2: Welche Akteur:innen und Akteursgruppen erhalten besonders viel Aufmerksamkeit?
- FF1.3: Wie verändern sich die Aufmerksamkeitsstrukturen zwischen Phasen erhöhter Kommunikationsaktivität?

## Design

| Aspekt | Umsetzung |
|---|---|
| Design | quantitativ-explorativ, Kombination aus egozentrierter und Gesamtnetzwerk-Perspektive |
| Stichprobe | 139 Journalist:innen (Egos) aus 8 Medien: Bild, FAZ, Focus, SZ, Der Spiegel, taz, Die Zeit, Welt |
| Zeitraum | 7. Oktober 2023 bis 24. April 2026 |
| Datenerhebung | Zeeschuimer und 4CAT |
| Interaktionstypen | Mention, Retweet, Quote, Reply |
| Themenfilter | zweistufig (siehe Methodenkapitel 3.3) |
| Phasenbestimmung | Burst Detection nach Kleinberg (2003), `bursts::kleinberg()` |
| Akteurskategorisierung | 11 funktionale Kategorien (K01 bis K11) für die 152 meistadressierten Accounts |

Da nur die Egos Kanten senden können, ist das Netzwerk nahezu bipartit. Standardmaße wie Dichte oder Louvain auf dem Gesamtnetz sind deshalb nicht sinnvoll interpretierbar. Der Code verwendet stattdessen designangepasste Alternativen (designkorrigierte Ausschöpfungsquote, Ego-Ego-Projektion über gemeinsam adressierte Alteri, Analyse des Netzwerks innerhalb der Stichprobe).

**Begriffe:** Im Code heißen die 139 untersuchten Journalist:innen *Egos* und die von ihnen adressierten Accounts *Alteri*. Das sind die üblichen Bezeichnungen der Netzwerkanalyse. Die Arbeit selbst spricht von den Journalist:innen der Stichprobe und von adressierten Accounts.

## Struktur des Repositorys

```
.
├── R/                  # Analyseskripte in Ausführungsreihenfolge
├── data/               # Rohdaten und erzeugte Daten (nicht im Repository)
├── output/             # Abbildung und Gephi-Dateien
├── [NAME].Rproj        # RStudio-Projektdatei, legt den Projektordner fest
├── LICENSE
└── README.md
```

## Skripte

| Skript | Inhalt | Kapitel |
|---|---|---|
| `R/01_datenbereinigung.Rmd` | Import der Rohdaten, Auswahl netzwerkrelevanter X-Beiträge, zweistufiger Themenfilter | 3.3 |
| `R/02_netzwerk_listen.Rmd` | Kanten je Interaktionstyp, Bereinigung von Artefakten durch geänderte Handles, Kanten- und Knotenlisten, Liste der Redaktionsaccounts | 3.4 |
| `R/03_burst_detection.Rmd` | Burst Detection nach Kleinberg, Bildung der Phasen, Sensitivitätsanalyse, Kanten je Vergleichsphase | 3.5 |
| `R/04_gesamtnetzwerkanalyse.Rmd` | Analysenetzwerk, Verteilung der Aufmerksamkeit, Akteurskategorien, Phasenvergleich, Binnennetzwerk, Community Detection | 3.6, 4.1 bis 4.4 |

Jedes Skript nennt im Kopf seine Eingabe- und Ausgabedateien sowie die erwarteten Fallzahlen.

## Daten

Die Daten sind aus datenschutzrechtlichen Gründen und wegen der Nutzungsbedingungen von X **nicht** Teil dieses Repositorys. Alle Dateien liegen lokal im Ordner `data/`.

**Eingabedateien** (von Hand erstellt oder erhoben, nicht aus dem Code erzeugbar)

| Datei | Inhalt | Zeilen | Gebraucht in |
|---|---|---|---|
| `Tweets_Rohdaten.xlsx` | Export der X-Beiträge aus 4CAT | 33.718 | 01 |
| `Kategorisierung_Akteure.xlsx` | manuelle Kategorisierung der meistadressierten Accounts | 152 | 04 |
| `Burstphasen_Nachkategorisierung_fertig.xlsx` | manuelle Kategorisierung zusätzlicher Accounts aus den Vergleichsphasen | 9 | 04 |

**Erzeugte Dateien**

| Datei | Inhalt | Zeilen | Erzeugt in |
|---|---|---|---|
| `tweets_topic_final` (rds, csv), `Tweet_Stichprobe_BEREINIGT.xlsx` | themenrelevante X-Beiträge der Stichprobe | 17.910 | 01 |
| `Kantenliste_Ereignisse` (rds, csv) | einzelne Interaktionsereignisse | 20.599 | 02 |
| `Kantenliste_gewichtet` (rds, csv) | gewichtete Kanten je Paar aus Ego und Alter | 9.538 | 02 |
| `Knotenliste` (rds, csv) | alle Knoten (Egos und Alteri) | 4.125 | 02 |
| `Egoliste` (rds, csv) | Journalist:innen der Stichprobe | 139 | 02 |
| `outlet_medium.rds` | Redaktionsaccounts der acht Medien | 29 | 02 |
| `sensitivity_phases.csv` | Phasen je Lückenwert der Sensitivitätsanalyse | 120 | 03 |
| `Kantenliste_gewichtet_Burstphasen.rds` | gewichtete Kanten in den drei Vergleichsphasen | 4.258 | 03 |
| `Top_Alteri_Kategorisierung.csv` | Vorlage für die manuelle Kategorisierung | 152 | 04 |
| `Burstphasen_Nachkategorisierung.xlsx` | Vorlage für die manuelle Nachkategorisierung | 9 | 04 |

Die Kanten- und Knotenlisten enthalten die Redaktionsaccounts noch. Das Analysenetzwerk der Arbeit entsteht in Skript 04 durch deren Ausschluss und umfasst 4.096 Knoten, 9.216 gerichtete Kanten und 18.744 Bezugnahmen.

## Reproduktion

Voraussetzung: R, RStudio und die drei Eingabedateien im Ordner `data/`.

1. Projekt über die `.Rproj`-Datei öffnen. Alle Pfade sind über `here::here()` relativ zum Projektordner gesetzt.
2. Pakete installieren:

```r
install.packages(c("tidyverse", "igraph", "bursts", "readxl", "writexl", "scales", "here"))
```

3. Die Skripte in `R/` in nummerierter Reihenfolge knitten.

**Hinweise**

- Die Rohdaten werden vollständig als Text eingelesen, damit die 19-stelligen Beitrags-IDs nicht durch Gleitkomma-Rundung verfälscht werden.
- Zwischenergebnisse werden als `.rds` zwischen den Skripten übergeben.
- Die beiden manuellen Kategorisierungen beruhen auf Vorlagen, die Skript 04 selbst erzeugt. Für die Reproduktion müssen die fertig codierten Dateien bereits in `data/` liegen.
- Skript 04 benötigt `igraph` ab Version 2.1.0.
- Louvain ist nicht deterministisch. Die Stabilität der Community-Zuordnung wird deshalb über 100 Durchläufe berichtet, nicht anhand eines einzelnen Laufs. Trotz gesetztem Startwert können die Ergebnisse je nach `igraph`-Version leicht abweichen.

## Verwendete Software

| Software | Version |
|---|---|
| R | 4.5.1 |
| tidyverse | 2.0.0 |
| igraph | 2.3.3 |
| bursts | 1.0.2 |
| readxl | 1.5.0 |
| writexl | 1.5.4 |
| scales | 1.4.0 |
| here | 1.0.2 |

## Lizenz

Code: MIT

## Nutzung von KI-Tools

Siehe Anhang "Nutzung KI-Tools" der Arbeit.
