# Bachata Analyzer

Une application Python d'analyse musicale pour la bachata (et la salsa), permettant de :

- Découper un morceau en sections de 4 temps
- Séparer les instruments automatiquement
- Identifier les patterns rythmiques et mélodiques (4 ou 8 temps)
- Déduire les phrases musicales et la structure de la chanson
- Classer le style de bachata (traditionnelle, moderne, urbaine…)
- Proposer des visualisations interactives pour musiciens, danseurs et chercheurs

## Fonctionnalités

- **Prétraitement audio** : découpage en sections selon le BPM
- **Séparation d'instruments** : via Spleeter, Demucs ou autres
- **Analyse audio** : extraction de spectrogrammes, chromagrammes, tempogrammes…
- **Détection de patterns** : reconnaissance de motifs rythmiques ou mélodiques
- **Phrases musicales** : classification en derecho, climax, etc.
- **Structure musicale** : détection des parties (intro, chorus…)
- **Typologie** : reconnaissance du type de bachata par machine learning

## Données produites

Chaque chanson génère plusieurs DataFrames :

- `df_section` : segments temporels analysés
- `df_audio_features` : spectres, chroma, rythme
- `df_instruments_section` : activité par instrument
- `df_patterns_detectes` : patterns identifiés
- `df_structure_chanson` : structure globale
- `df_prediction_type_bachata` : classification du style

## Base de connaissances

- `df_instruments` : instruments détectables
- `df_types_bachata` : typologie bachata
- `df_patterns_bachata_4` / `8` : motifs connus
- `df_phrases` : phrases musicales standardisées

## Exigences

- Python 3.9+
- Libs : `librosa`, `pandas`, `spleeter`, `essentia`, `matplotlib`, `scikit-learn`

## Lancer l’analyse

```bash
python analyze_song.py path/to/song.mp3
