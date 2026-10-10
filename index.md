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

<div class="held">
<section class="opening">
  <h1 class="slogan">Zeg wat je ziet.<br>KLAPekster schrijft het op.</h1>
  <p class="kernzin">Meer vogels kijken. Minder tijd aan invoeren.</p>
  <p class="inleiding">Spreek meerdere soorten in één keer in, met hun aantallen
  en details. KLAPekster maakt er afzonderlijke waarnemingen van.</p>
  <p class="kenmerken">Gratis, voor Android · Export naar waarnemingen.be en waarneming.nl</p>
  {% include playknop.html %}
</section>

<section class="toonbeeld" aria-label="Voorbeeld">
  <figure>
    <figcaption class="wie">Jij spreekt, KLAPekster luistert…</figcaption>
    <img class="scherm" src="{{ '/assets/beeld/luisterbeeld.webp' | relative_url }}" alt="De klapekster op zijn paal in de heide luistert. In zijn wolk staat: {{ eerste.zin }}" width="384" height="600">
  </figure>
  <figure>
    <figcaption class="wie">…en maakt er dit van:</figcaption>
    <img class="fiche" src="{{ '/assets/beeld/fiches/' | append: eerste.naam | append: '.webp' | relative_url }}" alt="Drie waarnemingen: drie kieviten overvliegend west, twee wulpen ter plaatse en een grutto roepend" width="{{ eerste.breedte }}" height="{{ eerste.hoogte }}">
  </figure>
</section>
</div>

## Voor wie

Voor vogelaars die liever spreken dan typen, of hun waarnemingen sneller
willen ingeven: aan de voederplaats, tijdens een wandeling of op de telpost.

## Zo werkt het

<ol class="stappen">
  <li>
    <h3>Spreek je waarneming in</h3>
    <p>Tik op de spreekknop en zeg wat je ziet of hoort. Bijvoorbeeld:
    <span class="zin-kort">“Drie koolmezen overvliegend noord.”</span></p>
    <p class="flauw">KLAPekster herkent jouw woorden, geen vogelgeluiden.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/stappen/stap-1.webp' | relative_url }}" alt="De klapekster luistert. In zijn wolk staat: drie koolmezen overvliegend noord" width="384" height="780" loading="lazy">
  </li>
  <li>
    <h3>Controleer en bewaar</h3>
    <p>Kijk na of alles klopt, pas zo nodig iets aan en bewaar. Plaats en tijd
    voegt de app automatisch toe.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/stappen/stap-2.webp' | relative_url }}" alt="De fiche: drie koolmezen, overvliegend noord, met de knoppen Bewaar en Opnieuw" width="384" height="780" loading="lazy">
  </li>
  <li>
    <h3>Stuur je waarnemingen door</h3>
    <p>Na je wandeling stuur je de bewaarde waarnemingen samen naar
    waarnemingen.be of waarneming.nl, via je eigen account.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/stappen/stap-3.webp' | relative_url }}" alt="Het scherm Versturen met zes waarnemingen van die ochtend, klaar om te versturen" width="384" height="780" loading="lazy">
  </li>
</ol>

## Zonder naar je scherm te kijken

Je kunt KLAPekster bedienen met de volumeknoppen, de knop van een bedraad
oortje of een losse Flic-knop. Spreek je waarneming in en laat de app die
hardop teruglezen. Met een knopdruk bewaar je ze of begin je opnieuw.

Welke knop wat doet, stel je zelf in. De app moet geopend blijven en het
scherm moet aanstaan. Het scherm dimt automatisch om het batterijverbruik te
beperken.

## Meer dan soort en aantal

KLAPekster kan tot acht waarnemingen uit één zin halen, elk met hun eigen
details. Je kunt onder meer inspreken:

- gedrag, leeftijd, geslacht, kleed, kleurvorm en vliegrichting;
- verschillende aantallen binnen een groep;
- een koppel of een ouder met jongen;
- wat een vogel eet of waarop hij jaagt;
- een geschat aantal of twijfel over soort en leeftijd.

De app kent bijna duizend vogelsoorten en bijna tweehonderd volks- en
dialectnamen. Ook veel verkeerd verstane vogelnamen kan KLAPekster alsnog
herkennen.

{% comment %}
  De voorbeelden komen ná de uitleg over het gebruik (Olivier, 9 oktober
  2026: elf voorbeelden duwden de uitleg bijna twee schermhoogtes naar
  beneden). Eerst zes, op een breed scherm twee rijen van drie; de rest klapt
  open achter een knop in het midden (Olivier, 10 oktober 2026: met drie en
  een knop links zag je die knop makkelijk over het hoofd). Welke: de
  volgorde in tools/website_fiches.dart in de app-repo. Openklappen zonder
  script, met details/summary.
{% endcomment %}
{% assign zichtbaar = 6 %}
{% assign verder = zichtbaar | plus: 1 %}
{% assign rest = site.data.voorbeelden.size | minus: verder %}

## Zeg het zoals je het ziet

<p class="flauw alleen-telefoon"><strong>Veeg opzij voor meer.</strong></p>

<div class="voorbeelden">
{% for v in site.data.voorbeelden offset:1 limit:zichtbaar %}{% include voorbeeld.html v=v %}{% endfor %}
</div>

<details class="meer-voorbeelden">
  <summary>Bekijk nog {{ rest }} voorbeelden</summary>
  <div class="voorbeelden">
  {% for v in site.data.voorbeelden offset:verder %}{% include voorbeeld.html v=v %}{% endfor %}
  </div>
</details>

## Goed om te weten

- Alleen in het Nederlands.
- Alleen voor Android, nog niet voor iPhone.
- Voor België en Nederland.
- Gratis, zonder reclame, zonder account.
- Je waarnemingen blijven op je telefoon, tot jij ze verstuurt.{% if site.fase == 'test' %}
  Zolang de app nog niet vrij in Google Play staat, gaat er wel een logboek
  naar de maker, zodat ze beter leert verstaan.{% endif %} Alles staat in het
  [privacybeleid]({{ '/privacy/' | relative_url }}).{% if site.fase == 'test' %}
- KLAPekster is nog in ontwikkeling. Met je feedback help je de app
  verbeteren.{% endif %}

## Gemaakt door een vogelaar

KLAPekster is een hobbyproject van Olivier Fuchs, zelf vogelaar.

<div class="slotknop">{% include playknop.html %}</div>
