# 📚 Ontologie des données — Bachata Analyzer

Ce document décrit la structure des données utilisées et générées par l'application d'analyse musicale de bachata et salsa.

---

## 🧠 Données globales

### `df_instruments`

| Colonne          | Type   | Description                                           |
| ---------------- | ------ | ----------------------------------------------------- |
| instrument\_name | string | Nom de l’instrument (guïra, bongo, lead guitar, etc.) |
| instrument\_type | string | Type (percussion, string, voix...)                    |
| description      | string | Rôle ou caractéristiques sonores                      |

---

### `df_types_bachata`

| Colonne         | Type   | Description                                         |
| --------------- | ------ | --------------------------------------------------- |
| type\_id        | string | Identifiant unique du style                         |
| type\_name      | string | Nom du style (ex: Bachata Moderna)                  |
| characteristics | string | Traits typiques (tempo, instrumentation, structure) |

---

### `df_patterns_bachata_4` / `df_patterns_bachata_8`

| Colonne      | Type   | Description                                   |
| ------------ | ------ | --------------------------------------------- |
| pattern\_id  | string | Identifiant du pattern                        |
| instruments  | list   | Liste d'instruments impliqués                 |
| phrase\_name | string | Phrase musicale associée (derecho, climax...) |
| description  | string | Description textuelle du pattern              |

---

### `df_phrases`

| Colonne      | Type   | Description                              |
| ------------ | ------ | ---------------------------------------- |
| phrase\_id   | string | Identifiant unique de la phrase          |
| phrase\_name | string | Nom de la phrase (derecho, climax, etc.) |
| description  | string | Définition ou caractéristiques           |

---

## 🎵 Données par chanson

### `df_song_metadata`

| Colonne         | Type   | Description              |
| --------------- | ------ | ------------------------ |
| song\_id        | string | Identifiant unique       |
| song\_title     | string | Titre de la chanson      |
| artist          | string | Nom de l’artiste         |
| duration        | float  | Durée en secondes        |
| bpm             | float  | Tempo global estimé      |
| sections\_count | int    | Nombre total de sections |

---

### `df_section`

| Colonne         | Type   | Description                  |
| --------------- | ------ | ---------------------------- |
| section\_id     | string | Identifiant de section       |
| start\_time     | float  | Temps de début (en secondes) |
| end\_time       | float  | Temps de fin                 |
| section\_type   | string | intro, chorus, bridge, etc.  |
| tempo           | float  | BPM local                    |
| instrumentation | list   | Instruments actifs           |
| phrase          | string | Phrase musicale identifiée   |

---

### `df_audio_features`

| Colonne            | Type   | Description                      |
| ------------------ | ------ | -------------------------------- |
| section\_id        | string | Référence de section             |
| spectrogram        | array  | Fréquence x temps                |
| chromagram         | array  | 12 hauteurs chromatiques x temps |
| tempogram          | array  | Tempo x temps                    |
| amplitude\_profile | array  | Profil d’intensité sonore        |

---

### `df_instruments_section`

| Colonne     | Type   | Description                |
| ----------- | ------ | -------------------------- |
| section\_id | string | Section analysée           |
| instrument  | string | Instrument concerné        |
| presence    | float  | Score de présence relative |
| intensity   | float  | Intensité moyenne de jeu   |

---

### `df_patterns_detectes`

| Colonne       | Type   | Description                    |
| ------------- | ------ | ------------------------------ |
| section\_id   | string | Section concernée              |
| pattern\_id   | string | Pattern reconnu                |
| pattern\_type | string | "4 temps" ou "8 temps"         |
| match\_score  | float  | Score de correspondance \[0,1] |

---

### `df_structure_chanson`

| Colonne          | Type   | Description                    |
| ---------------- | ------ | ------------------------------ |
| segment\_id      | string | Identifiant de segment         |
| start\_time      | float  | Début du segment               |
| end\_time        | float  | Fin du segment                 |
| structure\_label | string | intro, chorus, breakdown, etc. |

---

### `df_prediction_type_bachata`

| Colonne         | Type   | Description                          |
| --------------- | ------ | ------------------------------------ |
| song\_id        | string | Identifiant de la chanson            |
| predicted\_type | string | Style prédit (moderne, fusion, etc.) |
| confidence      | float  | Confiance du modèle \[0,1]           |

---

## 🫀 Patterns par instrument (4 temps)

### `df_pattern_guira`

* Profil rythmique haute fréquence, répétitif.

### `df_pattern_bongo`

* Intensité dynamique, accents rythmiques ("martillo").

### `df_pattern_kick`

* Pulsation basse (temps forts), lié au tempo.

### `df_pattern_bass`

* Courbes sinusoïdales lentes, ligne de basse harmonique.

### `df_pattern_rythm_guitar`

* Accord répétitif, signature harmonique par section.

### `df_pattern_lead_guitar`

* Lignes mélodiques, motifs chromatiques.

### `df_pattern_voix`

* Profil chromatique et amplitude variable (paroles, chœurs).

---

## 📊 Dictionnaires de référence

**Phrases musicales courantes** : derecho, climax, breakdown, drop, silence

**Structures de chanson** : intro, outro, verse, chorus, bridge, pre-chorus, interlude, solo guitar, breakdown, mambo, rap

**Instruments analysés** : vocals, bongo, guïra, kick drum, bass guitar, rythm guitar, lead guitar

---

> Ce fichier est la base documentaire de l'ontologie musicale utilisée dans l'application. Il pourra être complété avec des exemples concrets et enrichi lors des analyses futures.
