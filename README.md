# SGN — Système de Gestion des Notes

SGN est un projet universitaire de compilation qui permet d'analyser des fichiers de notes rédigés dans un langage spécialement conçu pour organiser les résultats des étudiants des niveaux L1, L2 et L3.

Le projet met en pratique les principales étapes de la compilation. **Flex** assure l'analyse lexicale et **Bison** réalise l'analyse syntaxique. Des vérifications sémantiques contrôlent ensuite la cohérence des informations, notamment les matricules, les coefficients, les notes et les semestres. Les données analysées sont organisées dans un **arbre syntaxique abstrait (AST)**.

Le système calcule les moyennes semestrielles et annuelles, les rangs, les mentions et les décisions. Il fournit également des diagnostics lorsqu'un fichier contient des erreurs. Une interface graphique développée avec **Python et Tkinter** permet d'ouvrir et de modifier les fichiers `.sgn`, de lancer leur analyse, de consulter les résultats et d'exporter les données aux formats CSV et TXT.

## Technologies utilisées

- C, GCC
- Flex et Bison
- Python 3 et Tkinter
- JSON pour l'échange des résultats
- Make pour automatiser la compilation

## Organisation du projet

```text
sgn_project/
├── src/       # Analyseur lexical, syntaxique et AST
├── gui/       # Interface graphique et communication avec le compilateur
├── tests/     # Fichiers de test SGN
├── rapport/   # Documents du projet
└── README.md
```

## Installation et lancement

Sous Ubuntu ou Ubuntu via WSL, installer les outils nécessaires :

```bash
sudo apt update
sudo apt install build-essential flex bison make python3 python3-tk
```

Compiler le programme :

```bash
cd sgn_project/src
make clean
make
```

Lancer l'interface graphique :

```bash
cd ../gui
python3 app.py
```

## Exécuter un test

Depuis le dossier principal du projet :

```bash
./src/sgn_parser < tests/test_valide.sgn | python3 -m json.tool
```

Les fichiers du dossier `tests/` permettent également de vérifier le traitement des erreurs lexicales, syntaxiques et sémantiques, la récupération après une erreur ainsi que les calculs.

## Objectif pédagogique

Ce projet a pour objectif de mettre en application les notions de compilation, de conception d'un AST, de gestion des erreurs et d'intégration d'un programme C avec une interface Python.
