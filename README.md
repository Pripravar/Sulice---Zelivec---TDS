# II/603 Sulice – Želivec · TDS / objednatel

Zjednodušená mobilní webová mapa stavby pro **technický dozor stavebníka (TDS)** a **objednatele**.

Slouží pouze k orientaci na stavbě — kde se právě nacházíte a kterého stavebního objektu (SO) se to týká. Bez výkresů, technických zpráv, poznámek a fotek.

## Použití

Aplikace běží na GitHub Pages: **https://pripravar.github.io/Sulice---Zelivec---TDS/**

Otevři v telefonu (Chrome / Safari), povol GPS.

## Funkce

- 🗺️ Podkladové mapy: Mapy.cz (Outdoor / Basic / Letecká) + OSM
- 📍 GPS sledování + aktuální staničení (km) + aktuální SO v hlavičce
- 📏 Markery staničení po 100 m — kliknutím se zobrazí popup s km a příslušným SO
- 🏗️ Vrstva stavebních objektů SO 101 / 101.1 / 101.2 / 101.3 / 101.4 / 102 / 103 / 104 / 105 / 106 / 107 jako barevné úseky podél osy
- 🔵 Propustky P1 (km 2,405, SO 104) a P2 (km 3,071, SO 105) — jen body s popiskem
- 📜 Vyklápěcí legenda SO

## Co tu **není** (oproti plné verzi)

- ❌ PDF výkresy (situace, podélný profil, vzorové řezy, technická zpráva, dopravní značení)
- ❌ Sdílené poznámky s GPS pinem a kategoriemi
- ❌ Focení a sdílená galerie
- ❌ Firebase backend (žádné sdílení dat mezi uživateli)

Pokud TDS nebo objednatel potřebuje výkresy, použije plnou verzi: https://pripravar.github.io/Sulice---Zelivec/

## Struktura repa

```
index.html              ← celá aplikace (single-file HTML+JS, ~25 KB)
README.md
```

## Konfigurace (uvnitř `index.html`)

```js
var MAPY_API_KEY = 'n4vDG-...';   // mapy.cz API
var KM_START = 0.000;
var KM_END   = 4.605;
```

Pole `STAVEBNI_OBJEKTY`, `CALIB_POINTS` a `GPX_POINTS` jsou identická s plnou verzí — pokud se geometrie aktualizuje v jedné, ručně se přenese i sem.

## Deploy na GitHub Pages

1. Push do repa `Pripravar/Sulice---Zelivec---TDS` (větev `main`).
2. V Settings → Pages: Source = `Deploy from a branch`, Branch = `main` / root.
3. Stránka bude do 1–2 minut na `https://pripravar.github.io/Sulice---Zelivec---TDS/`.

## Kalibrace GPS ↔ km

Identická jako v plné verzi (8 kalibračních bodů). Pokud bude potřeba doladit, uprav pole `CALIB_POINTS` v `index.html`.
