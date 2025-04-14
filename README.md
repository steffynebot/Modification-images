# 🌸 Brain & Nature Palette Harmonization

Ce projet propose une harmonisation artistique d'une illustration de cerveau fleuri, en s'inspirant des couleurs dominantes d'un fichier SVG de style "blob" abstrait.

## 🎯 Objectif

Utiliser une palette de couleurs issue d’un fichier SVG (`blob-scene-haikei.svg`) pour recolorer une illustration complexe (`brain_flower.png`), et ainsi créer une cohérence visuelle entre deux univers graphiques.

## 📁 Fichiers

| Fichier | Description |
|--------|-------------|
| `blob-scene-haikei.svg` | SVG d’arrière-plan servant de référence pour la palette |
| `ChatGPT Image 10 avr. 2025, 22_08_01.png` | Image originale d’un cerveau fleuri |
| `brain_flower_recolored.png` | Image finale recolorée à l’aide de la palette extraite |
| `color_analysis_and_mapping.ipynb` | (optionnel) Notebook Python avec tout le code utilisé |
| `README.md` | Ce fichier de documentation |

## 🧪 Librairies utilisées

- `Pillow` (PIL) – pour manipuler les images
- `matplotlib` – pour visualiser les résultats
- `numpy` – pour le traitement des pixels
- `sklearn.cluster.KMeans` – pour extraire les couleurs dominantes
- `cairosvg` – pour convertir le SVG en image PNG analysable

## 🧠 Étapes du traitement

1. **Conversion SVG → PNG**
   - Le fichier SVG est converti en PNG à l’aide de `cairosvg`.

2. **Extraction des couleurs dominantes**
   - L’image PNG obtenue est réduite et analysée via K-Means clustering (5 couleurs principales).

3. **Analyse de l’image du cerveau fleuri**
   - Une autre analyse K-Means est appliquée à l’image originale pour identifier ses couleurs dominantes.

4. **Mapping des couleurs**
   - Les couleurs dominantes du cerveau sont mappées vers celles du SVG en respectant un certain seuil de tolérance (30).

5. **Recoloration**
   - Chaque pixel de l’image est recoloré si sa couleur correspond à une des couleurs dominantes d’origine.

## ✨ Résultat

L'image finale propose une fusion visuelle entre deux styles : anatomique et floral d'un côté, et abstrait/organique de l'autre.

<p align="center">
  <img src="brain_flower_recolored.png" alt="Cerveau fleuri recoloré" width="400"/>
</p>

## 📌 À venir

- Export sous forme de palette `.ase` (Adobe)
- Génération de plusieurs variantes
- Interface utilisateur pour le mapping manuel

## 💡 Auteur·rice

Projet conçu avec ChatGPT et un·e passionné·e de data science et d’art visuel 🧠🎨

---

**Licence :** MIT

