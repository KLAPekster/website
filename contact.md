---
title: Contact
description: Stuur de maker van KLAPekster een bericht.
permalink: /contact/
---

# Contact

Een vraag, een idee, of iets dat niet werkt? Laat het gerust weten.

{% comment %}
  Hetzelfde als "Contact" in de app: het bericht gaat naar het Apps Script
  (type 'bericht', tabblad "Berichten"), dat het doormailt naar
  {{ site.contact }}. In de kolom 'versie' staat dan "website".
  Het vak "kenmerk" (class .lokvak) is onzichtbaar voor mensen; wie het
  invult is een robot, en dan wordt er niets verstuurd. Bewust geen naam
  die een browser herkent en zelf invult (zoals "website").
{% endcomment %}
<form id="contactformulier" class="formulier" novalidate markdown="0">
  <div class="veld">
    <label for="naam">Naam <span class="veldnoot">(optioneel)</span></label>
    <input type="text" id="naam" name="naam" autocomplete="name">
  </div>

  <div class="veld">
    <label for="adres">E-mailadres <span class="veldnoot">(optioneel)</span></label>
    <input type="email" id="adres" name="adres" autocomplete="email" inputmode="email">
    <p class="hint">Alleen als je een antwoord wilt.</p>
  </div>

  <div class="veld">
    <label for="bericht">Bericht</label>
    <textarea id="bericht" name="bericht" rows="6" required></textarea>
  </div>

  <div class="lokvak" aria-hidden="true">
    <label for="kenmerk">Laat dit leeg</label>
    <input type="text" id="kenmerk" name="kenmerk" tabindex="-1" autocomplete="off">
  </div>

  <p class="fout" id="foutmelding" role="alert" hidden></p>
  <button type="submit" class="knop" id="verstuurknop">Versturen</button>
  <p class="hint">Wat er met je bericht gebeurt, staat in het
  <a href="{{ '/privacy/' | relative_url }}">privacybeleid</a>.</p>
</form>

<div id="verstuurd" class="kaart" hidden>
  <h3>Bedankt, je bericht is binnen.</h3>
  <p>Gaf je een mailadres, dan antwoord ik zo snel ik kan.</p>
</div>

<p class="flauw">Liever mailen, of een schermafbeelding meesturen? Dat kan
naar <a href="mailto:{{ site.contact }}">{{ site.contact }}</a>.</p>

<script>
  // Het adres van het Apps Script staat in _config.yml (script_url).
  var SCRIPT_URL = '{{ site.script_url }}';

  var formulier = document.getElementById('contactformulier');
  var knop = document.getElementById('verstuurknop');
  var fout = document.getElementById('foutmelding');

  function toonFout(tekst) {
    fout.textContent = tekst;
    fout.hidden = false;
  }

  function klaar() {
    formulier.hidden = true;
    document.getElementById('verstuurd').hidden = false;
  }

  // Zoals de app het doet: plaatselijke tijd, "2026-10-10T14:05".
  function nu() {
    var d = new Date();
    function twee(n) { return (n < 10 ? '0' : '') + n; }
    return d.getFullYear() + '-' + twee(d.getMonth() + 1) + '-' + twee(d.getDate())
      + 'T' + twee(d.getHours()) + ':' + twee(d.getMinutes());
  }

  formulier.addEventListener('submit', function (ev) {
    ev.preventDefault();
    fout.hidden = true;
    var bericht = document.getElementById('bericht').value.trim();
    var adres = document.getElementById('adres').value.trim();

    // Een robot: doen alsof het lukte, en niets versturen.
    if (document.getElementById('kenmerk').value) {
      klaar();
      return;
    }
    if (!bericht) {
      toonFout('Je bericht is nog leeg.');
      document.getElementById('bericht').focus();
      return;
    }
    if (adres && !document.getElementById('adres').checkValidity()) {
      toonFout('Dat e-mailadres lijkt niet te kloppen.');
      document.getElementById('adres').focus();
      return;
    }

    knop.disabled = true;
    knop.textContent = 'Bezig met versturen…';
    var payload = {
      type: 'bericht',
      tijd: nu(),
      naam: document.getElementById('naam').value.trim(),
      adres: adres,
      bericht: bericht,
      versie: 'website',
      toestel: '',
    };

    // Bewust géén eigen Content-Type: zie de uitleg op Proberen (meedoen.md).
    fetch(SCRIPT_URL, { method: 'POST', body: JSON.stringify(payload) })
      .then(function (antwoord) { return antwoord.json(); })
      .then(function (data) {
        if (!data.ok) throw new Error(data.error || 'onbekende fout');
        klaar();
      })
      .catch(function () {
        toonFout('Het versturen lukte niet. Probeer het zo meteen opnieuw, '
          + 'of mail naar {{ site.contact }}.');
        knop.disabled = false;
        knop.textContent = 'Versturen';
      });
  });
</script>
