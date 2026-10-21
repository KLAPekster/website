---
layout: null
permalink: /app/
sitemap: false
---
{% comment %}
  Het vaste korte adres klapekster.be/app, voor de QR-code op kaartjes en
  affiches: het stuurt meteen door naar de app in Google Play. Zo blijft
  een gedrukte QR-code geldig, ook als het adres in Play ooit verandert
  (go-live-plan, stap G).
{% endcomment %}
{% assign winkel = 'https://play.google.com/store/apps/details?id=' | append: site.play_id %}
<!doctype html>
<html lang="nl">
<head>
<meta charset="utf-8">
<title>KLAPekster in Google Play</title>
<meta name="robots" content="noindex">
<meta http-equiv="refresh" content="0; url={{ winkel }}">
<link rel="canonical" href="{{ winkel }}">
<script>location.replace('{{ winkel }}');</script>
</head>
<body>
<p><a href="{{ winkel }}">KLAPekster in Google Play</a></p>
</body>
</html>
