# fiks-saksfaser-specification

_Under arbeid_

### Utgangspunkt
Vi har brukt datamodellene for _prosesser_ fra eByggesak (se diagram 1.5 på side 23) som utgangspunkt
https://www.ks.no/globalassets/fagomrader/digitalisering/verktoykasse-plan--og-byggesaker/verktoy/ebyggesak/vedleggspakke-ebyggesak-v2.1.pdf



### Noen mål for protokollen:

- Man skal kunne se framdriften på en sak
- Man skal kunne se hva som har skjedd på en gitt fase
- Det skal gi nok informasjon til at man skal kunne f.eks. sende inn et innspill fra en innsyns/publiseringsløsning.
- Gi nok informasjon om dokumenter til at man skal kunne hente selve dokumentet via Fiks Arkiv

### Notater 

#### Fra møtet 04.09.2024

- Det kom et forslag om å heller kalle protokollen for Fiks Saksbehandling. Dette kan vi ta opp neste gang igjen, men foreløpig kaller vi det fortsatt for Saksfaser.
- Vi lager et github repository med forslag til ny protokoll for saksfaser.
Datamodell kan baseres på eByggesak.
- Vi lager json-schemas basert på datamodellen fra eByggesak.
- Protokollen skal støtte kun 2 hent-meldinger. En for hent sak som gir alt for saken, og en for hent prosess som gir alt for den fasen men etterspør.
- Nøkkel for hent vil være saksnummer for hent sak og saksnummer + en identikator for fasen i hent prosess.
- Tjener (tjener part) i protokollen er typisk saksbehandlingssystemer, og klient (klient part) er typisk publiseringssystemer.
T- jener vil kun gi offentlige data, ikke skjermet data.
- Det er viktig at vi får frikoblet faser og milepæler

#### Fra møtet 11.09.2024
- Vi gikk gjennom utkastene som var laget og gjorde endringer i klassediagrammene. Se siste versjoner lenger nede under [Klassediagram](#klassediagram) og kom gjerne med kommentarer som nytt issue [her](https://github.com/ks-no/fiks-saksfaser-specification/issues).

### Json schemas
_Schemas er ikke oppdatert. Se klassediagram under for innspill_

### Klassediagram


#### Melding - Hent saksfaser

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfaser.hent/classdiagram.svg)

#### Melding - Hent saksfaser resultat

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfaser.hent.resultat/classdiagram.svg)

- Vedtak som Kode under Fase?
- Milepeler er liste under fase. Kan være 2, start og slutt, eller flere. Alt etter brukstilfelle.

#### Melding - Hent saksfase

Henter en enkelt saksfase basert på saksnummer og faseid.
Faseid får man ut fra hent saksfaser tjenesten.

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.prosess.hent/classdiagram.svg)

#### Melding - Hent saksfase resultat

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfase.hent.resultat/classdiagram.svg)

- Listen med dokumenter under Fase er summen av alle dokumenter for alle milepeler.
- Listen med dokumenter under Milepel er nok stort sett bare 1 dokument, men som liste støtter vi evt tilfeller med flere dokumenter. Dokumenter under Milepel vil også ligge i listen under Fase.
- Dokument objektet inneholder referanse til dokumentet slik at det kan hentes og nok metadata til å vise til bruker. 
