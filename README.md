# ecommerce-classification
Classification sur des données e-commerce

## Énoncé du projet

Consulter [l’énoncé du projet](https://github.com/yste9/ecommerce-classification -> Prédiction achat en e-commerce 2026


# Prédiction de l’intention d’achat en e-commerce

**Étude comparative de méthodes de classification supervisée sous R.**

Projet universitaire réalisé par **Yannick ASSI** et **Guillaume COULON** à l’Université Catholique de l’Ouest, dans le cadre du Master MIASHS, sous l’encadrement de **Nisrine DOUMIATI JRAD**.

📅 Présentation : février 2026.

## 🎯 Objectif

Prédire si une session de navigation sur un site e-commerce aboutira à un achat, à partir de variables décrivant le comportement et le contexte de visite.

La variable cible est **Revenue** :

- `1` : la session aboutit à un achat ;
- `0` : la session n’aboutit pas à un achat.

L’objectif est de comparer plusieurs modèles en tenant compte de leur performance globale, de leur capacité à détecter les acheteurs et de leur interprétabilité.

## 📊 Données

Le jeu de données comporte **12 330 observations** avant préparation.

Les classes sont déséquilibrées :

- Environ **85 % de non-acheteurs**.
- Environ **15 % d’acheteurs**.

| Catégorie | Exemples de variables |
|---|---|
| Pages consultées | `Administrative`, `Informational`, `ProductRelated` |
| Durées de navigation | `Administrative_Duration`, `ProductRelated_Duration` |
| Comportement | `BounceRates`, `ExitRates`, `PageValues` |
| Contexte | `Month`, `VisitorType`, `Weekend` |

## ⚙️ Démarche

1. Transformer les variables qualitatives en variables numériques.
2. Détecter et filtrer les valeurs extrêmes à partir du quantile 0,99.
3. Normaliser les variables quantitatives.
4. Constituer la base préparée de **11 768 observations**.
5. Effectuer une séparation aléatoire :
   - **80 % pour l’apprentissage** ;
   - **20 % pour le test**.
6. Entraîner et comparer les méthodes de classification.
7. Interpréter les résultats en fonction de l’objectif métier.

Ces étapes décrivent la démarche rapportée dans la présentation. Leur ordre exact et leur application aux ensembles d’apprentissage et de test doivent être vérifiés dans le code pour évaluer la reproductibilité et l’absence de fuite de données.

## 🧠 Modèles étudiés

- Analyse discriminante linéaire — **LDA**.
- Analyse discriminante quadratique — **QDA**.
- **Arbre de décision**.
- **SVM linéaire**.
- **SVM non linéaire**.
- **Réseau de neurones**.

## 📈 Résultats

Les valeurs ci-dessous sont celles rapportées dans la présentation et sont arrondies.

Les taux de détection correspondent à la proportion correctement classée au sein de chaque classe.

| Modèle | Accuracy globale | Détection des non-acheteurs | Détection des acheteurs |
|---|---:|---:|---:|
| LDA | ≈ 89 % | ≈ 97 % | ≈ 42 % |
| QDA | ≈ 82 % | ≈ 87 % | ≈ 67 % |
| Arbre de décision | ≈ 90 % | ≈ 94 % | ≈ 51 % |
| SVM linéaire | ≈ 89 % | ≈ 97 % | ≈ 40 % |
| SVM non linéaire | ≈ 89 % | ≈ 96 % | ≈ 50 % |
| Réseau de neurones | Très faible | Faible | Très faible |

### Analyse des résultats

Une accuracy élevée ne garantit pas une bonne détection des acheteurs. Les modèles reconnaissent généralement mieux les non-acheteurs, qui constituent la classe majoritaire.

La **QDA** obtient le meilleur taux de détection des acheteurs parmi les résultats présentés, avec une accuracy globale plus faible.

L’**arbre de décision** est retenu dans l’étude comme un compromis entre performance, interprétabilité et lecture métier. Il obtient environ **90 % d’accuracy**, mais ne détecte qu’environ **la moitié des acheteurs** : cette limite reste importante.

Les faibles résultats du réseau de neurones concernent l’implémentation testée dans ce projet et ne permettent pas de conclure à l’inadaptation générale de cette méthode.

## 💡 Interprétation métier

L’analyse de l’arbre de décision met notamment en avant :

- `PageValues` ;
- `BounceRates` ;
- `ProductRelated_Duration` ;
- `Administrative` ;
- `Month`.

Les résultats suggèrent une association entre l’achat et :

- La valeur des pages visitées.
- Un faible taux de rebond.
- Un engagement plus important sur les pages produits.

Ces observations décrivent des relations prédictives, sans démontrer de causalité.

## 🔎 Limites et pistes d’amélioration

- Mieux prendre en compte le déséquilibre des classes.
- Optimiser les hyperparamètres avec une validation croisée adaptée.
- Compléter l’évaluation avec la précision, le rappel, le F1-score et la courbe précision-rappel.
- Étudier la pondération des classes ou le sur-échantillonnage sur les données d’apprentissage uniquement.
- Vérifier que les transformations sont ajustées sur l’apprentissage, puis appliquées au test.
- Vérifier que chaque variable, notamment `PageValues`, est disponible au moment où la prédiction doit être faite.
- Documenter les versions des dépendances, la graine aléatoire et les instructions d’exécution lors de l’ajout du code.

## 📁 Documents

- [l’énoncé du projet](https://github.com/yste9/ecommerce-classification

## 🛠️ Compétences mobilisées

- Préparation et transformation des données.
- Classification supervisée.
- Analyse discriminante.
- Support Vector Machines.
- Arbres de décision.
- Évaluation et comparaison de modèles.
- Interprétation métier.
- Programmation sous R.

## 👥 Auteurs

**Yannick ASSI** et **Guillaume COULON**

Université Catholique de l’Ouest - Master MIASHS




