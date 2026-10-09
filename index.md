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
  <h1 class="slogan">Zeg wat je ziet.<br>Klapekster schrijft het op.</h1>
  <p class="inleiding">Een gratis Android-app voor vogelaars die liever blijven
  kijken dan typen. Spreek in wat je ziet of hoort: Klapekster noteert de soort,
  het aantal en de details. Later stuur je je waarnemingen door naar
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

## Jij kijkt en luistert. Klapekster noteert.

Klapekster herkent jouw woorden, geen vogelgeluiden. Vertel welke vogel je
ziet of hoort, hoeveel het er zijn en wat ze doen. De app zet je woorden om in
waarnemingen en voegt plaats en tijd toe. Twijfel je over de soort of de
leeftijd? Ook dat kun je inspreken.

## Zeg het zoals je het ziet

<p class="flauw">Van een losse vogel tot meerdere soorten in één zin: zo verwerkt Klapekster je woorden.<span class="alleen-telefoon"> Veeg opzij voor meer.</span></p>

<div class="voorbeelden">
{% for v in site.data.voorbeelden offset:1 %}
  <figure class="voorbeeld">
    <figcaption>
      <span class="opschrift">{{ v.opschrift }}</span>
      {% comment %}
        Bij de verhaspeling is de zin wat de spraakherkenning ervan maakte,
        niet wat de vogelaar zei. Wat hij wél zei, staat in
        tools/website_fiches.dart in de app-repo, en de fiche toont het.
      {% endcomment %}
      {% if v.naam == 'verhaspeling' %}<span class="verstaan">De spraakherkenning verstond:</span>{% endif %}
      <span class="voorbeeldzin">“{{ v.zin }}”</span>
      {% if v.naam == 'verhaspeling' %}<span class="verstaan">Je zei: “Buidelmees gehoord.”</span>{% endif %}
    </figcaption>
    <img src="{{ '/assets/beeld/fiches/' | append: v.naam | append: '.webp' | relative_url }}" alt="Wat KLAPekster maakt van: {{ v.zin }}" width="{{ v.breedte }}" height="{{ v.hoogte }}" loading="lazy">
  </figure>
{% endfor %}
</div>

## Zo werkt het

<ol class="stappen">
  <li>
    <h3>Spreek je waarneming in</h3>
    <p>Tik op de spreekknop en zeg wat je ziet of hoort. Bijvoorbeeld:
    <span class="zin-kort">“Drie koolmezen overvliegend noord.”</span></p>
  </li>
  <li>
    <h3>Controleer en bewaar</h3>
    <p>Klapekster zet je woorden om in een overzichtelijke waarneming. Kijk na
    of alles klopt, pas zo nodig iets aan en bewaar.</p>
  </li>
  <li>
    <h3>Stuur je waarnemingen door</h3>
    <p>Na je wandeling stuur je de bewaarde waarnemingen samen naar
    waarnemingen.be of waarneming.nl, via je eigen account.</p>
  </li>
</ol>

## Blijf kijken, ook tijdens het noteren

Je kunt Klapekster bedienen met de volumeknoppen, de knop van een bedraad
oortje of een losse Flic-knop. Spreek je waarneming in en laat de app die
hardop teruglezen. Met een knopdruk bewaar je ze of begin je opnieuw.

Welke knop wat doet, stel je zelf in. De app moet geopend blijven en het
scherm moet aanstaan. Het scherm dimt automatisch om het batterijverbruik te
beperken.

## Meer dan soort en aantal

Klapekster kan tot acht waarnemingen uit één zin halen, elk met hun eigen
details. Je kunt onder meer inspreken:

- gedrag, leeftijd, geslacht, kleed, kleurvorm en vliegrichting;
- verschillende aantallen binnen een groep;
- een koppel of een ouder met jongen;
- wat een vogel eet of waarop hij jaagt;
- een geschat aantal of twijfel over soort en leeftijd.

De app kent bijna duizend vogelsoorten en bijna tweehonderd volks- en
dialectnamen. Ook veel verkeerd verstane vogelnamen kan Klapekster alsnog
herkennen.

## Voor wie

Van de mezen aan je voederplaats tot de ganzen boven de telpost: je wilt
vogels kijken, niet op je scherm turen. Met KLAPekster spreek je je
waarnemingen in terwijl je de vogels blijft volgen. Thuis, onderweg of midden
in de najaarstrek. Zeg wat je ziet of hoort, en kijk verder.

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

Klapekster is een hobbyproject van Olivier Fuchs, zelf vogelaar. Het idee is
eenvoudig: minder tijd besteden aan invoeren, meer aandacht voor wat er om je
heen gebeurt.

Klapekster is een onafhankelijk initiatief en is niet verbonden aan
Natuurpunt of de organisatie achter waarnemingen.be, waarneming.nl en
observation.org.

<div class="slotknop">{% include playknop.html %}</div>
