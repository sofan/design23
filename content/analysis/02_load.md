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
Jag har valt att analysera startsidan, en event/film-sida, samt kontaktsidan.

Metod
-----------------------
Som verktyg används PageSpeed Insights för att mäta prestanda samt se förslag på förbättringsåtgärder. DevTools flik Nätverk används för att mäta antal efterfrågade resurser, den tid det tar för alla resurser att laddas och sidans totala storlek.

De detaljerade analysmått som tagits hänsyn till för prestanda är följande:
- **LCP** - Largest Contentful Paint. Den tid det tar för den största innehållsrika elementet på en webbsida att visas för användaren. För en bra användarupplevelse bör denna vara max 2.5 sekunder.
- **FID** - First Input Delay. Tiden det tar från det att en användare först interagerar med sidan till det att webbläsaren faktiskt kan svara på den interaktionen. Denna tid bör vara maximalt 100 ms för en bra användarupplevelse.
- **CLS** - Cumulative Layout Shift. Hur mycket sidans innehåll rör sig eller förskjuts under laddningsprocessen.




Resultat
-----------------------
I tabellen nedan listas resultaten för de olika sidorna samt ett snittbetyg för varje webbplats. Därefter följer en kort analys av respektive sida.

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
Alla sidor har låg prestanda med hög LCP. På startsidan och eventsidan finns många bilder samt video som ska laddas. Lite förvånande är att även kontakt-sidan med enbart en enda bild även den har låg prestanda, där verkar det mer vara tredjepartskod och Javascript som är begränsande.

#### Rekommendationer
Rekommendationer som fås är att förladda bilder, använda modernare bildformat samt minska påverkan av tredjepartskod.
Inspekterar man nätverkstrafiken går det ändå att se att de försöker förbättra prestandan genom att till viss del använda bildformatet WebP samt att de nyttjar modulen <code>lazysizes</code> för "lazy loading" av bilder och andra resurser. Men trots dessa åtgärder lyckas inte sidan få ett godkänt betyg.

---

### Cnema

<picture>
    <source media="(min-width: 500px)" srcset="%assets_url%/img/analysis/cnema.webp">
    <img src="%assets_url%/img/analysis/cnema_liten.webp?w=400" alt="SON">
</picture>

#### Prestanda
Här ser vi en sida med många och stora bilder som ska laddas, vilket ger en dålig prestanda. Till exempel är personbilderna på kontaktsidan 1200 px breda men på webbsidan är de som störst 340 px breda, och den bild som visas på filmsidan är 3800 px bred vilket är mycket större än vad som egentligen behövs.
DOM-trädet är dessutom väldigt stort med totalt 2406 DOM-element och ett största djup på 25 samt ett stort antal underordnade element (som mest 978 underlement, då man i en datumväljare lite onödigt ger användaren möjlighet att boka bio fram till år 3000).

#### Rekommendationer
Använda modernare bildformat som WebP och anpassa bildernas storlek bättre efter sidans behov. Använda width och height för bilderna för att förbättra CLS. Minska antalet DOM-element.
Använda "lazy loading" för att skjuta upp inläsningen av bilder. Ta bort oanvänd Javascript och CSS.


---

### Filmstaden

<picture>
    <source media="(min-width: 500px)" srcset="%assets_url%/img/analysis/filmstaden.webp">
    <img src="%assets_url%/img/analysis/filmstaden_liten.webp?w=400" alt="SON">
</picture>

#### Prestanda
Även denna sida har en dålig prestanda på alla analyserade sidor. Flera bilder laddas i för stor storlek mot vad som behövs. Till exempel kan man se att alla film-bilder laddas via ett API som returnerar bilden i full storlek (width = 1920 px), men som på sidan endast visas med ca 230 px bredd.


#### Rekommendationer
Använda bilder i modernare format och i rätt storlek. Reducera Javascript och CSS som inte används.


Analys
-----------------------
Alla analyserade webbsidor får fårvånansvärt dåligt betyg på prestanda. Det är många resurser som ska laddas och laddtiderna är långa, mycket på grund av att bilder laddas i fel format och storlek. Norrköpings symfoniorkester är den enda sida som använder "lazy loading" samt modernare bildformat, men lyckas trots det inte få godkänt betyg även om dessa åtgärder ändå lyfter webbsidan högre än övriga analyserade sidor.


### Topplista

1. **Norrköpings Symfoniorkester**. Vinnare, trots ej godkänt betyg och trots sämst LCP. Men genom att använda modernare bildformat samt "lazy loading" skapas en  bättre användarupplevelse.
2. **Filmstaden**. Stora bilder som laddas via API i fel format gör sidan långsam.
3. **Cnema**. Många och tunga bilder bilder gör sidan långsam. Har lite kortare laddtid än Filmstaden, och har faktiskt bäst LCP men hamnar ändå på sista plats på grund av alla de otroligt stora resurser som ska läsas in.

### Laddningstider

Trots de dåliga resultaten vill jag ändå påstå att jag själv inte störs nämnvärt av laddningstiden på sidorna. För mig känns LCP som ett viktigare mått än den absoluta laddningstiden. Ingen av de analyserade sidorna har enligt Pagespeed godkänd LCP (maximalt 2,5) så min upplevelse stämmer inte helt överens med dessa resultat då jag tycker att de laddade tillräckligt snabbt även via mobil.
Filmstaden är den sida som hade högst absolut laddningstid, med ca 11 sekunder i snitt, men som användare märker jag inte det då huvudinnehållet laddas snabbare än så.


Referenser
-----------------------

<a href="https://pagespeed.web.dev/" target="_blank">Pagespeed Insights</a>


Övrigt
-----------------------

Rapporten är skriven av mig Sofie Strömberg