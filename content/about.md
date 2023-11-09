---
Title: About
Description: This is an about page

---

Om sidan
==========================

Denna sida är byggd med Pico CMS. Sidorna är skrivna i Markdown som av Pico görs om till HTML, och template görs med twig.
Jag har i kmom02 lagt till ett tema "kmom02" som använder SASS, där jag har använt mig av nästlade regler, variabler, importerade moduler och mixins. Ett väldigt trevligt sätt att jobba med stilar på. Jag valde att använda @use istället för @import vid import av moduler då SASS själva förespråkar det.


## Fonter
Som fonter används Roboto och Tillium Web från Google fonts vilka jag (enligt extrauppgiften) laddad hem och importerat lokalt för att minska antalet beroenden mot andra tjänster.

## Ikoner
Av de ikoner som visas i footern är den ena (Github) en ikon från Font Awesome medan den andra är en Unicode-ikon. Jag ville testa både sätten att göra det på men tänker att det nog är bättre att endast använda Unicode.

## Responsivitet
Sidan är gjord för att vara responsiv och fungera även i mobil. Bilderna är satta till 100% bredd och site-header ändras till flex-direction "column" för att följa sidans bredd när den krymper.