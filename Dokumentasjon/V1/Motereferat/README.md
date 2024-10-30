### Notater fra møter

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

#### Fra møtet 18.09.2024
- Vi jobbet videre med resultat for hent saksfaser. Endringer er gjort i uml. Se diagram under.
- Hent Saksfase skal ikke trenge saksnummer som nøkkel. Kun faseid.
- Vi korrigerte noen navn på kodeobjekter.
- Global/intern som attributt på fase og milepel er ikke nødvendig da interne data ikke skal komme som noe resultat i denne protkollen. Kun globale data som skal vises.
- Kodeverdi og kodebeskrivelse for kode-objekter er navn hentet fra andre protokoller som vi ønsker å bruke videre i denne protokollen.
- Det ble diskutert om Milepel som objekt burde være likt i Hent saksfaser og Hent saksfase. Vi konkluderte ikke noe her, men tar det opp igjen på neste møte. Det er fordeler og ulemper med å gjøre det likt.

#### Fra møtet 02.10.2024
- Vi gjorde noen endringer på modellene
- Det dukket opp noen spørsmål som vi registrerte som issues her: https://github.com/ks-no/fiks-saksfaser-specification/issues
- Vedtak på fase kom opp igjen. Vi laget et issue her som vi får dokumentert svar på og jeg tar det inn i dokumentasjonen: https://github.com/ks-no/fiks-saksfaser-specification/issues/5
- Vi kom fram til at vi trenger å få invitert med de som jobber med NPS for å få avklart flere ting etter høstferien.

#### Fra møtet 16.10.2024
Vi så noen endringer vi ønsker å gjøre på Milepel:
- Ta bort Journaldato. Dette finner man via ReferanseJournalpost
- referanseDokument kan ikke være en string, men bør være et objekt slik som i Fiks Arkiv
- Rekkefølgen faser kommer i listen i SaksfaserHentResultat er rekkefølgen fasene har.
- Ta bort erGlobal
- Legge til planlagtTil - dato
- Ta bort listen med dokumenter da dette kan hentes via Fiks Arkiv i stedet

#### Fra møtet 23.10.2024
- Godkjente forrige ukes endringer
- Endret navn fra systemId til milepelId på Milepel
- Endret navn fra planlagtTil til planlagtUtfoert
- Begynte å markere felter som er påkrevd og valgfrie i modellene
- Endret liste med dokumenter til liste med referanseJournalpost
- Diskusjon rundt issue [#10](https://github.com/ks-no/fiks-saksfaser-specification/issues/10). Se kommentarer

#### Fra møtet 30.10.2024
- Litt få på møtet da det er samtidig Byggesaksdager fra DiBk
- Godkjente og merget inn forrige ukes endringer da det ikke har kommet noen kommentarer på det
- For kodelister skal vi henvise Geonorge sine sider: https://register.geonorge.no/kodelister/ebyggesak/milepel
- Kodelistene der skal oppdateres
