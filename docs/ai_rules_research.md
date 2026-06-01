# AI Arendusassistendi Reeglite Faili Uurimus

## Eesmärk

Käesoleva töö eesmärk on uurida, milliseid reeglite faile erinevad AI arendusassistendid toetavad ning millised tarkvaraarenduse praktikad aitavad tagada AI loodud koodi kvaliteedi, turvalisuse ja töökindluse.

Uurimistöö põhineb ametlikel dokumentatsioonidel ja tarkvaraarenduse parimatel praktikatel.

---

# 1. Millist reeglite faili AI tööriistad toetavad?

Erinevad AI tööriistad kasutavad erinevaid juhisefaile projekti reeglite kirjeldamiseks.

## Claude Code

Claude Code toetab faile:

* `CLAUDE.md`
* `.claude/CLAUDE.md`

Neid kasutatakse püsivate projekti juhiste salvestamiseks, mida Claude kasutab kogu arendustöö vältel.

Allikas:
https://docs.claude.com/en/docs/claude-code/memory

---

## GitHub Copilot

GitHub Copilot toetab faile:

* `.github/copilot-instructions.md`
* `.github/instructions/*.instructions.md`

Need failid võimaldavad määrata projekti-spetsiifilisi juhiseid, mida Copilot arvestab koodi genereerimisel.

Allikas:
https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot

---

## AGENTS.md

AGENTS.md on tööriistadeülene formaat, mida kasutatakse AI agentide käitumise kirjeldamiseks.

Selle eeliseks on tööriistasõltumatus ja võimalus kasutada sama reeglistikku erinevate AI arendusassistentidega.

Allikas:
https://agentsmd.io

---

# 2. Kuidas AI peaks projekti enne muudatuste tegemist analüüsima?

AI ei tohiks alustada kohe koodi kirjutamisest.

Enne muudatuste tegemist peab AI:

1. Uurima projekti struktuuri.
2. Tuvastama kasutatavad tehnoloogiad.
3. Lugema olemasolevat koodi.
4. Mõistma projekti arhitektuuri.
5. Otsima olemasolevaid sarnaseid lahendusi.
6. Analüüsima olemasolevaid teste.

Näiteks tuleks uurida järgmisi faile:

* package.json
* requirements.txt
* pyproject.toml
* go.mod
* Cargo.toml
* docker-compose.yml
* CI konfiguratsioonid

Selline lähenemine vähendab vigade ja ebajärjekindla koodi tekkimise riski.

---

# 3. Kuidas vältida katkise koodi jõudmist main harusse?

Kaasaegses tarkvaraarenduses kasutatakse selleks mitut kaitsekihti.

## Feature Branch

Kõik arendus toimub eraldi harus.

Näiteks:

feature/add-login

See hoiab pooleliolevad muudatused eemal põhiharust.

---

## Pull Request

Enne muudatuste ühendamist luuakse Pull Request.

See võimaldab:

* kontrollida muudatusi;
* arutada lahendust;
* teha koodi ülevaatust.

---

## Branch Protection

Branch Protection piirab tegevusi põhiharus.

Näiteks:

* keelab otsesed commitid main harusse;
* nõuab ülevaatust enne merge'i;
* nõuab edukat CI kontrolli.

Allikas:
https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches

---

## Required Status Checks

Merge lubatakse ainult siis, kui kõik kontrollid on edukalt läbitud.

Näiteks:

* testid;
* linting;
* build;
* type checking.

---

## CI Pipeline

Continuous Integration süsteem käivitab automaatsed kontrollid iga muudatuse korral.

Levinud kontrollid:

* testid;
* linting;
* build;
* turvakontrollid.

Allikas:
https://docs.github.com/en/actions

---

## Automated Tests

Automaatsed testid kontrollivad, et olemasolev funktsionaalsus ei puruneks.

---

## Linting

Linting leiab:

* süntaksivead;
* stiilivead;
* riskantsed konstruktsioonid.

Näited:

* ESLint
* Pylint
* Ruff

---

## Type Checking

Tüübikontroll leiab vead enne programmi käivitamist.

Näiteks TypeScripti puhul:

tsc --noEmit

---

## Code Review

Koodi ülevaatus aitab avastada:

