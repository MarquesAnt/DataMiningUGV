PROJET DATAMINING UGV
Détection automatique de pièces usinées – Clustering non supervisé
1. Objectif du projet

L’objectif de ce projet est d’identifier automatiquement le nombre de pièces usinées ainsi que les phases actives de coupe sur une machine-outil 5 axes, à partir de données industrielles collectées toutes les 0,1 secondes.

Ce travail s’inscrit dans une démarche de Data Mining appliqué à l’usinage grande vitesse (HSM), avec pour finalité d’évaluer la productivité et de caractériser les cycles d’usinage grâce à des techniques d’apprentissage non supervisé.

2. Contexte et jeu de données

Les données proviennent d’un système de mesure EmmaTools installé sur une machine-outil Five Machining, utilisée dans l’industrie aéronautique pour la fabrication de pièces en alliage d’aluminium.

Elles contiennent :

72 variables mesurées toutes les 0,1 secondes,

sur une journée complète de production,

comprenant plusieurs programmes d’usinage (ProgP).

L’objectif principal est de segmenter ces signaux afin de détecter automatiquement le nombre de pièces produites et d’estimer les phases d’usinage effectif.

3. Approche méthodologique
3.1 Clustering non supervisé

Le projet repose sur des techniques de clustering non supervisé afin d’identifier des structures naturelles dans les données :

K-Means : approche basée sur la distance euclidienne, avec ajustement du nombre de clusters par la méthode du coude (Elbow Method).

GMM (Gaussian Mixture Model) : approche statistique probabiliste utilisant la maximisation de vraisemblance et le critère BIC pour déterminer le nombre optimal de clusters.

Ces modèles ont été comparés sur différents sous-ensembles correspondant à des programmes d’usinage spécifiques (ProgP = 32, ProgP = 35, etc.).

3.2 Variables utilisées

Positions et vitesses des axes (X, Y, Z)

Paramètres machine tels que la puissance ou la vitesse de broche

Indicateurs temporels pour suivre les transitions de cycles

4. Résultats principaux
Méthode	Nombre de clusters optimal	Interprétation
K-Means	3 à 4	Représente les cycles successifs d’usinage de pièces
GMM	3 à 4	Confirme les segments détectés, avec une meilleure flexibilité sur la forme des clusters

Les clusters obtenus correspondent aux phases de production successives observées sur la machine.

La segmentation temporelle permet de distinguer clairement les périodes d’usinage actif des temps morts (changement d’outil, repositionnement, etc.).

Ces résultats ouvrent la voie à la détection automatique d’incidents de production ou d’anomalies de coupe.

5. Calcul de la productivité (OEE)

L’OEE (Overall Equipment Efficiency) est estimé à partir de la durée totale des phases de coupe identifiées par clustering.

> **Formule :**  
> OEE = (Temps d’usinage effectif) / (Temps total de production)

Cette mesure, obtenue sans supervision, illustre la possibilité d’un monitoring intelligent de la performance machine à partir des seules données capteurs.

6. Stack technique
Technologie	Utilisation
Python	Traitement et modélisation
scikit-learn	Clustering (K-Means, GMM)
matplotlib / seaborn	Visualisation des clusters et des transitions
NumPy / pandas	Manipulation des données temporelles
BIC / Elbow Method	Sélection du nombre optimal de clusters
7. Résumé et perspectives

Ce projet illustre l’application de l’apprentissage non supervisé à un contexte industriel réel.
Les résultats démontrent la capacité des approches de clustering à :

détecter automatiquement les cycles de production,

estimer la productivité,

et fournir une base pour la surveillance prédictive de l’atelier.

Des perspectives d’amélioration incluent :

l’intégration de méthodes plus robustes (DBSCAN, Spectral Clustering),

la réduction de dimension (PCA),

et la mise en place d’une pipeline MLOps pour un suivi en temps réel.

