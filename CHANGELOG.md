# Journal des modifications - Biathlon VMA

Journal démarré le 2026-11-22. Repères techniques : `versionCode` Android (APK) et `CACHE_NAME` du service worker (`service-worker.js`).

---

## 2026-11-22 (suite 2) - version 1.17 (APK versionCode 18, cache v11)

- APK reconstruite avec le correctif du nom de fichier CSV (suite précédente) : nom de fichier toujours avec l'heure, jamais la date seule.
- `versionCode` 17→18, `versionName` "1.16-tablette"→"1.17-tablette", numéro affiché (en-tête + pied de l'aide) 1.16→1.17.
- Signature vérifiée : même SHA-256 (`89c21b2b...`) que l'APK v1.16 - même clé.
- Guide PDF régénéré en version 1.17 (`generer-guide-biathlonvma.py`).
- Ancienne APK v1.16 sauvegardée dans `biathlonvma-backup/`.

---

## 2026-11-22 (suite) - nom de fichier CSV : date seule interdite (PWA seulement, version affichée 1.16 inchangée, cache v11)

- Fallback du nom de fichier CSV (quand `dateSeance` est vide) : `new Date().toISOString().slice(0,10)` (date seule) remplacé par `.slice(0,16).replace('T','_').replace(':','h')` (date + heure), dans `ajouterBoutonTelechargement()` et `afficherBlocSeanceCumulee()`. Deux exports le même jour auraient sinon écrasé le précédent (règle "jamais la date seule" du `CLAUDE.md` racine).
- Correctif déjà présent dans le dossier APK (`biathlonvma_apk_tablette 4`, commit local `30e5766`), jamais reporté ici jusqu'à ce jour.
- Aucune autre fonction modifiée, pas de nouvelle APK dans cette passe.

---

## 2026-11-22 - titre et description pour les moteurs de recherche (PWA seulement, version affichée 1.16 inchangée, cache v10)

- Balise `<title>` : « Biathlon VMA : écarts d'allure en VMA et lancers longs » (ancien titre « Biathlon VMA - 5ème »).
- `<meta name="description">` : « Biathlon VMA : évaluez l'allure, la régularité et les lancers de vos élèves sans multiplier les relevés papier. Gratuit et hors ligne. »
- Aucun changement de fonction, pas de nouvelle APK : le titre n'est pas visible dans le WebView.
