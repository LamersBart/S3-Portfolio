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

## Inhoudsopgave
* [1. Introductie](#1-introductie)
* [2. Leeruitkomsten (English)](#2-leeruitkomsten-english)
* [3. Onderzoek](#3-onderzoek)
    * 3.1 Beveiliging
      * 3.1.1 Welke manieren zijn er om JWT-tokens te bewaren?
      * 3.1.2 Conclusie
    * 3.2 Agile
      * 3.2.1 Welke vormen van agile zijn er?
      * 3.2.2 Conclusie
    * 3.3 Culturele verschillen
      * 3.3.1 Wat zijn culturele verschillen?
      * 3.3.2 Conclusie
* [4. Individueel project (Chefresh)](#4-individueel-project-chefresh)
    * 4.1 Project beschrijving
    * 4.2 User stories
    * 4.3 Requirements
    * 4.4 Minimal API or REST API?
    * 4.5 Frond-end
    * 4.6 Back-end
* [5. Groepsproject (Ordinner)](#5-groepsproject-ordinner)
    * 5.1 Project beschrijving
    * 5.2 Front-end
    * 5.3 Back-end
* [6. Reflectie](#6-reflectie)
        
## 1. Introductie

<details>
<summary> </summary>
In this document I describe the learning outcomes, 
</details>

## 2. Leeruitkomsten (English)

<details>
<summary> </summary>
<table>
  <tr>
    <th>#</th>
    <th>Name</th>
    <th>Clarification</th>
  </tr>
  <tr>
    <td>
      1
    </td>
    <td>
      You design and build user-friendly, full-stack web applications.
    </td>
    <td>
      User friendly: You apply basic User experience testing and development techniques.
      <br/>
      <br/>
      Full-stack: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.
    </td>
  </tr>
  <tr>
    <td>
      2
    </td>
    <td>
      You use software tooling and methodology that continuously monitors and improve the software quality during software development.
    </td>
    <td>
      Tooling and methodology: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.
    </td>
  </tr>
  <tr>
    <td>
      3
    </td>
    <td>
      You choose and implement the most suitable agile software development method for your software project.
    </td>
    <td>
      Choose: You are aware of the most popular agile methods and their underlying agile principles. Your choice of a method is motivated and based on well-defined selection criteria and context analyses.
    </td>
  </tr>
  <tr>
    <td>
      4
    </td>
    <td>
      You design and implement a (semi)automated software release process that matches the needs of the project context.
    </td>
    <td>
      Design and implement: You design a release process and implement a continuous integration and deployment solution (using e.g. Gitlab CI and Docker).
    </td>
  </tr>
  <tr>
    <td>
      5
    </td>
    <td>
      You recognize and take into account cultural differences between project stakeholders and ethical aspects in software development.
    </td>
    <td>
      Recognize: Recognition is based on theoretically substantiated awareness of cultural differences and ethical aspects in software engineering.
      <br/>
      <br/>
      Take into account: Adapt your communication, working, and behavior styles to reflect project stakeholders from different cultures; Address one of the standard Programming Ethical Guidelines (e.g., ACM Code of Ethics and Professional Conduct) in your work.
    </td>
  </tr>
  <tr>
    <td>
      6
    </td>
    <td>
      You analyze (non-functional) requirements, elaborate (architectural) designs and validate them using multiple types of test techniques.
    </td>
    <td>
      Multiple types of test techniques: You apply user acceptance testing and stakeholder feedback to validate the quality of the requirements. You evaluate the quality of the design (e.g., by testing or prototyping) taking into account the formulated quality properties like security and performance.
    </td>
  </tr>
  <tr>
    <td>
      7
    </td>
    <td>
      You analyze and describe simple business processes that are related to your project.
    </td>
    <td>
      Simple: Involving stakeholders, predominantly sequential processes with one or two alternative paths.
      <br/>
      <br/>
      Related: Business processes during which the software that you are developing will be used (business processes that the software must support by fully or partially automating them).
      <br/>
      <br/>
      or
      <br/>
      <br/>
      Business processes needed for the success of your software development project (e.g., product release, market release, financial assurance).
    </td>
  </tr>
  <tr>
    <td>
      8
    </td>
    <td>
      You act in a professional manner during software development and learning.
    </td>
    <td>
      Professional manner: You actively ask and apply feedback from stakeholders and advise them on the most optimal technical and design (architectural) solutions. You choose and substantiate solutions for a given problem.
    </td>
  </tr>
</table>

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 3. Onderzoek

<details>
<summary> </summary>
Door middel van onderzoek heb ik de volgende leeruitkomsten aangetoond:
<br/>
Leeruitkomsten 2, 3 en 5

### 3.1 Beveiliging
**Best practices for storing a JWT in my project:** <br/>
Voor mijn project (.NET 6 Minimal API) API -> (ReactJS) Front-end maak ik gebruik van JWT-tokens voor authenticatie.
Deze tokens moeten ergens worden opgeslagen, dit kan echter op verschillende manieren.
Dit ben ik verder gaan uitzoeken door er onderzoek naar te doen. 
Iedere manier heeft namelijk zijn voor- en zijn nadelen en deze ga ik behandelen.

#### 3.1.1 Welke manieren zijn er om JWT-tokens te bewaren?
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

#### 3.1.2 Conclusie
Het bewaren van een JWT-token in een httpOnly cookie is het veiligst. Ik heb daarom ook gekeken of ik dit kan toepassen in mijn persoonlijk project.
Echter, omdat ik werk met een minimal-API kan ik alleen cookies aanmaken in de "middleware" en niet in mijn endpoints.
Het probleem is dus dat er dan al een JWT-token moet worden aangemaakt voordat een gebruiker zich kan authentiseren,
hierdoor ben ik genoodzaakt ben gebruik te maken van localstorage, omdat mijn applicatie wel persistente opslag van de token vereist. [^2], [^3], [^4]

### 3.2 Agile

#### 3.2.1 Welke vormen van agile zijn er?

#### 3.2.2 Conclusie

### 3.3 Culturele verschillen

#### 3.3.1 Wat zijn culturele verschillen?

#### 3.3.2 Welke invloed heeft dit in het werkveld?

#### 3.3.3 Conclusie


[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)
  
</details>

## 4. Individueel Project (Chefresh)

<details>
<summary> </summary>
Met mijn individuele project (IP) heb ik de volgende leeruitkomsten aangetoond:
<br/>
Leeruitkomsten 1, 2, 4 en 6

### 4.1 Project beschrijving
Chefresh is a app developed in C# with the use of a minimal-API backend and a ReactJS front-end.

Purpose of the app: <br/>
Chefresh: the revolutionary inventory app that allows you to keep track of your products in the house by best before date!
This way you will never be faced with surprises in the fridge again, and you can prepare the tastiest dishes with food that needs to be consumed the fastest.
So nice for our planet 🌍

### 4.2 User stories
De user stories heb ik beschreven bij de [issues](https://github.com/LamersBart/S3-Portfolio/issues).
</br>
Ik heb voor de user stories het volgende format gebruikt [^1]: [bron: agilescrumgroup](https://agilescrumgroup.nl/wat-is-een-user-story/](https://agilescrumgroup.nl/wat-is-een-user-story/):
* Als: (klant)
* Wil ik: (beschrijving van datgene dat ontwikkeld moet worden)
* Zodat ik: (beschrijving van de reden waarom dat ontwikkeld moet worden)

### 4.3 Requirements
* Front-end language: ReactJS
* Back-end language: .NET 6
* Backend bestaat uit een Minimal API zodat de app ook door derden kan worden geïmplementeerd
* Database voor het bijhouden van producten en voorraad

### 4.4 Minimal API or REST API?
Chefresh versie 1 is een MVC-applicatie met 3-lagen structuur.
Dit was nodig om de leeruitkomsten uit semester 2 aan te tonen.
Nu wil ik de Chefresh app verder optimaliseren en ga ik een API maken die met een losse front-end communiceerd.
Hiervoor heb ik onderzoek gedaan naar een minimal API (zonder controllers) of een standaard API (met controllers) zie 4.6.

### 4.5 Front-end
De front-end van Chefresh is gemaakt in ReactJS i.c.m. bootstrap voor react.
Ik had nog nooit eerder gewerkt met ReactJS dus het was een hele uitdaging om de web-app op de juiste manier te laten functioneren.
In de frond-end maak ik gebruik van Axios voor het versturen van calls naar de back-end.

In het begin liep ik tegen het probleem van cross-origin aan en dat mijn front-end daardoor niet kon communiceren met de back-end.
Na wat aanpassingen in de back-end was dit probleem ook verholpen.


### 4.6 Back-end
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

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)

</details>

## 5. Groepsproject (Ordinner)

<details>
<summary> </summary>
Met het groepsproject (GP) heb ik de volgende leeruitkomsten aangetoond:
<br/>
Leeruitkomsten 3, 6, 7 en 8

### 5.1 Project beschrijving
Ordinner is een applicatie voor gebruik in de horeca.
De app is voorzien van meerdere frond-ends en één back-end.
Zo is er een front-end voor de restaurantgasten die via de web-app een bestelling kunnen plaatsen die vervolgens - via de API - word doorgestuurd naar de front-end voor keuken en bar.
Het was een hele uitdaging om alle requirements te verwezenlijken, maar met goed teamwork is het wel gelukt.
De stakeholders zijn bij alle opleveringen erg enthousiast geweest over het opgeleverde werk, en zijn in het hele process ook nauw betrokken geweest. 
  
### 5.2 Front-end
De front-end van Ordinner is geschreven in ReactJS, ik heb me samen met Britt voornamelijk ingespannen voor het front-end gedeelte van de app.
De front-end is regelmatig aangepast op basis van nieuwe feedback van de stakeholders.
Omdat we werken in het groepsproject met agile is het project eigenlijk nooit "af", maar is er altijd ruimte voor verbetering.
Ik heb de samenwerking met Britt als erg prettig ervaren en we mogen bij zijn met het behaalde resultaat.

### 5.3 Back-end
De back-end van Ordinner is geschreven in JAVA spring-boot en er is gebruik gemaakt van {ORM} voor het genereren van de database.
Omdat ik voornamelijk bezig ben geweest met de front-end is er niet een specifiek item uit de back-end wat ik heb gemaakt.
Wel is er veel overleg geweest tussen Maarten en Janine (team back-end) om nieuwe endpoints te maken die vervolgens gebruikt zouden worden in de front-end.
Ook deze samenwerking is prettig verlopen.

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)  
  
</details>

## 6. Reflectie

<details>
<summary> </summary>
Ik heb het derde semester als zeer leerzaam ervaren. Ik heb veel plezier gehad met het groepsproject, onder andere door het fijne team maar ook de leuke opdracht.
Daarnaast heb ik veel geleerd en toegepast, denk aan ReactJS (zowel bij IP als GP) en het gebruik van een minimal-API. Ook de onderzoeken naar beveiliging hebben me veel gebracht.
Ik weet nu wat de beste manier is om een JWT-token te gebruiken en hoe ik op die manier een veilige API kan bouwen. Dit was mijn nog niet gelukt in semester 1 en 2.

[⬆️ Terug naar inhoudsopgave](#inhoudsopgave)  
  
</details>

### Bronvermelding

[//]: # ()
[//]: # ([^2]: [https://tkacz.pro/how-to-securely-store-jwt-tokens/])

[//]: # ([^3]: [https://www.blinkingcaret.com/2018/07/18/secure-an-asp-net-core-web-api-using-cookies/])

[//]: # ([^4]: [https://vivekkrishnavk.medium.com/using-jwts-as-http-only-cookies-with-react-js-a301991fdfa6])
