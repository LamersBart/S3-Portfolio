<h1 align="center">
  Semester 3
  <br/>
  Portfolio
</h1>
<h3 align="center">
  Bart Lamers
</h3>
<br/>

<p align="center"><img alt="" src="https://c.tenor.com/_DOBjnGspYAAAAAC/code-coding.gif"/></p>

# Inhoudsopgave
* [1. Introductie](#1-introductie)
* [2. Leeruitkomsten](#2-leeruitkomsten)
  * [2.1 Web applicatie](#21-web-applicatie)
  * [2.2 Software kwaliteit](#22-software-kwaliteit)
  * [2.3 Agile methode](#23-agile-methode)
  * [2.4 CI/CD](#24-cicd)
  * [2.5 Culturele verschillen en ethiek](#25-culturele-verschillen-en-ethiek)
  * [2.6 Requirements en design](#26-requirements-en-design)
  * [2.7 Business processen](#27-business-processen)
  * [2.8 Professioneel](#28-professioneel)
* [3. Reflectie](#3-reflectie)
* [Bronvermelding](#bronvermelding)

# 1. Introductie
<details>
<summary>&nbsp;Uitklappen</summary>

In dit document beschijf ik de leeruitkomsten van semester 3 en hoe ik deze heb aangetoond.<br/>
Ook kijk ik middels een reflectie terug op dit semester wat ik heb geleerd en wat ik daarvan meeneem naar semster 4.

</details>

# 2. Leeruitkomsten
## 2.1 Web applicatie
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je ontwerpt en bouwt gebruiksvriendelijke, full-stack webapplicaties.

Gebruiksvriendelijk: Je past basistechnieken voor het testen en ontwikkelen van gebruikerservaringen toe.

Full-stack: Je ontwerpt en bouwt een full-stack applicatie met behulp van algemeen aanvaarde front-end (Javascript-gebaseerd framework) en back-endtechnieken (bijv. Object Relational Mapping), waarbij je relevante communicatieprotocollen kiest en implementeert en problemen met asynchrone communicatie aanpakt.
```

### Hoe heb ik deze leeruitkomst aangetoond:
<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>

#### 2.1.1 Project beschrijving
Chefresh is een app die is ontwikkeld in C# met gebruik van een minimale API-backend en een ReactJS-frontend.

Doel van de app: <br/>
Chefresh: de revolutionaire inventarisatie-app waarmee u uw producten in huis kunt bijhouden op houdbaarheidsdatum!
Zo kom je nooit meer voor verrassingen in de koelkast te staan en bereid je de lekkerste gerechten met etenswaren die het snelst genuttigd moeten worden.
Wel zo fijn voor onze planeet 🌍

#### 2.1.4 Minimal-API of REST-API?
Chefresh versie 1 is een MVC-applicatie met 3-lagen structuur.
Dit was nodig om de leeruitkomsten uit semester 2 aan te tonen.
Nu wil ik de Chefresh app verder optimaliseren en ga ik een API maken die met een losse front-end communiceerd.
Hiervoor heb ik onderzoek gedaan naar een minimal API (zonder controllers) of een standaard API (met controllers) zie 4.6.

#### 2.1.5 Front-end
De front-end van Chefresh is gemaakt in ReactJS i.c.m. bootstrap voor react.
Ik had nog nooit eerder gewerkt met ReactJS dus het was een hele uitdaging om de web-app op de juiste manier te laten functioneren.
In de frond-end maak ik gebruik van Axios voor het versturen van calls naar de back-end.

In het begin liep ik tegen het probleem van cross-origin aan en dat mijn front-end daardoor niet kon communiceren met de back-end.
Na wat aanpassingen in de back-end was dit probleem ook verholpen.

#### 2.1.6 Back-end
Ik heb dit semester opnieuw gekozen voor een backend in C# (.Net6).
In het 2e semester heb ik ook al met C# (.Net6) gewerkt met een MVC-versie van Chefresh.
Omdat ik me meer wilde verdiepen in C# heb ik niet gekozen voor een standaard REST-API met controllers aangezien dit te makkelijk zou zijn met het ombouwen van de MVC-applicatie naar een API.
Daarom heb ik gekozen voor een minimal-API, een API zonder controllers waarbij de endpoints worden aangemaakt in de program.cs.

Omdat Chefresh voornamelijk bestaat uit CRUD-acties heeft een minimal-API als voordeel dat het compacter is dan een standaard-API.
Het was wel even zoeken hoe een minimal-API werkt omdat de documentatie en implementatie er van nog niet zo breed bekend is als de standaard versie van een API.

Gaandeweg ben ik er achter gekomen dat naast de voordelen die een minimal-API met zich mee brengt er ook nadelen zijn.
Zo is het niet mogelijk om een cookie aan te maken in een endpoint, maar uitsluitend in de middleware.
Hierdoor heb ik de JWT-token niet als httpOnly-cookie kunnen meesturen en moest ik de token opslaan in de localstorage van de browser.
Meer hierover heb ik beschreven in mijn onderzoek naar veiligheid.


#### 2.1.7 Beveiliging
**Best practices for storing a JWT in my project:** <br/>
Voor mijn project (.NET 6 Minimal API) API -> (ReactJS) Front-end maak ik gebruik van JWT-tokens voor authenticatie.
Deze tokens moeten ergens worden opgeslagen, dit kan echter op verschillende manieren.
Dit ben ik verder gaan uitzoeken door er onderzoek naar te doen.
Iedere manier heeft namelijk zijn voor- en zijn nadelen en deze ga ik behandelen.

#### 2.1.8 Welke manieren zijn er om JWT-tokens te bewaren?
**LocalStorage:**
Het opslaan van de JWT-token in localStorage heeft als voordeel dat het makkelijk toegankelijk is via JavaScript en dus daardoor gemakkelijker te beheren en op te vragen.
Daarnaast is het persistente opslag, dit houdt in dat zelfs wanneer een browser wordt afgesloten of wanneer een nieuwe tab of verversing van de pagina plaats vindt de gebruiker nog steeds geauthentiseerd is.
Dit kan voor sommige applicaties een uitkomst bieden, zeker als deze uit meerdere pagina’s bestaat zoals Chefresh.

De gemakkelijke toegankelijkheid is ook meteen de grootste valkuil van localStorage,
aangezien iedereen met kennis van JavaScript de tokens zou kunnen onderscheppen.
Dit zorgt voor een veiligheidsrisico XSS-attack.

**SessionStorage:**
Het opslaan van de JWT-token in sessionStorage heeft hetzelfde voordeel als localStorage dat het makkelijk toegankelijk is via JavaScript en dus daardoor gemakkelijker te beheren en op te vragen.
Anders dan localStorage is sessionStorage niet persistente opslag, dit houdt in dat wanneer een browser wordt afgesloten of wanneer een nieuwe tab of verversing van de pagina plaats vindt de gebruiker niet meer geauthentiseerd is.
Dit kan voor sommige applicaties een uitkomst bieden (denk aan een one-page-applicatie), maar voor mijn applicatie is dat juist niet handig.

Net als bij localStorage is de gemakkelijke toegankelijkheid ook meteen de grootste valkuil van sessionStorage,
aangezien iedereen met kennis van JavaScript de tokens zou kunnen onderscheppen.
Dit zorgt voor een veiligheidsrisico XSS-attack.

**Cookies:**
Het opslaan van een JWT-token in de cookies kan op meerdere manieren en heeft als voordeel dat ze volledig te configureren zijn.
Ook cookies zijn persistente opslag, dus net als bij localStorage blijven gebruikers geauthentiseerd.
Indien een cookie juist is geconfigureerd is het ook de veiligste oplossing en ben je tegen XSS-attacks beschermt.
Het nadeel van een “veilige” cookie is dat je deze instelt op HTTPonly, wat inhoudt dat de cookie niet meer bereikbaar is via JavaScript en enkel in de header wordt meegestuurd.
Hierdoor kun je de token dus ook niet meer gebruiken in de front-end laag om data uit te halen.
Maar ook cookies bevatten kwetsbaarheden zoals CSRF-attacks. Het is dus de vraag wat het best werkt voor je applicatie.

#### 2.1.9 Conclusie
Het bewaren van een JWT-token in een httpOnly cookie is het veiligst. Ik heb daarom ook gekeken of ik dit kan toepassen in mijn persoonlijk project.
Echter, omdat ik werk met een minimal-API kan ik alleen cookies aanmaken in de "middleware" en niet in mijn endpoints.
Het probleem is dus dat er dan al een JWT-token moet worden aangemaakt voordat een gebruiker zich kan authentiseren,
hierdoor ben ik genoodzaakt ben gebruik te maken van localstorage, omdat mijn applicatie wel persistente opslag van de token vereist. [^2], [^3], [^4]


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>

#### 2.1.10 Project beschrijving
Ordinner is een applicatie voor gebruik in de horeca.
De app is voorzien van meerdere frond-ends en één back-end.
Zo is er een front-end voor de restaurantgasten die via de web-app een bestelling kunnen plaatsen die vervolgens - via de API - word doorgestuurd naar de front-end voor keuken en bar.
Het was een hele uitdaging om alle requirements te verwezenlijken, maar met goed teamwork is het wel gelukt.
De stakeholders zijn bij alle opleveringen erg enthousiast geweest over het opgeleverde werk, en zijn in het hele process ook nauw betrokken geweest.

#### 2.1.11 Front-end
De front-end van Ordinner is geschreven in ReactJS, ik heb me samen met Britt voornamelijk ingespannen voor het front-end gedeelte van de app.
De front-end is regelmatig aangepast op basis van nieuwe feedback van de stakeholders.
Omdat we werken in het groepsproject met agile is het project eigenlijk nooit "af", maar is er altijd ruimte voor verbetering.
Ik heb de samenwerking met Britt als erg prettig ervaren en we mogen bij zijn met het behaalde resultaat.

#### 2.1.12 Back-end
De back-end van Ordinner is geschreven in JAVA spring-boot en er is gebruik gemaakt van hybernate voor het genereren van de database.
Omdat ik voornamelijk bezig ben geweest met de front-end is er niet een specifiek item uit de back-end wat ik heb gemaakt.
Wel is er veel overleg geweest tussen Maarten en Janine (team back-end) om nieuwe endpoints te maken die vervolgens gebruikt zouden worden in de front-end.

</details>


[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.2 Software kwaliteit
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je maakt gebruik van software tooling en methodiek die de kwaliteit van de software continu monitort en verbetert tijdens de software ontwikkeling.

Tooling en methodiek: Uitvoeren, monitoren en rapporteren van unit integratie-, regressie- en systeemtesten, met aandacht voor security- en performance aspecten, alsmede het toepassen van statische code analyse en code reviews.
```

### Hoe heb ik deze leeruitkomst aangetoond:
<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>

Om de software kwaliteit van mijn app te controleren heb ik gebruik gemaakt van SonarQube.
Ik heb hiervoor SonarQube geinstalleerd op mijn eigen server.<br/>
Via github-actions wordt er bij iedere push op de main branch middelds een yaml file een build van het project uitgevoerd en als deze geslaagd is wordt de code doorgestuurd naar het SonarQube dashboard.


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>

Om de software kwaliteit van het groepsproject te controleren heb ik gebruik gemaakt van SonarQube.
Ik heb hiervoor de sonarqube installatie gebruikt van mijn eigen server<br/>
Via github-actions wordt er bij iedere push en/of pull-request op de master branch middelds een yaml file een build van het project uitgevoerd en als deze geslaagd is wordt de code doorgestuurd naar het SonarQube dashboard.

Na de eerste keer dat SonarQube de code heeft gescand had de back-end de volgende issues:
  * 3 bugs
  * 43 code smells
  * 8 vulnerabilities
  * 1 security hotspot(s)

![img.png](images/GPBackEnd-Sonar-7-12-10-35.png)

Ik heb daarna samen met Janine diverse oplossingen doorgevoerd, daarna had de code de volgende issues:
  * 0 bugs
  * 46 code smells
  * 8 vulnerabilities
  * 0 security hotspot(s)

![img.png](images/GPBackEnd-Sonar-7-12-11-56.png)

Op moment van schrijven (7 december 2022) scooren Reliability, Security Review en Maintainability een 'A' en Security een 'E'

![img.png](images/GPBackEnd-Sonar-7-12-2022.png)

</details>


[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.3 Agile methode
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je kiest en implementeert de meest geschikte agile software ontwikkelmethode voor uw softwareproject.

Kiezen: Je bent op de hoogte van de meest populaire agile methoden en hun onderliggende agile principes.
Je keuze voor een methode is gemotiveerd en gebaseerd op goed gedefinieerde selectiecriteria en contextanalyses.
```

### Hoe heb ik deze leeruitkomst aangetoond:

#### Welke vormen van agile zijn er?
#### vervolgvragen

<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>


</details>


[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.4 CI/CD
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je ontwerpt en implementeert een (semi)automatisch software release proces dat aansluit bij de noden van de projectcontext.

Ontwerp en implementeer: Je ontwerpt een releaseproces en implementeert een oplossing voor continue integratie en implementatie (met behulp van bijvoorbeeld Gitlab CI en Docker).
```

### Hoe heb ik deze leeruitkomst aangetoond:
<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>


</details>

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.5 Culturele verschillen en ethiek
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je herkent en houdt rekening met culturele verschillen tussen projectstakeholders en ethische aspecten bij softwareontwikkeling.

Herkennen: Erkenning is gebaseerd op theoretisch onderbouwde bewustwording van culturele verschillen en ethische aspecten in software engineering.
Houd rekening met: Pas je communicatie-, werk- en gedragsstijlen aan om projectbetrokkenen uit verschillende culturen te weerspiegelen; Spreek een van de standaard Ethische Richtlijnen voor Programmeren (bijv. ACM Code of Ethics and Professional Conduct) in je werk aan.
```

### Hoe heb ik deze leeruitkomst aangetoond:

#### 2.5.1 Wat zijn culturele verschillen?

#### 2.5.2 Welke invloed heeft dit in het werkveld?

#### 2.5.3 Ethiek en ICT

<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>


</details>

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.6 Requirements en design
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je analyseert (niet-functionele) requirements, werkt (architecturale) ontwerpen uit en valideert deze met behulp van meerdere soorten testtechnieken.

Meerdere soorten testtechnieken: Je past gebruikersacceptatietesten en feedback van belanghebbenden toe om de kwaliteit van de vereisten te valideren.
Je evalueert de kwaliteit van het ontwerp (bijvoorbeeld door testen of prototyping) rekening houdend met de geformuleerde kwaliteitseigenschappen zoals veiligheid en prestatie.
```

### Hoe heb ik deze leeruitkomst aangetoond:
<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>

#### 2.6.1 User stories
De user stories heb ik beschreven bij de [issues](https://github.com/LamersBart/S3-Portfolio/issues).
</br>
Ik heb voor de user stories het volgende format gebruikt [^1]: [bron: agilescrumgroup](https://agilescrumgroup.nl/wat-is-een-user-story/](https://agilescrumgroup.nl/wat-is-een-user-story/):
* Als: (klant)
* Wil ik: (beschrijving van datgene dat ontwikkeld moet worden)
* Zodat ik: (beschrijving van de reden waarom dat ontwikkeld moet worden)

#### 2.6.2 Requirements
* Front-end language: ReactJS
* Back-end language: .NET 6
* Backend bestaat uit een Minimal API zodat de app ook door derden kan worden geïmplementeerd
* Database voor het bijhouden van producten en voorraad

</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>

Voor het groepsproject heb ik me voornamelijk bezig gehouden met front-end.
Ik heb hier ook designs en wireframes voor gemaakt.
Na goedkeuring en opmerkingen van de stakeholders zijn deze designs verwekt tot het eindresultaat

Wireframe ([interactieve link](https://www.sketch.com/s/8c5fc696-7497-4b51-8202-7c120f0a2fe2/prototype/a/5AC3CB5E-4325-450B-A216-F6D7D8AA4C84)):

![img.png](images/GP-wireframe.png)

</details>

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.7 Business processen
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je analyseert en beschrijft eenvoudige bedrijfsprocessen die gerelateerd zijn aan jouw project.

Gerelateerd: Bedrijfsprocessen waarbij de software die u aan het ontwikkelen bent wordt gebruikt (bedrijfsprocessen die de software moet ondersteunen door deze geheel of gedeeltelijk te automatiseren).

of

Bedrijfsprocessen die nodig zijn voor het succes van uw softwareontwikkelingsproject (bijv. productrelease, marktrelease, financiële zekerheid).
```

### Hoe heb ik deze leeruitkomst aangetoond:
<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>


</details>

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 2.8 Professioneel
<details>
<summary>&nbsp;Uitklappen</summary>

```
Je handelt op een professionele manier tijdens het ontwikkelen en leren van software.

Professionele manier: Je vraagt en past actief feedback toe van stakeholders en adviseert hen over de meest optimale technische en ontwerpende (bouwkundige) oplossingen.
Je kiest en onderbouwt oplossingen voor een gegeven probleem.
```

### Hoe heb ik deze leeruitkomst aangetoond:
<details>
<summary><b>&nbsp;Individueel project (Chefresh)</b></summary>


</details>
<br/>
<details>
<summary><b>&nbsp;Groepsproject (Ordinner)</b></summary>


</details>

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 3. Reflectie
<details>
<summary>&nbsp;Uitklappen</summary>

Ik heb het derde semester als zeer leerzaam ervaren. Ik heb veel plezier gehad met het groepsproject, onder andere door het fijne team maar ook de leuke opdracht.
Daarnaast heb ik veel geleerd en toegepast, denk aan ReactJS (zowel bij IP als GP) en het gebruik van een minimal-API. Ook de onderzoeken naar beveiliging hebben me veel gebracht.
Ik weet nu wat de beste manier is om een JWT-token te gebruiken en hoe ik op die manier een veilige API kan bouwen. Dit was mijn nog niet gelukt in semester 1 en 2.

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## Bronvermelding

[^2]: [https://tkacz.pro/how-to-securely-store-jwt-tokens/]
[^3]: [https://www.blinkingcaret.com/2018/07/18/secure-an-asp-net-core-web-api-using-cookies/]
[^4]: [https://vivekkrishnavk.medium.com/using-jwts-as-http-only-cookies-with-react-js-a301991fdfa6]