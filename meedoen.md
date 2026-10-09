---
title: KLAPekster proberen
description: Meld je aan om KLAPekster nu al te proberen op je Android-telefoon.
permalink: /meedoen/
---

# KLAPekster proberen

{% if site.fase == 'winkel' %}
KLAPekster staat in Google Play. Wil je nieuwe versies eerder dan iedereen,
meld je dan hieronder aan.
{% else %}
KLAPekster staat nog niet vrij in Google Play, maar je kan haar nu al
proberen. Meld je hieronder aan, dan zet ik je op de lijst.
{% endif %}

## Hoe het gaat

- Je gebruikt de app gewoon, thuis of in het veld, voor je echte waarnemingen.
- Werkt iets niet zoals je verwacht, of kent ze een naam niet? Laat het gerust
  weten: wat je meldt, helpt mee.
- Je hebt een Android-telefoon nodig, en je spreekt Nederlands. De app is er
  voor België en Nederland.
- Zolang de app niet vrij in Google Play staat, stuurt ze een logboek mee,
  zodat ze beter leert verstaan. Wat daarin staat, lees je in het
  [privacybeleid]({{ '/privacy/' | relative_url }}).

## Aanmelden

<form id="aanmeldformulier" class="formulier" novalidate markdown="0">
  <label for="naam">Naam <span class="veldnoot">(verplicht)</span></label>
  <input type="text" id="naam" name="naam" required autocomplete="name">

  <label for="email">E-mailadres van je Google-account <span class="veldnoot">(verplicht)</span></label>
  <input type="email" id="email" name="email" required autocomplete="email" inputmode="email">
  <p class="hint">Het adres waarmee je op je telefoon in de Play Store zit.
  Dat hoeft geen Gmail-adres te zijn. Hiermee zet ik je op de lijst, en
  hierheen gaat ook de bevestiging.</p>

  <fieldset>
    <legend>Welke telefoon heb je? <span class="veldnoot">(verplicht)</span></legend>
    <label class="keuze"><input type="radio" name="toestel" value="Android" required> Android</label>
    <label class="keuze"><input type="radio" name="toestel" value="iPhone"> iPhone</label>
  </fieldset>
  <p class="hint melding" id="iphonemelding" hidden>KLAPekster werkt voorlopig
  alleen op Android. Meld je gerust aan: komt er een versie voor iPhone, dan
  laat ik het je weten.</p>

  <fieldset>
    <legend>In welk land woon je? <span class="veldnoot">(verplicht)</span></legend>
    <label class="keuze"><input type="radio" name="land" value="België" required> België</label>
    <label class="keuze"><input type="radio" name="land" value="Nederland"> Nederland</label>
  </fieldset>

  <label for="vogelervaring">Hoe zou je je ervaring met vogels omschrijven? <span class="veldnoot">(optioneel)</span></label>
  <select id="vogelervaring" name="vogelervaring">
    <option value=""></option>
    <option>Beginnend</option>
    <option>Regelmatig bezig met vogels</option>
    <option>Ervaren vogelaar</option>
    <option>Zeer ervaren of professioneel actief</option>
  </select>

  <label for="stemherkenningErvaring">Heb je ooit waarnemingen ingesproken met spraakherkenning? <span class="veldnoot">(optioneel)</span></label>
  <select id="stemherkenningErvaring" name="stemherkenningErvaring">
    <option value=""></option>
    <option>Nog nooit geprobeerd</option>
    <option>Weleens geprobeerd</option>
    <option>Gebruik ik regelmatig</option>
  </select>

  <fieldset>
    <legend>Welke apps gebruik je bij het vogels kijken? <span class="veldnoot">(meerdere mogelijk, optioneel)</span></legend>
    <div class="vinkjes">
      <label class="keuze"><input type="checkbox" name="apps" value="Waarnemingen.be"> Waarnemingen.be</label>
      <label class="keuze"><input type="checkbox" name="apps" value="Waarneming.nl"> Waarneming.nl</label>
      <label class="keuze"><input type="checkbox" name="apps" value="ObsMapp"> ObsMapp</label>
      <label class="keuze"><input type="checkbox" name="apps" value="ObsIdentify"> ObsIdentify</label>
      <label class="keuze"><input type="checkbox" name="apps" value="Merlin"> Merlin</label>
      <label class="keuze"><input type="checkbox" name="apps" value="BirdTrack"> BirdTrack</label>
      <label class="keuze"><input type="checkbox" name="apps" value="eBird"> eBird</label>
      <label class="keuze"><input type="checkbox" name="apps" value="Geen"> Geen</label>
      <label class="keuze"><input type="checkbox" name="apps" value="Andere"> Andere</label>
    </div>
  </fieldset>

  <label for="opmerking">Opmerking of vraag <span class="veldnoot">(optioneel)</span></label>
  <textarea id="opmerking" name="opmerking" rows="3"></textarea>

  <p class="fout" id="foutmelding" role="alert" hidden></p>
  <button type="submit" class="knop" id="verstuurknop">Aanmelden</button>
  <p class="hint">Wat er met je gegevens gebeurt, staat in het
  <a href="{{ '/privacy/' | relative_url }}">privacybeleid</a>.</p>
