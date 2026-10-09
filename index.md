---
permalink: /
---

{% comment %}
  De voorbeelden (zin, opschrift en het beeld van de fiche) komen uit de app:
  tools/website_fiches.dart haalt elke zin door de echte herkenning en
  tekent wat de app ervan maakt; tools/build_website_beeld.py zet ze in
  _data/voorbeelden.json en assets/beeld/fiches/. Niet met de hand wijzigen.
{% endcomment %}
{% assign eerste = site.data.voorbeelden | first %}

<section class="opening">
  <h1 class="slogan">Zeg wat je ziet.<br>KLAPekster schrijft het op.</h1>
  <p class="inleiding">Een gratis app voor vogelaars. Je spreekt je waarneming
  in, en KLAPekster maakt er een nette waarneming van voor waarnemingen.be of
  waarneming.nl.</p>
  {% include playknop.html %}
</section>

<section class="toonbeeld" aria-label="Voorbeeld">
  <figure>
    <figcaption class="wie">Jij spreekt, KLAPekster luistert mee…</figcaption>
    <img class="scherm" src="{{ '/assets/beeld/luisterbeeld.webp' | relative_url }}" alt="De klapekster op zijn paal in de heide luistert. In zijn wolk staat: {{ eerste.zin }}" width="384" height="600">
  </figure>
  <figure>
    <figcaption class="wie">…en maakt er dit van:</figcaption>
    <img class="fiche" src="{{ '/assets/beeld/fiches/' | append: eerste.naam | append: '.webp' | relative_url }}" alt="Drie waarnemingen: drie kieviten overvliegend west, twee wulpen ter plaatse en een grutto roepend" width="{{ eerste.breedte }}" height="{{ eerste.hoogte }}">
  </figure>
</section>

## KLAPekster herkent geen vogels. Jij wel.

Zij verstaat jou. Je zegt wat je ziet of hoort, gewoon zoals je het tegen een
andere vogelaar zou zeggen, en de app maakt er een waarneming van: soort,
aantal, gedrag, leeftijd, plek en tijd. Ze luistert naar jou, niet naar de
vogels. Het determineren blijft jouw werk.

## Zeg het zoals je het ziet

<p class="flauw">Echte zinnen, en wat de app er zelf van maakt.<span class="alleen-telefoon"> Veeg opzij voor meer.</span></p>

<div class="voorbeelden">
{% for v in site.data.voorbeelden offset:1 %}
  <figure class="voorbeeld">
    <figcaption>
      <span class="opschrift">{{ v.opschrift }}</span>
      <span class="voorbeeldzin">“{{ v.zin }}”</span>
    </figcaption>
    <img src="{{ '/assets/beeld/fiches/' | append: v.naam | append: '.webp' | relative_url }}" alt="Wat KLAPekster maakt van: {{ v.zin }}" width="{{ v.breedte }}" height="{{ v.hoogte }}" loading="lazy">
  </figure>
{% endfor %}
</div>

## Bijna zonder scherm

Je ogen bij de vogel, de telefoon in je hand of je zak.

<ol class="stappen">
  <li>
    <h3>Druk en spreek</h3>
    <p>Houd de volumeknop, de knop van een bedraad oortje of een losse
    Flic-knop ingedrukt, en zeg wat je ziet.</p>
  </li>
  <li>
    <h3>Luister</h3>
    <p>KLAPekster kan je waarneming hardop teruglezen. Zo hoor je of het klopt,
    zonder te kijken. Niet goed gehoord door de wind? Laat het nog eens
    voorlezen.</p>
  </li>
  <li>
    <h3>Bevestig</h3>
    <p>Kort tikken bewaart de waarneming. Met een andere knop gooi je ze weg
    en spreek je opnieuw.</p>
  </li>
</ol>

<p class="flauw">Welke knop wat doet, kies je zelf in de instellingen. De app
moet wel open staan met het scherm aan; dat dimt vanzelf, om je batterij te
sparen.</p>

## Wat ze verstaat

- Tot acht vogels in één zin, elk met een eigen aantal en gedrag.
- Aantal, gedrag, leeftijd, geslacht, kleed, kleurvorm en vliegrichting.
- Een groep opsplitsen: “waarvan vijf noord en drie west”.
- Een koppel, of een ouder met jongen.
- De prooi of de plant: “jagend op veldmuis”.
- Twijfel: “sperwer of havik”, “waarschijnlijk tweede kalenderjaar”.
- Schattingen: “ongeveer vijftig”, “een stuk of tien”.
- Bijna duizend vogelsoorten, bijna tweehonderd volks- en dialectnamen, en
  ruim elfhonderd manieren waarop de spraakherkenning een vogelnaam verkeerd
  verstaat.

## Zo werkt het

<ol class="stappen">
  <li>
    <h3>Zeg het</h3>
    <p>Tik op de knop en spreek, gewoon zoals je praat:
    <span class="zin-kort">“Drie koolmezen overvliegend noord.”</span></p>
  </li>
  <li>
    <h3>Kijk het na</h3>
    <p>Je ziet meteen een fiche met de soort, het aantal en het gedrag. Klopt
    er iets niet, dan pas je het aan met een tik.</p>
  </li>
  <li>
    <h3>Stuur het door</h3>
    <p>Na je wandeling stuur je alles in één keer naar waarnemingen.be of
    waarneming.nl, met je eigen account.</p>
  </li>
</ol>

## Voor wie

Voor wie in de tuin naar de voederplaats kijkt en niet telkens een lijst wil
openen. Voor wie wandelt en de verrekijker niet wil laten zakken om te typen.
En voor wie op een telpost staat waar het snel gaat: zeg het, en kijk verder.

## Eerlijk

- Alleen in het Nederlands.
- Alleen voor Android, nog niet voor iPhone.
- Voor België en Nederland.
- Gratis, zonder reclame, zonder account.
- Je waarnemingen blijven op je telefoon, tot jij ze verstuurt.{% if site.fase == 'test' %}
  Zolang de app nog niet vrij in Google Play staat, gaat er wel een logboek
  naar de maker, zodat ze beter leert verstaan.{% endif %} Alles staat in het
  [privacybeleid]({{ '/privacy/' | relative_url }}).{% if site.fase == 'test' %}
- Nog volop in de maak: er komen geregeld nieuwe versies, en wat je
  laat weten, helpt mee.{% endif %}

## Wie het maakt

KLAPekster is een hobbyproject van Olivier Fuchs, mede-vogelaar. Je kunt met
de app (via je eigen account) je waarnemingen snel opladen. Toch is dit
initiatief op dit moment niet verbonden met Natuurpunt of de organisatie
achter waarnemingen.be, waarneming.nl of observation.org.

<div class="slotknop">{% include playknop.html %}</div>
