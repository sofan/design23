---
Title: About
Description: This is an about page

---

Om sidan
==========================

Denna sida är byggd med Pico CMS. Sidorna är skrivna i Markdown som av Pico görs om till HTML, och template görs med twig.
Jag har i kmom02 lagt till ett tema "kmom02" som använder SASS, där jag har använt mig av nästlade regler, variabler, importerade moduler och mixins. Ett väldigt trevligt sätt att jobba med stilar på. Jag valde att använda @use istället för @import vid import av moduler då SASS själva förespråkar det.


## Fonter
Som fonter används Inter och Tillium Web från Google fonts vilka jag (enligt extrauppgiften) laddad hem och importerat lokalt för att minska antalet beroenden mot andra tjänster.

## Ikoner
Av de ikoner som visas i footern är den ena (Github) en ikon från Font Awesome medan den andra är en Unicode-ikon. Jag ville testa både sätten att göra det på men tänker att det nog är bättre att endast använda Unicode.

## Responsivitet
Sidan är gjord för att vara responsiv och fungera även i mobil. Bilderna är satta till 100% bredd och site-header ändras till flex-direction "column" för att följa sidans bredd när den krymper.

## Färger
Det ljusa temat använder ett komplementärt färgschema där basfärgen är blå och kontrastfärgerna går mot det bruna och orangea håller, vilket skapar en visuell variation.
<div class="colors">
<table>
<tr>
<td style="background-color: #3C6975">
<td style="background-color: #37a6a2">
<td style="background-color: #2F98B5">
<td style="background-color: #A06A37">
<td style="background-color: #f99428">
</tr>
</table>
</div>

Det mörka temat använder har mer mörk och jordnära ton men med lite inslag av guld. Det är inte strikt monokromatiskt, analogt eller komplementärt, utan snarare en kombination av olika färger som fungerar harmoniskt tillsammans och där guldtonen sticker ut en aning.
<div class="colors">
<table>
<tr>
<td style="background-color: #1E1E1E">
<td style="background-color: #313730">
<td style="background-color: #121617">
<td style="background-color: #17272B">
<td style="background-color: #312121">
<td style="background-color: #42341a">
</tr>
</table>
</div>