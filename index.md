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
  <p class="inleiding">Een gratis Android-app voor vogelaars die liever blijven
  kijken dan typen. Spreek in wat je ziet of hoort: KLAPekster noteert de soort,
  het aantal en de details. Stuur je waarnemingen daarna door naar
  waarnemingen.be of waarneming.nl.</p>
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
</div>

## Jij kijkt en luistert. KLAPekster noteert.

KLAPekster herkent jouw woorden, geen vogelgeluiden. Vertel welke vogel je
ziet of hoort, hoeveel het er zijn en wat ze doen. De app zet je woorden om in
waarnemingen en voegt plaats en tijd toe. Twijfel je over de soort of de
leeftijd? Ook dat kun je inspreken.

## Voor wie

Van de mezen aan je voederplaats tot de ganzen boven de telpost: je wilt
vogels kijken, niet op je scherm turen. Met KLAPekster spreek je je
waarnemingen in terwijl je de vogels blijft volgen. Thuis, onderweg of midden
in de najaarstrek. Zeg wat je ziet of hoort, en kijk verder.

## Zo werkt het

<ol class="stappen">
  <li>
    <h3>Spreek je waarneming in</h3>
    <p>Tik op de spreekknop en zeg wat je ziet of hoort. Bijvoorbeeld:
    <span class="zin-kort">“Drie koolmezen overvliegend noord.”</span></p>
  </li>
  <li>
    <h3>Controleer en bewaar</h3>
    <p>KLAPekster zet je woorden om in een overzichtelijke waarneming. Kijk na
    of alles klopt, pas zo nodig iets aan en bewaar.</p>
  </li>
  <li>
    <h3>Stuur je waarnemingen door</h3>
    <p>Na je wandeling stuur je de bewaarde waarnemingen samen naar
    waarnemingen.be of waarneming.nl, via je eigen account.</p>
  </li>
</ol>

## Blijf kijken, ook tijdens het noteren

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
  De voorbeelden komen ná de uitleg over het gebruik, en eerst maar drie; de
  rest klapt open (Olivier, 9 oktober 2026: elf voorbeelden duwden de uitleg
  bijna twee schermhoogtes naar beneden). Welke drie: de volgorde in
  tools/website_fiches.dart in de app-repo. Openklappen zonder script, met
  details/summary.
{% endcomment %}
{% assign aantal = site.data.voorbeelden.size | minus: 1 %}

## Zeg het zoals je het ziet

<p class="flauw">Van een losse vogel tot meerdere soorten in één zin: zo verwerkt KLAPekster je woorden.<span class="alleen-telefoon"> Veeg opzij voor meer.</span></p>

<div class="voorbeelden">
{% for v in site.data.voorbeelden offset:1 limit:3 %}{% include voorbeeld.html v=v %}{% endfor %}
</div>

<details class="meer-voorbeelden">
  <summary>Bekijk alle {{ aantal }} voorbeelden</summary>
  <div class="voorbeelden">
  {% for v in site.data.voorbeelden offset:4 %}{% include voorbeeld.html v=v %}{% endfor %}
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
- Nog volop in de maak: er komen geregeld nieuwe versies, en wat je
  laat weten, helpt mee.{% endif %}

## Gemaakt door een vogelaar

KLAPekster is een hobbyproject van Olivier Fuchs, zelf vogelaar. Het idee is
eenvoudig: minder tijd besteden aan invoeren, meer aandacht voor wat er om je
heen gebeurt.

KLAPekster is een onafhankelijk initiatief en is niet verbonden aan
Natuurpunt of de organisatie achter waarnemingen.be, waarneming.nl en
observation.org.

<div class="slotknop">{% include playknop.html %}</div>
