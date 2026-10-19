---
title: KLAPekster steunen
description: Help de kosten dragen om KLAPekster ook op iPhone te brengen. Wat het kost, hoeveel er al binnen is, en hoe je met een overschrijving steunt.
permalink: /steunen/
---

{% comment %}
  Stap 2 van ontwerp/iphone-en-steunen/PLAN.md in de app-repo. Alles wat
  verandert, staat in _config.yml: `rekening` en `begunstigde` (de
  overschrijving en de betaalcode), `steun_binnen` en `steun_doel` (het
  balkje). Zolang `rekening` leeg is, staat er "binnenkort" in plaats van
  het rekeningnummer en de code.
{% endcomment %}
{% assign steun_doel = site.steun_doel | default: 200 %}
{% assign steun_binnen = site.steun_binnen | default: 0 %}
{% assign steun_procent = steun_binnen | times: 100 | divided_by: steun_doel | at_most: 100 %}

<style>
  /* Alleen voor deze pagina: het balkje en het betaalblok. Kleuren uit
     assets/stijl.css. De site is alleen licht (zie daar), dus geen donkere
     versie. */
  .steunbalk {
    height: 14px;
    border-radius: 999px;
    background: var(--petrol-vlak);
    border: 1px solid var(--lijn);
    overflow: hidden;
    margin: 10px 0 6px;
  }
  .steunbalk span {
    display: block;
    height: 100%;
    background: var(--petrol-vol);
    border-radius: 999px;
  }
  .steunbedrag { font-weight: 600; margin: 0; }
  .steunbedrag strong { color: var(--petrol); }

  .betaalblok {
    display: grid;
    gap: 20px;
    align-items: start;
  }
  @media (min-width: 620px) {
    .betaalblok { grid-template-columns: minmax(0, 1fr) auto; }
  }
  .betaalgegevens { margin: 0; }
  .betaalgegevens dt {
    color: var(--grijs);
    font-size: 0.9rem;
    margin-top: 12px;
  }
  .betaalgegevens dt:first-child { margin-top: 0; }
  .betaalgegevens dd {
    margin: 2px 0 0;
    font-weight: 600;
  }
  .rekeningregel {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 6px 12px;
  }
  .rekeningnummer { letter-spacing: 0.02em; }
  .kopieerknop {
    font: inherit;
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--petrol);
    background: var(--kaart);
    border: 2px solid var(--petrol);
    border-radius: 999px;
    padding: 4px 14px;
    min-height: 36px;
    cursor: pointer;
  }
  .kopieerknop:hover { background: var(--petrol-vlak); }
  .kopieerknop:focus-visible {
    outline: 3px solid var(--petrol);
    outline-offset: 3px;
  }
  .betaalcode { margin: 0; text-align: center; }
  .betaalcode .code {
    width: 200px;
    height: 200px;
    margin: 0 auto;
    background: #FFFFFF;
    border: 1px solid var(--lijn);
    border-radius: 12px;
    padding: 6px;
  }
  .betaalcode svg { display: block; width: 100%; height: 100%; }
  .betaalcode path { shape-rendering: crispEdges; }
  .betaalcode figcaption {
    color: var(--grijs);
    font-size: 0.9rem;
    margin: 8px auto 0;
    max-width: 200px;
  }
</style>

# KLAPekster steunen

KLAPekster werkt nu alleen op Android. Om er ook een versie voor iPhone van te
maken, zijn er kosten, vooral bij Apple. Met een kleine gift help je die
dragen.

- De app blijft gratis en zonder reclame, ook voor wie niet steunt.
- Het is een gift aan een hobbyproject, geen aankoop. Je krijgt er geen
  fiscaal attest voor.

## Het doel: {{ steun_doel }} euro

Dat is wat Apple twee jaar lang vraagt, afgerond. Ik begin aan de versie voor
iPhone zodra twee dingen geregeld zijn: dat bedrag is binnen, en er is een
iPhone om op te testen, geleend of tweedehands gekocht.

<div class="kaart" markdown="0">
  <div class="steunbalk" role="progressbar" aria-label="Al binnen" aria-valuemin="0" aria-valuemax="{{ steun_doel }}" aria-valuenow="{{ steun_binnen }}">
    <span style="width: {{ steun_procent }}%"></span>
  </div>
  <p class="steunbedrag">Al binnen: <strong>{{ steun_binnen }}</strong> van {{ steun_doel }} euro</p>
</div>

Een overschrijving meldt zich niet vanzelf: ik werk dit bedrag met de hand
bij.

## Wat het kost

- **Apple: 99 euro per jaar.** Zoveel vraagt Apple om een app in de App Store
  te zetten.
