# Analyse-Dynamique-d-une-Suspension-Automobile-sous-MSC-ADAMS
Projet ADAMS (TP2 ASMC - INSA HDF) sur l'analyse dynamique d'une suspension automobile. Du modèle double triangulation au modèle réduit quart de véhicule : identification théorique des coefficients k_eq, c_eq et simulation du passage d'un dos d'âne pour évaluer le confort et la tenue de route. 


[cite_start]Ce dépôt contient les fichiers de simulation et le compte rendu du **TP2 d'ASMC** réalisé dans le cadre du cursus à l'**INSA Hauts-de-France** (Université Polytechnique Hauts-de-France)[cite: 1].

## 👥 Auteurs
* [cite_start]**Pierre Vilcocq** [cite: 1]
* [cite_start]**Léo Sentes** [cite: 1]
* [cite_start]**Groupe :** 5 [cite: 1]
* [cite_start]**Date :** 17 février 2026 [cite: 1]

---

## 🎯 Objectif du Projet
[cite_start]L'objectif de ce projet est d'apporter une justification physique et mathématique à l'utilisation d'un **modèle quart de véhicule** à 2 degrés de liberté, puis de l'exploiter pour caractériser le comportement dynamique d'une suspension automobile lors du franchissement d'un obstacle (dos d'âne)[cite: 1].

Le projet se divise en deux grandes parties :
1. [cite_start]**Identification** des caractéristiques d'une suspension réelle à double triangulation pour définir un modèle équivalent[cite: 2].
2. [cite_start]**Simulation et analyse** du passage d'un obstacle avec le modèle quart de véhicule réduit[cite: 13].

---

## 🛠️ Structure et Déroulement du TP

### Partie 1 : Identification des caractéristiques de la suspension
[cite_start]À partir d'un modèle partiel (`suspension.bin`), une suspension à double triangulation complète a été modélisée sous MSC ADAMS[cite: 2, 324].
* [cite_start]**Méthodologie :** Simulation du comportement vibratoire du système en oscillation libre (sans pesanteur) afin de relever le déplacement vertical de l'axe de roue $Z_{roue}(t)$[cite: 5, 325].
* **Exploitation mathématique :** En identifiant la courbe obtenue avec l'équation théorique amortie :
  $$Z_{roue\_eq}(t)=Z_{0}(cos\Omega t+\frac{\xi\omega_{0}}{\Omega}sin\Omega t)e^{-\xi\omega_{0}t} + Z_{final}$$
  [cite_start]les coefficients équivalents ont été identifiés analytiquement[cite: 7]:
  * [cite_start]**Raideur équivalente ($k_{eq}$) :** $27288 \text{ N.mm}^{-1}$ [cite: 11]
  * **Amortissement équivalent ($c_{eq}$) :** $479 \text{ N.s.mm}^{-1}$ [cite: 11]

[cite_start]La superposition des courbes ADAMS et du modèle théorique calculé valide la réduction de modèle[cite: 11, 12, 35].

### Partie 2 : Modélisation simplifiée quart de véhicule & Passage d'obstacle
[cite_start]Un nouveau modèle réduit à un quart de véhicule a été conçu sous ADAMS sur la base des coefficients identifiés ($k_{eq}$, $c_{eq}$) et des paramètres pneumatiques fournis ($k_{pneu} = 175 \text{ N/mm}$, $c_{pneu} = 0,525 \text{ Ns/mm}$)[cite: 13, 15].
* **Caractéristiques de la simulation :**
  * [cite_start]Masse suspendue ($\frac{1}{4}$ véhicule) : $320 \text{ kg}$ [cite: 15]
  * [cite_start]Masse non suspendue (Roue) : $52 \text{ kg}$ [cite: 15]
  * Obstacle : Dos d'âne sinusoïdal de hauteur $h = 0,1 \text{ m}$ et de longueur $l = 1 \text{ m}$ [cite: 18]
  * [cite_start]Vitesse de franchissement : $50 \text{ km/h}$ (durée de l'impact : $72 \text{ ms}$) [cite: 18]

---

## 📊 Critères de Performance Évalués

[cite_start]Les résultats obtenus mettent en évidence deux aspects essentiels de la dynamique du véhicule[cite: 340]:

1. [cite_start]**Le Confort :** L'accélération verticale maximale subie par le châssis est mesurée à environ **$0,128\text{ g}$** ($12500 \text{ mm.s}^{-2}$)[cite: 20, 21]. [cite_start]Cette valeur faible confirme un excellent filtrage des vibrations par la suspension conçue[cite: 21, 36].
2. [cite_start]**La Tenue de Route :** * Lors de l'impact initial, le pneumatique s'écrase de **$35 \text{ mm}$**[cite: 24].
   * [cite_start]En sortie d'obstacle, on observe un phénomène de décollement numérique où la roue "s'envole" de **$87 \text{ mm}$** au-dessus du sol[cite: 25, 31]. 
   * *Note physique :* L'apparition de forces de contact négatives dans les graphes ADAMS met en évidence les limites du modèle numérique (un pneu réel ne peut pas "tirer" sur le sol, la force normale réelle tombe à zéro lors de la perte de contact)[cite: 30, 32].

---

## 📁 Contenu du Repository
* `/Simulation_Files` : Fichiers `.bin` ou de commande ADAMS utilisés pour les deux modèles (double triangulation et quart de véhicule).
* `/Reports` : Le compte rendu complet du TP au format PDF (`TP_2_ASMC_VILCOCQ_SENTES.pdf`).

## 💻 Logiciels requis
* **MSC ADAMS** (Adams/View & Adams/PostProcessor)
