# Benchmarks pratiques des performances quantiques sur IBM Sherbrooke

_Auteur : Luther Tendano, Polytechnique Montréal_

---

Ce dépôt accompagne un projet de recherche visant à **évaluer les performances pratiques du processeur quantique IBM Sherbrooke** à travers l’exécution de benchmarks algorithmiques concrets : la **Transformée de Fourier Quantique (QFT)** et l’**algorithme de Grover**.

## Objectifs du projet

- **Comparer la performance réelle du matériel quantique IBM Sherbrooke** à celle d’un simulateur idéal (Qiskit Aer).
- **Mesurer l’influence de la taille, de la profondeur des circuits et des niveaux d’optimisation** sur la fidélité des résultats.
- **Identifier les limites actuelles des processeurs quantiques NISQ** pour l’exécution d’algorithmes représentatifs.

## Structure du dépôt

- `QFT.ipynb` : Benchmarks et analyses pour la Transformée de Fourier Quantique (QFT).
- `Grover's_Search.ipynb` : Benchmarks et analyses pour l’algorithme de recherche de Grover.
- `Hamiltonien.ipynb` : (Si inclus) Simulation de circuits Hamiltoniens pour évaluation complémentaire.
- `README.md` : Ce fichier, présentant le contexte et les résultats clés du projet.

## Résumé méthodologique

- **Systèmes testés** :  
    - Simulateur classique Qiskit Aer (référence idéale sans bruit)
    - Processeur quantique IBM Sherbrooke (127 qubits, architecture Eagle R3)

- **Protocole expérimental** :  
    - Génération automatique de circuits pour chaque algorithme, avec variation du nombre de qubits (2 à 8).
    - Transpilation avec différents niveaux d’optimisation (Qiskit, `optimization_level` 1 à 3).
    - Exécution multiple (1024 shots) sur simulateur et matériel réel.
    - Collecte des métriques : profondeur algorithmique, profondeur normalisée, temps d’exécution, fidélité (distance de Hellinger).

- **Analyses** :  
    - Comparaison directe entre simulateur et processeur réel.
    - Impact de la profondeur, du type de circuit, et du niveau d’optimisation sur la fidélité.
    - Positionnement volumétrique selon le Quantum Volume.

## Principaux résultats

- **Fidélité décroissante avec la profondeur** : sur IBM Sherbrooke, la fidélité chute rapidement dès que la profondeur normalisée dépasse 20 à 60 couches.
- **Rôle de l’optimisation** : Le niveau 2 de transpilation permet d’atteindre une meilleure fidélité sur de petits circuits (≤3 qubits), mais l’optimisation plus agressive (niveau 3) peut dégrader la performance.
- **Limites du Quantum Volume** : Cette métrique surestime souvent les performances pour des circuits profonds et structurés ; une analyse volumétrique détaillée est préférable.
- **Latence et file d’attente** : Le temps effectif d’exécution quantique représente <1 % du temps total en cloud, le reste étant dominé par la latence de soumission.

## Reproduire les résultats

1. **Prérequis**
   - Python 3.8+
   - Qiskit (`pip install qiskit`)
   - Accès à IBM Quantum Experience pour l’exécution sur Sherbrooke (ou autre backend réel)

2. **Ouvrir les notebooks**
   - Avec Jupyter Lab/Notebook, VSCode, ou Google Colab.
   - Suivre les cellules pour reproduire la génération, la transpilation et l’exécution des circuits.

3. **Adapter les credentials** (si besoin)  
   - Pour l’exécution sur un backend IBM réel, renseigner son `IBM Quantum account` dans le notebook.

## Références clés

- T. Lubinski et al., _Application-oriented performance benchmarks for quantum computing_, arXiv:2110.03137, 2022.
- IBM Quantum [Quantum Volume](https://research.ibm.com/blog/quantum-volume-64)
- Documentation Qiskit : https://qiskit.org/documentation/

## Pour aller plus loin

- Les circuits exécutés sont disponibles dans les notebooks et en annexe du rapport PDF.
- Possibilités d’étendre l’étude à d’autres benchmarks (Hamiltonien, circuits aléatoires) et backends (ion trap, photonique).

---

<div align="center">

[![Licence](https://img.shields.io/badge/Licence-MIT-blue.svg)](LICENSE)  
[![Qiskit](https://img.shields.io/badge/Qiskit-Enabled-blueviolet?logo=Qiskit)](https://qiskit.org/)  
[![IBM Quantum](https://img.shields.io/badge/Backend-IBM_Sherbrooke-lightgrey?logo=IBM)](https://quantum-computing.ibm.com/)  

</div>