* loogikavigu;
* turvaprobleeme;
* arhitektuurilisi probleeme.

Automaatkontroll ei asenda inimülevaatust.

---

# 4. Kuidas vältida regressioone?

Regressioon tähendab olukorda, kus varem parandatud viga ilmub uuesti.

Kõige tõhusam meetod regressioonide vältimiseks on regressioonitest.

## Regressioonitesti põhimõte

Bugi parandamisel tuleb:

1. kirjutada test, mis vea taastoodab;
2. veenduda, et test enne parandust ebaõnnestub;
3. teha parandus;
4. kontrollida, et test pärast parandust õnnestub.

See tagab, et sama probleem ei naase tulevikus märkamatult.

Paljud arendusmeeskonnad peavad bug fix'i lõpetamata tööks, kui regressioonitesti ei lisata.

---

# 5. Milliseid käske peab AI enne töö lõpetamist käivitama?

Enne töö valmisks märkimist tuleb käivitada kõik projekti kvaliteedikontrollid.

## Testid

Näited:

npm test

või

pytest

---

## Lint

Näited:

npm run lint

või

ruff check .

---

## Type Checking

Näide:

tsc --noEmit

---

## Build

Näide:

npm run build

---

## Formatter

Näide:

prettier --check .

---

## Security ja Dependency Check

Näited:

npm audit

pip-audit

Dependabot

OWASP Dependency Check

Need aitavad leida teadaolevaid turvanõrkuseid sõltuvustes.

---

# 6. Kuidas piirata AI muudatuste ulatust?

AI üks peamisi riske on liiga suurte muudatuste tegemine.

Seetõttu tuleks järgida järgmisi põhimõtteid.

## Muuda ainult seotud faile

Kui probleem puudutab autentimist, ei tohiks AI muuta maksete või teavituste mooduleid.

---

## Väikesed muudatused

Väikseid muudatusi on:

* lihtsam üle vaadata;
* lihtsam testida;
* lihtsam tagasi võtta.

---

## Väldi põhjendamatut refaktoreerimist

Kui ülesanne on parandada üks viga, ei tohiks AI samaaegselt ümber kirjutada kogu arhitektuuri.

---

## Säilita olemasolev arhitektuur

AI peaks eelistama olemasolevate mustrite järgimist uute lahenduste leiutamise asemel.

---

# 7. Millal peab AI kasutajalt kinnitust küsima?

AI ei tohiks teha kõrge mõjuga muudatusi ilma kasutaja nõusolekuta.

Kinnitust tuleks küsida järgmiste tegevuste korral:

## Andmebaasi skeemi muutmine

Näiteks:

* tabelite muutmine;
* veergude kustutamine;
* migratsioonid.

---

## Uute dependency’de lisamine

Iga uus sõltuvus suurendab:

* hoolduskoormust;
* turvariski;
* projekti keerukust.

---

## Failide kustutamine

Oluliste failide kustutamine peab olema teadlik otsus.

---

## Avaliku API muutmine

API muudatused võivad lõhkuda olemasolevad kliendid.

---

## Turvalisusega seotud muudatused

Näiteks:

* autentimine;
* autoriseerimine;
* tokenid;
* sessioonid;
* õiguste kontroll.

---

## Suured refaktoreerimised

Kui muudatus puudutab suurt osa projektist või paljusid faile, peab AI enne jätkamist kinnitust küsima.

---

# Kokkuvõte

Uurimistöö põhjal saab teha kolm peamist järeldust:

1. AI peab enne koodi genereerimist põhjalikult analüüsima olemasolevat projekti ja selle arhitektuuri.
2. Katkise koodi jõudmist põhiharusse aitab vältida mitmekihiline kvaliteedikontroll: feature branch, pull request, branch protection, CI, automaattestid ja code review.
3. AI loodud muudatused peavad olema võimalikult väikesed, testitud ning bug fix’ide korral peab olema lisatud regressioonitest.

---

# Kasutatud allikad

1. Anthropic Claude Code Documentation
   https://docs.claude.com/en/docs/claude-code/memory

2. GitHub Copilot Documentation
   https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot

3. GitHub Branch Protection Documentation
   https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches

4. GitHub Actions Documentation
   https://docs.github.com/en/actions

5. AGENTS.md Project
   https://agentsmd.io