</form>

<div id="iphonebedankt" class="kaart" hidden>
  <h3>Bedankt!</h3>
  <p>Je aanmelding is binnen. KLAPekster werkt voorlopig alleen op Android;
  komt er een versie voor iPhone, dan laat ik het je weten.</p>
</div>

## Zo zet je de app op je telefoon

{% include installatiestappen.html %}

<script>
  // Het adres van het Apps Script staat in _config.yml (script_url).
  var SCRIPT_URL = '{{ site.script_url }}';
  var BEDANKT = '{{ "/bedankt/" | relative_url }}';

  var formulier = document.getElementById('aanmeldformulier');
  var knop = document.getElementById('verstuurknop');
  var fout = document.getElementById('foutmelding');

  function gekozen(naam) {
    var el = formulier.querySelector('input[name="' + naam + '"]:checked');
    return el ? el.value : '';
  }

  formulier.querySelectorAll('input[name="toestel"]').forEach(function (el) {
    el.addEventListener('change', function () {
      document.getElementById('iphonemelding').hidden = gekozen('toestel') !== 'iPhone';
    });
  });

  function toonFout(tekst) {
    fout.textContent = tekst;
    fout.hidden = false;
  }

  formulier.addEventListener('submit', function (ev) {
    ev.preventDefault();
    fout.hidden = true;
    var naam = document.getElementById('naam').value.trim();
    var email = document.getElementById('email').value.trim();
    var toestel = gekozen('toestel');
    var land = gekozen('land');
    if (!naam || !email || !toestel || !land) {
      toonFout('Vul je naam, je e-mailadres, je telefoon en je land in.');
      return;
    }
    if (!document.getElementById('email').checkValidity()) {
      toonFout('Dat e-mailadres lijkt niet te kloppen.');
      return;
    }

    knop.disabled = true;
    knop.textContent = 'Bezig met versturen…';
    var payload = {
      type: 'aanmelding',
      naam: naam,
      email: email,
      toestel: toestel,
      land: land,
      vogelervaring: document.getElementById('vogelervaring').value,
      stemherkenningErvaring: document.getElementById('stemherkenningErvaring').value,
      appsGebruikt: Array.prototype.map.call(
        formulier.querySelectorAll('input[name="apps"]:checked'),
        function (el) { return el.value; }).join(', '),
      opmerking: document.getElementById('opmerking').value.trim(),
    };

    // Bewust géén eigen Content-Type: de browser zet dan zelf "text/plain",
    // een "simpel" verzoek zonder voorafgaande controle (preflight). Apps
    // Script beantwoordt zo'n controle niet, en met "application/json" zou
    // het versturen stil mislukken.
    fetch(SCRIPT_URL, { method: 'POST', body: JSON.stringify(payload) })
      .then(function (antwoord) { return antwoord.json(); })
      .then(function (data) {
        if (!data.ok) throw new Error(data.error || 'onbekende fout');
        if (toestel === 'iPhone') {
          formulier.hidden = true;
          document.getElementById('iphonebedankt').hidden = false;
        } else {
          window.location.href = BEDANKT;
        }
      })
      .catch(function () {
        toonFout('Het versturen lukte niet. Probeer het zo meteen opnieuw, '
          + 'of mail naar {{ site.contact }}.');
        knop.disabled = false;
        knop.textContent = 'Aanmelden';
      });
  });
</script>
