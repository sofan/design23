---
Title: Load
Description: This is my Load report page
Template: report

---

# Laddningstid och användbarhet

Uppgiften är att analysera tre webbsidor med avseende på laddningstid och användbarhet och analysera vad som kan förbättras.


Urval
-----------------------
Jag har valt följande tre sidor att.
- <a href="https://www.norrkopingssymfoniorkester.se/" target="_blank">Norrköpings symfoniorkester</a>
- <a href="https://cnema.se/" target="_blank">Cnema</a>
- <a href="https://www.filmstaden.se/" target="_blank">Filmstaden</a>

Alla dessa sidor erbjuder evenemang och använder sig av många bilder och filmer för att locka kunder.
Jag har valt att analysera startsidan, en event-sida, samt kontaktsidan.

Metod
-----------------------
Som verktyg har PageSpeed Insights används tillsammans med tillägget Lighthouse i Chrome.
De analysmått som tagits hänsyn till är:
- **LCP** -     Largest Contentful Paint. Den tid det tar för den största innehållsrika elementet på en webbsida att visas för användaren. För en bra användarupplevelse bör denna vara max 2.5 sekunder.
- **FID** - First Input Delay. Tiden det tar från det att en användare först interagerar med sidan till det att webbläsaren faktiskt kan svara på den interaktionen. Denna tid bör vara maximalt 100 ms för en bra användarupplevelse.
- **CLS** - Cumulative Layout Shift. Hur mycket sidans innehåll rör sig eller förskjuts under laddningsprocessen.

Fokus för analysen är mobila enheter (men anger även prestanda för desktop visas i resultattabellen).



Resultat
-----------------------
I tabellen nedan listas resultaten för de olika sidorna och därefter följer en analys av respektive sida.

<div class="embed-container load">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vSivhktTQCMMIQLBMWS2vyEJlFLMXeQ3LQ-1Cv_hxXksX2s0ZdhEdjw0vsSTabLGGM6MQbJO_YMZeFG/pubhtml?gid=634347005&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
</div>

---

### Norrköpings Symfoniorkester

<picture>
    <source media="(min-width: 500px)" srcset="%assets_url%/img/analysis/son.webp">
    <img src="%assets_url%/img/analysis/son_liten.webp?w=400" alt="SON">
</picture>


#### Prestanda
Alla sidor har låg prestanda med hög LCP. På startsidan och eventsidan finns många bilder samt video som ska laddas och därmed ökar laddtiden. Lite förvånande är att även kontakt-sidan med enbart en enda bild även den har låg prestanda, där verkar det mer vara tredjepartskod och javascript som är begränsande.

#### Rekommendationer
Rekommendationer som fås är att förladda bilder, använda modernare bildformat samt minska påverkan av tredjepartskod.
Inspekterar man nätverkstrafiken går det ändå att se att de försöker förbättra prestandan genom att använda WebP till viss del samt nyttja modulen <code>lazysizes</code> för "lazy loading" av bilder och andra resurser.

---

### Cnema

<picture>
    <source media="(min-width: 500px)" srcset="%assets_url%/img/analysis/cnema.webp">
    <img src="%assets_url%/img/analysis/cnema_liten.webp?w=400" alt="SON">
</picture>

#### Prestanda
Även här ses en dålig prestanda. Mycket på grund av bilder som laddas i större format än vad som behövs (t.ex. är personbilderna på kontaktsidan 1200 px breda men på webbsidan är de som störst 340 px breda).
DOM-trädet är väldigt stort med totalt 2406 DOM-element och ett största djup på 25 samt ett stort antal underordnade element (som mest 978 underlement, då man i en datumväljare lite onödigt ger användaren möjlighet att boka bio fram till år 3000). Detta kan göra sidan långsammare.

#### Rekommendationer
Använda modernare bildformat som WebP. Använda width och height för bilderna för att förbättra CLS. Minska antalet DOM-element.
Använd "lazy loading" för att skjuta upp inläsningen av bilder. Ta bort oanvänd Javascript och CSS.


---

### Filmstaden

<picture>
    <source media="(min-width: 500px)" srcset="%assets_url%/img/analysis/filmstaden.webp">
    <img src="%assets_url%/img/analysis/filmstaden_liten.webp?w=400" alt="SON">
</picture>

#### Prestanda
Prestandan är dålig på alla analyserade sidor. Flera bilder laddas i för stor storlek mot vad som behövs. Alla film-bilder laddas via ett API som returnerar bilden i full storlek (width = 1920 px), men som på sidan endast visas med ca 230 px bredd.


#### Rekommendationer
Använda bilder i modernare format och i rätt storlek. Reducera Javascript och CSS som inte används.


Analys
-----------------------
Resultatet visar att all tre webbplatser får dåliga resultat vad gäller laddningstid. Mycket beroende på bilder som laddas i fel format och storlek. Norrköpings symfoniorkester använder ändå "lazy loading" men lyckas trots det inte få tillräckligt bra prestanda.
Den sida som ändå får bäst totalt resultat är Cnema, som trots sitt enorma DOM-träd ändå får till en bättre laddningstid än övriga sidor. Den som lyckas sämst är Filmstaden, vars prestanda dras ner kraftigt på grund av all de bilder som laddas via API och inte returneras i anpassade storlekar.

Trots dessa dåliga resultat vill jag ändå påstå att jag själv inte störs av laddningstiden på sidorna. Jag tycker att den känns acceptabel när jag laddar sidorna via mobil.


Referenser
-----------------------

<a href="https://pagespeed.web.dev/" target="_blank">Pagespeed Insights</a>


Övrigt
-----------------------

Rapporten är skriven av mig Sofie Strömberg