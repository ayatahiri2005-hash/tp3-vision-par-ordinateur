# tp3-vision-par-ordinateur
# Floutage automatique des visages

Mini-projet du TP3 « Vision par ordinateur » (module Technologies IA, ENSA Fès, Pr. Youness IDRISSI KHAMLICHI).

## Objectif

Anonymiser une image en détectant automatiquement tous les visages qu'elle contient, puis en appliquant un flou gaussien sur chaque zone détectée. Ce traitement permet de respecter la vie privée des personnes (anonymisation, conformité aux règles de protection des données).

## Principe de fonctionnement

1. Lecture de l'image avec **OpenCV** (`cv2.imread`).
2. Conversion en niveaux de gris (`cv2.cvtColor`).
3. Détection des visages avec le détecteur frontal de **dlib** (`dlib.get_frontal_face_detector`).
4. Pour chaque visage détecté, extraction de la zone (région d'intérêt) et application de `cv2.GaussianBlur`.
5. Affichage et sauvegarde de l'image floutée.

## Technologies utilisées

- Python 3
- OpenCV (`opencv-python`)
- dlib (`dlib-bin` sous Windows)
- NumPy et Matplotlib

## Installation

```bash
pip install opencv-python numpy matplotlib
pip install dlib-bin
```

Sous Linux ou sur Google Colab :

```bash
apt-get install -y cmake libopenblas-dev liblapack-dev
pip install dlib
```

## Utilisation

1. Placer l'image à traiter dans le même dossier que le script (par exemple `people.jpg`).
2. Vérifier le nom du fichier dans la variable `nom_image` du code.
3. Lancer le script ou exécuter le notebook :

```bash
python floutage_visages.py
```

4. Le résultat s'affiche à l'écran et est enregistré dans `people_floute.jpg`.

Sur Google Colab, il faut d'abord uploader l'image :

```python
from google.colab import files
uploaded = files.upload()
```

## Paramètres modifiables

| Paramètre | Description |
|---|---|
| `nom_image` | Chemin de l'image à traiter |
| `(99, 99)` | Taille du noyau du flou (nombre impair). Plus il est grand, plus le flou est fort |
| `30` | Écart-type (sigma) du filtre gaussien |

## Limites

- Le détecteur de dlib (HOG) fonctionne surtout sur des visages de face et assez grands. Les visages de profil, très petits, ou partiellement cachés peuvent ne pas être détectés, donc rester non floutés.
- Les formats d'image non supportés par OpenCV (par exemple `.avif`) doivent être convertis en `.jpg` ou `.png`.

## Améliorations possibles

- Appliquer le floutage en temps réel sur la webcam ou sur une vidéo.
- Utiliser un détecteur plus robuste (CNN de dlib, YOLO) pour mieux détecter les visages de profil.
- Proposer un flou pixelisé comme alternative au flou gaussien.

## Auteur

AYA TAHIRI, 2eme année, Ingénierie Logicielle et Intelligence Artificielle (ILIA2), ENSA Fès.
