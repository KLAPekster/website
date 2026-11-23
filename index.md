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
  <p class="kernzin">Meer vogels kijken. Minder tikwerk.</p>
  <p class="inleiding">Spreek in wat je ziet, met aantallen en details. Meerdere
  soorten tegelijk? Ook goed. KLAPekster maakt er afzonderlijke waarnemingen van
  die je kunt versturen naar waarnemingen.be of waarneming.nl.</p>
  <p class="kenmerken">Gratis – voor Android en iPhone</p>
  {% comment %}
    Sinds november 2026 staat KLAPekster ook in de App Store. De knoppen
    voor beide winkels komen uit _includes/playknop.html: wie op een iPhone
    kijkt, krijgt de App Store vooraan. Tot dan stond hier een knop "iPhone?
    Zet me op de lijst" met een kaartje voor iPhone-bezoekers.
  {% endcomment %}
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

{% comment %}
  Wat vogelaars zeggen (_data/citaten.yml): meteen onder de opening, zodat
  je het ziet zonder te scrollen (Olivier, 11 oktober 2026). Eerst stond
  het onderaan, boven "Gemaakt door een vogelaar".
{% endcomment %}
<section class="citaten" aria-label="Wat vogelaars zeggen">
{% for c in site.data.citaten %}
  <figure class="citaat">
    <blockquote>{{ c.tekst }}</blockquote>
    <figcaption>{{ c.naam }}</figcaption>
  </figure>
{% endfor %}
</section>

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

{% comment %}
  Een stukje uit de app bij de tekst (Olivier, 19 oktober 2026, plan in de
  app-repo: ontwerp/website-schermbeelden/PLAN.md): geen heel scherm, alleen
  wat de tekst niet al zegt ("enkel de visuele ondersteuning"). Het komt uit
  de etalage, via tools/build_website_beeld.py. Op een telefoon onder de
  tekst, in het midden; op een breed scherm (kolom 1160, lopende tekst 720)
  ernaast, want eronder liet het rechts een grote lege vlakte en maakte het
  de pagina een scherm langer. De stijl staat hier, niet in
  assets/stijl.css.
{% endcomment %}
<style>
  .uitsnede {
    display: block;
    width: 100%;
    max-width: var(--maat);
    height: auto;
    margin: 24px auto 0;
    border-radius: 20px;
  }
  .uitsnede.knoppen { --maat: 320px; }
  .uitsnede.gedrag { --maat: 300px; border: 1px solid var(--lijn); }
  .uitsnede.reeks { --maat: 300px; border: 1px solid var(--lijn); }  @media (min-width: 1200px) {
    .naast {
      display: grid;
      grid-template-columns: minmax(0, 720px) auto;
      gap: 0 56px;
      align-items: start;
    }
    .naast .uitsnede { margin: 0; }
    .naast > div > :first-child { margin-top: 0; }
  }
</style>

## Zonder naar je scherm te kijken

<div class="naast" markdown="1">
<div markdown="1">

Je kunt KLAPekster bedienen met een knop. Op Android met de volumeknoppen,
de knop van een bedraad oortje of een losse Flic-knop. Op een iPhone met de
knop van je oortje, ook een draadloos, of met de actieknop of een tik op de
achterkant. Spreek je waarneming in en laat de app die hardop teruglezen. Met
een knopdruk bewaar je ze of begin je opnieuw.

Welke knop wat doet, stel je zelf in.

</div>
<div><img class="uitsnede knoppen" src="{{ '/assets/beeld/schermen/knoppen.webp' | relative_url }}" alt="De app leest je waarneming voor: IJsvogel, 1, Man, foeragerend. Met de volumeknop plus bewaar je, met min begin je opnieuw." width="352" height="285" loading="lazy"></div>
</div>

## Een hele reeks na elkaar

<div class="naast" markdown="1">
<div markdown="1">

Bij een watervogeltelling, op de telpost of om een notitieboekje over te
zetten: met Reeks inspreken blijft de microfoon open en zeg je je vogels
gewoon na elkaar. Elke vogel komt op een eigen regel. Iets vergeten? Zeg het
er meteen achteraan. Verkeerd? Zeg "fout". Wil je niet kijken, dan leest de
app elke vogel kort terug.

Spreek je achteraf in, bijvoorbeeld uit een notitieboekje, dan zet je
bovenaan één keer de dag, het uur en de plek vast, en zo nodig ook een
gedrag, zoals overvliegend. Elke vogel die je daarna inspreekt, krijgt ze
vanzelf.

</div>
<div><img class="uitsnede reeks" src="{{ '/assets/beeld/schermen/reeks.webp' | relative_url }}" alt="Reeks inspreken bij een watervogeltelling: 40 kolganzen, 12 wintertalingen, 3 kuifeenden en 2 tafeleenden, een regel die de app niet verstond, en een blauwe reiger, elk op een eigen regel" width="384" height="456" loading="lazy"></div>
</div>

## Meer dan soort en aantal

<div class="naast" markdown="1">
<div markdown="1">

