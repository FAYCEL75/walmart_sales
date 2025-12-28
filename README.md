# Walmart – Prédiction des ventes hebdomadaires  
**Projet Machine Learning | Approche professionnelle & orientée business**

---

Ce projet démontre ma capacité à **concevoir, structurer et expliquer un pipeline de Machine Learning de bout en bout**, appliqué à un cas business réel :  
**la prédiction des ventes hebdomadaires chez Walmart**.

En quelques mots :
- Problème business clair
- Données réelles et imparfaites
- Pipeline ML propre et reproductible
- Modèle interprétable
- Résultats chiffrés et comparés
- Conclusions exploitables métier

---

## Problème business

Le service marketing de Walmart souhaite :
- **anticiper les ventes hebdomadaires par magasin**,  
- **comprendre les leviers clés** (saisonnalité, jours fériés, contexte économique),  
- disposer d’un **modèle explicable**, utilisable comme outil d’aide à la décision.

---

## Données & compréhension métier

Dataset (version Jedha) comprenant :
- Ventes hebdomadaires (`Weekly_Sales`) – **cible**
- Identifiant magasin (`Store`)
- Jours fériés (`Holiday_Flag`)
- Indicateurs économiques (température, carburant, CPI, chômage)
- Date (transformée en features temporelles)

Contraintes réelles :
- outliers présents,
- magasins très hétérogènes,
- faible corrélation directe entre certaines variables et la cible.

---

## Analyse exploratoire (EDA)

L’EDA met en évidence :
- des **différences structurelles fortes entre magasins**,
- une **saisonnalité claire** (mois, jour de la semaine),
- un **impact réel des semaines fériées**,
- un rôle secondaire mais pertinent des indicateurs économiques.

Ces constats guident les choix de features et de modèles.

---

## Pipeline Machine Learning

Pipeline scikit-learn **propre et industriel**, sans fuite de données :

- Nettoyage de la cible (jamais imputée)
- Feature engineering temporel (`Year`, `Month`, `Day`, `DayOfWeek`)
- Gestion des outliers (règle des 3σ)
- Encodage catégoriel (`OneHotEncoder`)
- Standardisation (`StandardScaler`)
- Séparation Train / Test (80/20)
- Modélisation via `Pipeline` + `ColumnTransformer`

---

## Modèles & choix techniques

### Modèles testés
- Régression Linéaire (baseline)
- Régression Ridge (régularisation)
- Ridge optimisée via GridSearchCV

### Résultats (jeu de test)

| Modèle | R² | RMSE |
|------|----|------|
| Linear Regression | 0.947 | 132 277 |
| Ridge (α = 1.0) | 0.871 | 206 402 |
| **Ridge (α = 0.01)** | **0.955** | **121 026** |

**Modèle final retenu : Ridge (α = 0.01)**  
Meilleur compromis **performance / généralisation / explicabilité**

---

## Interprétation & valeur métier

L’analyse des coefficients montre que :
- le **magasin** est le facteur dominant (structurel),
- la **saisonnalité** joue un rôle clé,
- les **jours fériés** ont un impact mesurable,
- les variables économiques complètent l’information.

Le modèle est **compréhensible**, donc **exploitable par les équipes marketing**.

---

## Limites identifiées (vision mature)

- Modèle linéaire → interactions non capturées
- Gestion simple des outliers
- Manque de variables métier (promotions, région, taille magasin)
- Dataset bruité

Ces limites sont **connues, assumées et documentées**.

---

## Pistes d’évolution

- Modèles non linéaires (RandomForest, XGBoost)
- Features avancées (lags, moyennes glissantes)
- Analyse d’erreur par magasin
- Déploiement API / dashboard

---


## Auteur

Projet réalisé dans le cadre de la formation **Jedha – Machine Learning**.  
Objectif : démontrer une **approche professionnelle, lisible et orientée impact** du Machine Learning.
