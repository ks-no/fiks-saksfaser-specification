# ![](KSDigital25.png) Kontrakter og dokumentasjon for Fiks Saksfaser

_Under arbeid_
> Fiks Saksfaser er en modernisering av GI Saksfaser 1.1 og det nye grensesnittet som anbefales brukt.


### Utgangspunkt
Vi har brukt datamodellene for _prosesser_ fra eByggesak (se diagram 1.5 på side 23) som utgangspunkt
https://www.ks.no/globalassets/fagomrader/digitalisering/verktoykasse-plan--og-byggesaker/verktoy/ebyggesak/vedleggspakke-ebyggesak-v2.1.pdf



### Noen mål for protokollen:

- Man skal kunne se framdriften på en sak
- Man skal kunne se hva som har skjedd på en gitt fase
- Det skal gi nok informasjon til at man skal kunne f.eks. sende inn et innspill fra en innsyns/publiseringsløsning.
- Gi nok informasjon om dokumenter til at man skal kunne hente selve dokumentet via Fiks Arkiv


### [Møtereferat](Dokumentasjon/V1/Motereferat/README.md)
Ukentlige møter blir avholdt hvor vi jobber med protokollen.
Notater fra møtene er [her](Dokumentasjon/V1/Motereferat/README.md).

#### Fra møtet 23.10.2024
- Godkjente forrige ukes endringer
- Endret navn fra systemId til milepelId på Milepel
- Endret navn fra planlagtTil til planlagtUtfoert
- Begynte å markere felter som er påkrevd og valgfrie i modellene
- Endret liste med dokumenter til liste med referanseJournalpost
- Diskusjon rundt issue [#10](https://github.com/ks-no/fiks-saksfaser-specification/issues/10). Se kommentarer

### Wiki

Det er opprettet og begynt på en Wiki for Fiks Saksfaser.
Les mer [her](https://github.com/ks-no/fiks-saksfaser-specification/wiki) eller følg lenkene under.

#### [Brukstilfeller](https://github.com/ks-no/fiks-saksfaser-specification/wiki#brukstilfeller)

### Json schemas
_Schemas er ikke oppdatert. Se klassediagram under for innspill_

### Entitet diagrammer

Forklaring for diagrammene:

- Diagrammene viser hvordan datamodellene vil se ut for skjema i protokollen
- Sort punkt foran feltnavn viser felter som er påkrevd. Resten er ikke påkrevd

#### Melding - Hent saksfaser

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfaser.hent/classdiagram.svg)

#### Melding - Hent saksfaser resultat

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfaser.hent.resultat/classdiagram.svg)

- Fase inneholder mulighetene for å gi en liste med dokumenter. Dette er fordi vi gjenbruker fase objektet for hent faser og hent en enkelt fase.
- Milepel inneholder mulighetene for å gi en liste med dokumenter. Dette er fordi vi gjenbruker milepel objektetet for hent faser og hent en enkelt fase.
- Dokumenter vil være ikke påkrevd under milepel eller fase.
- Milepeler er liste under fase. Kan være 2, start og slutt, eller flere. Alt etter brukstilfelle.
- SaksfaserHentResultat: Rekkefølgen av Fase objekter i faser listen er signifikant. Det er den rekkefølgen fasene har.

#### Melding - Hent saksfase

Henter en enkelt saksfase basert på saksnummer og faseid.
Faseid får man ut fra hent saksfaser tjenesten.

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfase.hent/classdiagram.svg)

#### Melding - Hent saksfase resultat

![](Dokumentasjon/V1/ClassDiagrams/no.ks.fiks.saksfaser.v1.saksfase.hent.resultat/classdiagram.svg)

- Listen med dokumenter under Fase er summen av alle dokumenter for alle milepeler.
- Listen med dokumenter under Milepel er nok stort sett bare 1 dokument, men som liste støtter vi evt tilfeller med flere dokumenter. Dokumenter under Milepel vil også ligge i listen under Fase.
- Dokument objektet inneholder referanse til dokumentet slik at det kan hentes og nok metadata til å vise til bruker. 
