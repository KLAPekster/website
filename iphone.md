---
title: Komt KLAPekster ook op iPhone?
description: Waarom KLAPekster nog niet op iPhone werkt, en hoe je op de lijst komt om het te horen als dat verandert.
permalink: /iphone/
---

# Komt KLAPekster ook op iPhone?

Nog niet. KLAPekster werkt voorlopig alleen op Android-telefoons.

## Waarom nog niet

- Om een app in de App Store van Apple te zetten, betaal je Apple 99 euro per
  jaar.
- Om de app op een iPhone te testen, heb ik een iPhone nodig. Die heb ik niet.
- KLAPekster is een gratis hobbyproject, zonder reclame. Er komt dus niets
  binnen om die kosten mee te betalen.

Pas als dat geregeld is, kan ik aan een versie voor iPhone beginnen.

## Laat het me weten

Wil je het horen als KLAPekster op iPhone komt? Laat hieronder je naam en
e-mailadres achter, dan zet ik je op de lijst.

{% comment %}
  Dezelfde aanmelding als op Gebruiken (meedoen.md): type 'aanmelding' naar
  het Apps Script, tabblad Aanmeldingen, met toestel 'iPhone'. Zo krijgt ze
  de iPhone-mail (mailIphone) en nooit een uitnodiging voor Google Play. De
  vragen over ervaring en apps zijn er niet; die velden blijven leeg. Het
  vak "kenmerk" is het lokvak tegen robots, zoals op Gebruiken en Contact.
{% endcomment %}
<form id="iphoneformulier" class="formulier" novalidate markdown="0">
  <div class="veld">
    <label for="naam">Naam <span class="veldnoot">(verplicht)</span></label>
    <input type="text" id="naam" name="naam" required autocomplete="name">
  </div>

  <div class="veld">
    <label for="email">E-mailadres <span class="veldnoot">(verplicht)</span></label>
    <input type="email" id="email" name="email" required autocomplete="email" inputmode="email">
    <p class="hint">Hierheen laat ik het je weten. Je krijgt er meteen ook een
    bevestiging.</p>
  </div>

  <div class="veld">
    <fieldset>
      <legend>In welk land woon je? <span class="veldnoot">(verplicht)</span></legend>
      <label class="keuze"><input type="radio" name="land" value="België" required> België</label>
      <label class="keuze"><input type="radio" name="land" value="Nederland"> Nederland</label>
    </fieldset>
  </div>

  <div class="veld">
    <label for="opmerking">Opmerking of vraag <span class="veldnoot">(optioneel)</span></label>
    <textarea id="opmerking" name="opmerking" rows="3"></textarea>
  </div>

  <div class="lokvak" aria-hidden="true" style="position:absolute;left:-10000px;width:1px;height:1px;overflow:hidden">
    <label for="kenmerk">Laat dit leeg</label>
    <input type="text" id="kenmerk" name="kenmerk" tabindex="-1" autocomplete="off">
  </div>

  <p class="fout" id="foutmelding" role="alert" hidden></p>
  <button type="submit" class="knop" id="verstuurknop">Zet me op de lijst</button>
  <p class="hint">Wat er met je gegevens gebeurt, staat in het
  <a href="{{ '/privacy/' | relative_url }}">privacybeleid</a>.</p>
</form>

<div id="iphonebedankt" class="kaart" hidden>
  <h3>Bedankt!</h3>
  <p>Je staat op de lijst. Komt er een versie voor iPhone, dan laat ik het je
  weten. Je krijgt zo meteen een bevestigingsmail; niets ontvangen? Kijk even
  in je spam.</p>
  <p>Wil je helpen om het sneller mogelijk te maken? Hieronder lees je hoe.</p>
</div>

## Wil je helpen om het sneller mogelijk te maken?

{% comment %}
  De steunpagina (/steunen/, stap 2 van ontwerp/iphone-en-steunen/PLAN.md in
  de app-repo) verschijnt hier pas als de regel `rekening:` in _config.yml
  ingevuld is. Tot dan alleen het uitlenen.
{% endcomment %}
{% if site.rekening and site.rekening != '' %}
### Steunen

Met een kleine gift help je de kosten van Apple dragen.
[Zo kan je KLAPekster steunen]({{ '/steunen/' | relative_url }}).
{% endif %}

