---
layout: null
permalink: /app/
sitemap: false
---
{% comment %}
  Het vaste korte adres klapekster.be/app, voor de QR-code op kaartjes en
  affiches: het stuurt meteen door naar de app in de winkel van je
  telefoon, de App Store op een iPhone of iPad, anders Google Play. Zo
  blijft een gedrukte QR-code geldig, ook als het adres in een winkel ooit
  verandert (go-live-plan, stap G). Een iPad doet zich voor als Mac, maar
  heeft een aanraakscherm. Zonder script: Google Play, zoals vroeger.
{% endcomment %}
{% assign play = 'https://play.google.com/store/apps/details?id=' | append: site.play_id %}
<!doctype html>
<html lang="nl">
<head>
<meta charset="utf-8">
<title>KLAPekster</title>
<meta name="robots" content="noindex">
<meta name="viewport" content="width=device-width, initial-scale=1">
<script>
  (function () {
    var ua = navigator.userAgent || '';
    var apple = /iPhone|iPad|iPod/.test(ua)
      || (/Macintosh/.test(ua) && navigator.maxTouchPoints > 1);
    location.replace(apple ? '{{ site.appstore_url }}' : '{{ play }}');
  })();
</script>
<noscript><meta http-equiv="refresh" content="0; url={{ play }}"></noscript>
</head>
<body>
<p><a href="{{ site.appstore_url }}">KLAPekster in de App Store</a></p>
<p><a href="{{ play }}">KLAPekster in Google Play</a></p>
</body>
</html>