KLAPekster kan tot acht waarnemingen uit één zin halen, elk met hun eigen
details. Je kunt onder meer inspreken:

- gedrag, leeftijd, geslacht, kleed, kleurvorm en vliegrichting;
- verschillende aantallen binnen een groep;
- een koppel of een ouder met jongen;
- wat een vogel eet of waarop hij jaagt;
- een geschat aantal of twijfel over soort en leeftijd;
- een hybride, zoals "kruising grauwe gans brandgans";
- de kilometer- of hectometerpaal waar je hem zag.

De app kent meer dan duizend vogelsoorten en bijna tweehonderd volks- en
dialectnamen. Ook veel verkeerd verstane vogelnamen kan KLAPekster alsnog
herkennen. Bij elke waarneming kun je een opmerking inspreken en tot drie
foto's toevoegen.

</div>
<div><img class="uitsnede gedrag" src="{{ '/assets/beeld/schermen/gedrag.webp' | relative_url }}" alt="Het gedrag aanpassen in de app: overvliegend is gekozen, met een windroos om de richting aan te tikken" width="384" height="452" loading="lazy"></div>
</div>

## Zeldzame vogels in je buurt

In Zeldzaam rondom jou zie je welke zeldzame vogels er de laatste week in je
buurt gemeld zijn op waarnemingen.be en waarneming.nl, en hoe je er komt.

<style>
  /* Vijf stappen bij Zeldzaam rondom jou: op een breed scherm drie bovenaan
     en twee in het midden eronder, elk even breed als de stappen van "Zo
     werkt het" (Olivier, 18 november 2026). */
  @media (min-width: 1200px) {
    .voorpagina .stappen.vijf { grid-template-columns: repeat(6, 1fr); }
    .voorpagina .stappen.vijf li { grid-column: span 2; }
    .voorpagina .stappen.vijf li:nth-child(4) { grid-column: 2 / span 2; }
  }
</style>

<ol class="stappen vijf">
  <li>
    <h3>Wat zit er in de buurt?</h3>
    <p>Zeldzame vogels op de kaart en in een lijst. Je ziet wanneer hij laatst
    gespot is, hoe groot de trefkans is, in welke gebieden hij zit en hoe ver
    weg die zijn.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/schermen/zeldzaam-lijst.webp' | relative_url }}" alt="Zeldzaam rondom jou als lijst, de dichtstbije eerst: een rotszwaluw in Kruibeke op 40 kilometer, een ruigpootbuizerd op de Plaat van Baarland en een grijze wouw in de Doelpolder, elk met de trefkans en wanneer hij laatst gezien is" width="384" height="768" loading="lazy">
  </li>
  <li>
    <h3>Zijn eigen pagina</h3>
    <p>Tik op een vogel voor zijn eigen pagina: de laatste berichten, de
    foto's en de geluidsopnames.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/schermen/zeldzaam-pagina.webp' | relative_url }}" alt="De pagina van een witkopgors in Zeebrugge, 89 kilometer verder: misschien nog, 146 waarnemers, vier dagen op rij, de laatste berichten, een keuze van duidelijke foto's en een knop om een opname te beluisteren" width="384" height="768" loading="lazy">
  </li>
  <li>
    <h3>Waar zit hij precies?</h3>
    <p>Op de grote kaart zie je waar hij het vaakst gemeld werd, met de
    kijkplekken en parkings erbij. Ter plaatse zie je ook
    jezelf, en in welke richting je kijkt.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/schermen/zeldzaam-kaart.webp' | relative_url }}" alt="De grote kaart bij Doel op satellietbeeld: een vlek van geel tot rood waar de vogel het vaakst gemeld werd, een kijkwand en parkings, en jij op de Oostlangeweg met een oranje bundel in je kijkrichting" width="384" height="768" loading="lazy">
  </li>
  <li>
    <h3>Hoe kom je er?</h3>
    <p>Verschillende manieren om er te geraken, met informatie over parkings,
    wandelroutes, toegankelijkheid, veerboten en omwegen. Zet het direct door
    naar een auto- of wandelroute in je favoriete app.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/schermen/zeldzaam-weg.webp' | relative_url }}" alt="Een vogel aan de Schelde bij Hoboken: met de auto tot bij de vogel, met de auto naar een parking op 150 meter, of te voet of met de fiets, ook met het veer Kruibeke-Hoboken" width="384" height="768" loading="lazy">
  </li>
  <li>
    <h3>Wanneer ga je best?</h3>
    <p>Hoeveel vogelaars hem de laatste dagen zagen, op welk uur hij het vaakst
    gemeld wordt, informatie over getijden, openingsuren, faciliteiten en
    andere relevante informatie over het gebied.</p>
    <img class="scherm stapbeeld" src="{{ '/assets/beeld/schermen/zeldzaam-3.webp' | relative_url }}" alt="Een graszanger in het Zwin: de waarnemers per dag, het getij met hoog- en laagwater, en de openingsuren van het Zwin Natuur Park" width="384" height="780" loading="lazy">
  </li>
</ol>

