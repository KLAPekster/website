---
permalink: /
---

<section class="opening">
  <h1 class="slogan">Zeg wat je ziet.<br>KLAPekster schrijft het op.</h1>
  <p class="inleiding">Een app voor vogelaars. Je spreekt je waarneming in,
  en KLAPekster maakt er een nette waarneming van voor waarnemingen.be of
  waarneming.nl.</p>
  {% include playknop.html %}
</section>

<picture class="hero">
  <source media="(max-width: 640px)" srcset="{{ '/assets/beeld/hero_dag_smal.webp' | relative_url }}">
  <img src="{{ '/assets/beeld/hero_dag_breed.webp' | relative_url }}" alt="Een klapekster op een paal in de heide" width="1600" height="430">
</picture>

## KLAPekster herkent geen vogels. Jij wel.

Zij verstaat jou. Je zegt wat je ziet of hoort, en de app maakt er een
waarneming van: soort, aantal, gedrag, plek en tijd. Ze luistert naar jou,
niet naar de vogels. Het determineren blijft jouw werk.

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

## Wat ze verstaat

<ul class="verstaat">
  <li>{% include pictogrammen/16-aantal.svg %}<span>Tot acht vogels in één zin.</span></li>
  <li>{% include pictogrammen/38-vliegend-noord.svg %}<span>Aantal, gedrag, leeftijd, geslacht en vliegrichting.</span></li>
  <li>{% include pictogrammen/15-leeftijdspaar.svg %}<span>Een koppel, of een ouder met jongen.</span></li>
  <li>{% include pictogrammen/08-jagend.svg %}<span>De prooi of de plant: “jagend op veldmuis”.</span></li>
  <li>{% include pictogrammen/27-onbekend.svg %}<span>Twijfel: “vink of keep”.</span></li>
  <li>{% include pictogrammen/29-gehoord-oor.svg %}<span>Honderden Vlaamse en Nederlandse namen, en namen die de spraakherkenning verkeerd verstaat.</span></li>
  <li>{% include pictogrammen/04-roepend.svg %}<span>Ze leest je waarneming hardop terug, zodat je naar de vogel kan blijven kijken.</span></li>
  <li>{% include pictogrammen/70-op-geluidsrecorder.svg %}<span>Bedienen met de volumeknop of de knop van je oortje.</span></li>
</ul>

## Echte zinnen

<div class="zinnen">
  <p class="zin">“Drie kieviten overvliegend west, twee wulpen ter plaatse en een grutto roepend.”</p>
  <p class="zin">“Twaalf wilde eenden waarvan acht mannetjes, en vier krakeenden.”</p>
  <p class="zin">“Torenvalk jagend op veldmuis.”</p>
  <p class="zin">“Koppel knobbelzwanen met vijf jongen.”</p>
  <p class="zin">“Vink of keep overvliegend zuid.”</p>
</div>

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
  Tijdens de testronde gaat er wel een logboek naar de maker, om de app beter
  te leren verstaan.{% endif %} Alles staat in het
  [privacybeleid]({{ '/privacy/' | relative_url }}).

## Wie het maakt

KLAPekster is een hobbyproject van Olivier Fuchs, vogelaar. De app is niet
verbonden met Natuurpunt, waarnemingen.be of waarneming.nl. De soortenlijst
komt van waarnemingen.be.

<div class="slotknop">{% include playknop.html %}</div>