### Een iPhone uitlenen

Heb je een iPhone die niet al te oud is, en die je een tijd kan missen? Leen
hem me dan voor langere tijd uit, om de app op te testen. Laat het weten via
[Contact]({{ '/contact/' | relative_url }}).
{% if site.rekening and site.rekening != '' %}Dan gaat het geld alleen naar
de kosten van Apple, en niet naar een nieuwe iPhone voor mij.{% else %}Dan
hoeft er geen iPhone gekocht te worden, en blijven alleen de kosten van
Apple.{% endif %}

<script>
  // Het adres van het Apps Script staat in _config.yml (script_url).
  var SCRIPT_URL = '{{ site.script_url }}';

  var formulier = document.getElementById('iphoneformulier');
  var knop = document.getElementById('verstuurknop');
  var fout = document.getElementById('foutmelding');

  function gekozen(naam) {
    var el = formulier.querySelector('input[name="' + naam + '"]:checked');
    return el ? el.value : '';
  }

  function toonFout(tekst) {
    fout.textContent = tekst;
    fout.hidden = false;
  }

  function klaar() {
    formulier.hidden = true;
    document.getElementById('iphonebedankt').hidden = false;
  }

  formulier.addEventListener('submit', function (ev) {
    ev.preventDefault();
    fout.hidden = true;
    // Een robot: doen alsof het lukte, en niets versturen.
    if (document.getElementById('kenmerk').value) {
      klaar();
      return;
    }
    var naam = document.getElementById('naam').value.trim();
    var email = document.getElementById('email').value.trim();
    var land = gekozen('land');

    // Alleen noemen wat écht nog ontbreekt, en naar de eerste daarvan
    // springen, zoals op Gebruiken.
    var ontbreekt = [];
    var eerste = null;
    formulier.querySelectorAll('.ontbreekt').forEach(function (el) {
      el.classList.remove('ontbreekt');
    });
    function mist(tekst, veld, vraag) {
      ontbreekt.push(tekst);
      eerste = eerste || veld;
      vraag.classList.add('ontbreekt');
    }
    var naamveld = document.getElementById('naam');
    var emailveld = document.getElementById('email');
    var landveld = formulier.querySelector('input[name="land"]');
    if (!naam) mist('je naam', naamveld, formulier.querySelector('label[for="naam"]'));
    if (!email) mist('je e-mailadres', emailveld, formulier.querySelector('label[for="email"]'));
    if (!land) mist('in welk land je woont', landveld, landveld.closest('fieldset'));
    if (ontbreekt.length) {
      var lijst = ontbreekt.length === 1 ? ontbreekt[0]
        : ontbreekt.slice(0, -1).join(', ') + ' en ' + ontbreekt[ontbreekt.length - 1];
      toonFout('Vul nog in: ' + lijst + '.');
      eerste.scrollIntoView({ block: 'center', behavior: 'smooth' });
      eerste.focus({ preventScroll: true });
      return;
    }
    if (!emailveld.checkValidity()) {
      toonFout('Dat e-mailadres lijkt niet te kloppen.');
      emailveld.focus();
      return;
    }

    knop.disabled = true;
    knop.textContent = 'Bezig met versturen…';
    var payload = {
      type: 'aanmelding',
      naam: naam,
      email: email,
      toestel: 'iPhone',
      land: land,
      vogelervaring: '',
      stemherkenningErvaring: '',
      appsGebruikt: '',
      opmerking: document.getElementById('opmerking').value.trim(),
    };

    // Bewust géén eigen Content-Type en niet doorgaan naar het antwoord: zie
    // de uitleg op Gebruiken (meedoen.md).
    fetch(SCRIPT_URL, { method: 'POST', redirect: 'manual', body: JSON.stringify(payload) })
      .then(function (antwoord) {
        if (antwoord.type === 'opaqueredirect') return { ok: true };
        return antwoord.json();
      })
      .then(function (data) {
        if (!data.ok) throw new Error(data.error || 'onbekende fout');
        klaar();
      })
      .catch(function () {
        toonFout('Het versturen lukte niet. Probeer het zo meteen opnieuw, '
          + 'of mail naar {{ site.contact }}.');
        knop.disabled = false;
        knop.textContent = 'Zet me op de lijst';
      });
  });
</script>