{% comment %}
  Waarnemingen en Jij uit versie 1.6.6 (Olivier, 23 november 2026, plan in
  de app-repo: ontwerp/website-schermbeelden/PLAN.md, ronde 4). Geen
  kaartjes met uitleg: alleen schermen met een naam eronder, "de
  screenshots spreken voor zich". Op een telefoon twee per rij, breed vier.
  Je gebieden en Een waarneming zijn schermafbeeldingen van Oliviers
  telefoon; de rest komt uit de app met de echte tekeningen en verzonnen
  gegevens. De stijl staat hier, niet in assets/stijl.css.
{% endcomment %}
<style>
  .galerij {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 20px 16px;
    margin: 1em 0;
  }
  .galerij figure { margin: 0; }
  .galerij img { display: block; width: 100%; height: auto; max-width: none; }
  .galerij figcaption {
    margin-top: 8px;
    font-family: var(--schreef);
    font-weight: 600;
    text-align: center;
  }
  .galerij figcaption span {
    display: block;
    font-family: inherit;
    font-weight: 400;
    font-size: 0.9rem;
    color: var(--grijs);
  }
  @media (min-width: 700px) {
    .galerij { grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 24px; }
  }
</style>

## Al je waarnemingen op een rij

Ook die van waarnemingen.be.

<div class="galerij">
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/waarnemingen-gebieden.webp' | relative_url }}" alt="Je gebieden: 8751 waarnemingen, 276 soorten en 353 gebieden, met bovenaan het gebied waar je nu bent" width="384" height="742" loading="lazy"><figcaption>Je gebieden</figcaption></figure>
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/waarnemingen-gebied.webp' | relative_url }}" alt="Een gebied: je bijzonderste waarneming er, de maanden waarin je er kwam en de soorten die je er zag" width="384" height="742" loading="lazy"><figcaption>Een gebied</figcaption></figure>
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/waarnemingen-soort.webp' | relative_url }}" alt="Een soort, de merel: wanneer en waar je hem eerst en laatst zag, per maand, en al je waarnemingen" width="384" height="742" loading="lazy"><figcaption>Een soort</figcaption></figure>
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/waarnemingen-waarneming.webp' | relative_url }}" alt="Een waarneming: drie strandleeuweriken in het Zwin, met een kaartje en een foto" width="384" height="742" loading="lazy"><figcaption>Een waarneming</figcaption></figure>
</div>

## Wat je zag, en wat je nog mist

<div class="galerij">
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/lijst-overzicht.webp' | relative_url }}" alt="Je overzicht: 243 soorten in je lijst, de grauwe franjepoot als laatste nieuwe, en je jaarlijst naast die van vorig jaar" width="384" height="742" loading="lazy"><figcaption>Je lijst</figcaption></figure>
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/lijst-veldgids.webp' | relative_url }}" alt="Je veldgids: je soorten per familie, met hun tekening en wanneer je ze eerst en laatst zag" width="384" height="742" loading="lazy"><figcaption>Je veldgids</figcaption></figure>
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/lijst-schaamsoorten.webp' | relative_url }}" alt="Schaamsoorten in vier trappen, van gewoon tot zeldzaam, elk met een balkje van hoeveel je er al zag" width="384" height="742" loading="lazy"><figcaption>Schaamsoorten<span>gewone vogels die je nog nooit zag</span></figcaption></figure>
  <figure><img class="scherm" src="{{ '/assets/beeld/schermen/lijst-nog-niet-dit-jaar.webp' | relative_url }}" alt="Nog niet dit jaar: kramsvogel, middelste bonte specht, tapuit, hop en boomvalk, met wanneer je ze vorige jaren meestal zag" width="384" height="742" loading="lazy"><figcaption>Nog niet dit jaar</figcaption></figure>
</div>

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
- Voor Android en iPhone.
- Voor België en Nederland.
- Gratis en zonder reclame.
- De eerste keer dat je verstuurt, meld je je één keer aan met je
  Google-account. Vanaf dan staat er een kopie van je waarnemingen veilig bij
  KLAPekster, zodat je niets kwijt bent, ook niet met een nieuwe telefoon.
- De app houdt een logboek bij van wat ze verstond, zodat ze beter leert
  verstaan. Dat kan je uitzetten. Alles staat in het
  [privacybeleid]({{ '/privacy/' | relative_url }}).{% if site.fase == 'test' %}
- KLAPekster is nog in ontwikkeling. Met je feedback help je de app
  verbeteren.{% endif %}

## Gemaakt door een vogelaar

{% comment %}
  De foto staat links van de tekst: Olivier kijkt naar rechts, naar de
  tekst toe, niet naar de rand van het scherm.
{% endcomment %}
<div class="maker">
  <img src="{{ '/assets/beeld/olivier.webp' | relative_url }}" alt="Olivier met zijn verrekijker in een droog grasland" width="400" height="400" loading="lazy">
  <p>KLAPekster is een hobbyproject van Olivier Fuchs, zelf vogelaar.</p>
</div>

<div class="slotknop">{% include playknop.html %}</div>