- **Een iPhone om op te testen.** Dat kost niets als iemand er een uitleent
  ([zie hieronder](#een-iphone-uitlenen)). Anders koop ik een tweedehands
  toestel; wat dat kost, zet ik dan hier.
- **Bouwen zonder Mac.** Ik heb geen Mac. De versie voor iPhone laat ik online
  bouwen, bij Codemagic. Dat is gratis, zolang het binnen de maandelijkse
  gratis bouwtijd blijft. Kom ik daarboven, dan kost dat ongeveer één à twee
  euro per keer. Een nieuwe versie voor iPhone komt daarom minder vaak dan
  een nieuwe versie voor Android.

## Wat er met het geld gebeurt

Komt er meer binnen dan {{ steun_doel }} euro, en leent niemand me een
iPhone, dan gaat dat eerst naar een tweedehands iPhone om op te testen. Wat
daarna overblijft, gaat naar de kosten van Apple in de jaren erna.

## Zo steun je

{% if site.rekening and site.rekening != '' %}
Met een gewone overschrijving. Het bedrag kies je zelf.

<div class="kaart betaalblok" markdown="0">
  <dl class="betaalgegevens">
    <dt>Begunstigde</dt>
    <dd>{{ site.begunstigde | escape }}</dd>
    <dt>Rekeningnummer</dt>
    <dd class="rekeningregel">
      <span class="rekeningnummer" id="rekeningnummer">{{ site.rekening | escape }}</span>
      <button type="button" class="kopieerknop" id="kopieerknop">Kopieer</button>
    </dd>
    <dt>Mededeling</dt>
    <dd>Steun KLAPekster</dd>
  </dl>
  <figure class="betaalcode" id="betaalcode" hidden>
    <div class="code" id="betaalcodevak"></div>
    <figcaption>Of scan deze code met je bank-app. Het bedrag vul je zelf in.</figcaption>
  </figure>
</div>

<script src="{{ '/assets/js/qrcode-generator-1.4.4.js' | relative_url }}"></script>
<script>
  // De gegevens staan in _config.yml (rekening en begunstigde).
  var BEGUNSTIGDE = {{ site.begunstigde | jsonify }};
  var REKENING = {{ site.rekening | jsonify }};
  var MEDEDELING = 'Steun KLAPekster';

  // Het rekeningnummer zonder spaties: zo gaat het in de code en naar het
  // klembord.
  var iban = String(REKENING).replace(/\s+/g, '').toUpperCase();

  // De Europese betaalcode (EPC/SEPA): elke regel één gegeven, in deze
  // volgorde. Versie 002 mag zonder BIC; tekenset 1 is UTF-8. Geen bedrag:
  // dat vult de gever zelf in. Lege regels achteraan vallen weg.
  var betaalcode = [
    'BCD',                                    // vaste kop
    '002',                                    // versie
    '1',                                      // tekenset: UTF-8
    'SCT',                                    // overschrijving
    '',                                       // BIC: niet nodig
    String(BEGUNSTIGDE).trim().slice(0, 70),  // naam, hoogstens 70 tekens
    iban,                                     // rekeningnummer
    '',                                       // bedrag: kies je zelf
    '',                                       // doel
    '',                                       // gestructureerde mededeling
    MEDEDELING                                // vrije mededeling
  ].join('\n');

  try {
    // Zonder naam keurt een bank-app de code af: dan liever geen code.
    if (!String(BEGUNSTIGDE).trim()) throw new Error('geen begunstigde');
    qrcode.stringToBytes = qrcode.stringToBytesFuncs['UTF-8'];
    var qr = qrcode(0, 'M');
    qr.addData(betaalcode, 'Byte');
    qr.make();
    document.getElementById('betaalcodevak').innerHTML = qr.createSvgTag({
      cellSize: 1,
      margin: 4,
      scalable: true,
      title: 'Betaalcode voor een overschrijving aan ' + BEGUNSTIGDE
    });
    document.getElementById('betaalcode').hidden = false;
  } catch (e) {
    // Lukt de code niet, dan blijven de gegevens hierboven gewoon staan.
  }

  var kopieerknop = document.getElementById('kopieerknop');
  function gekopieerd() {
    kopieerknop.textContent = 'Gekopieerd';
    setTimeout(function () { kopieerknop.textContent = 'Kopieer'; }, 2000);
  }
  function kopieerOudeManier() {
    var vak = document.createElement('textarea');
    vak.value = iban;
    vak.setAttribute('readonly', '');
    vak.style.position = 'absolute';
    vak.style.left = '-10000px';
    document.body.appendChild(vak);
    vak.select();
    try { document.execCommand('copy'); gekopieerd(); } catch (e) {}
    document.body.removeChild(vak);
  }
  kopieerknop.addEventListener('click', function () {
    if (navigator.clipboard && window.isSecureContext) {
      navigator.clipboard.writeText(iban).then(gekopieerd, kopieerOudeManier);
    } else {
      kopieerOudeManier();
    }
  });
</script>
{% else %}
<div class="kaart" markdown="0">
  <p><strong>Binnenkort.</strong> Hier komt het rekeningnummer, met een code
  die je met je bank-app scant.</p>
</div>
{% endif %}

## Een iPhone uitlenen

Heb je een iPhone die niet al te oud is, en die je een tijd kan missen? Leen
hem me dan voor langere tijd uit, om de app op te testen. Laat het weten via
[Contact]({{ '/contact/' | relative_url }}).

<p class="flauw">Wil je eerst weten waarom KLAPekster nog niet op iPhone
werkt? Dat lees je op <a href="{{ '/iphone/' | relative_url }}">Komt
KLAPekster ook op iPhone?</a></p>
