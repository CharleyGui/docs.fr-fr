---
title: Tâches d’apprentissage automatique
description: Explorez les différentes tâches Machine Learning ainsi que les tâches associées prises en charge dans ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399202"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Tâches Machine Learning dans ML.NET

Une tâche d’apprentissage automatique est le type de prédiction ou d’inférence qui est faite, en fonction du problème ou de la question qui est posée, et des données disponibles. Par exemple, la tâche de classification attribue des données aux catégories, et les données des groupes de tâches en grappe en fonction de la similitude.

Les tâches d’apprentissage automatique reposent sur des modèles dans les données plutôt que d’être explicitement programmées.

Cet article décrit les différentes tâches d’apprentissage automatique que vous pouvez choisir dans ML.NET et certains cas d’utilisation courante.

Une fois que vous avez décidé de tâche qui fonctionne pour votre scénario, vous devez choisir le meilleur algorithme pour entraîner le modèle. Les algorithmes disponibles sont listés dans la section pour chaque tâche.

## <a name="binary-classification"></a>Classification binaire

Une tâche [Apprentissage automatique supervisé](glossary.md#supervised-machine-learning) utilisée pour prédire à laquelle des deux classes (catégories) appartient une instance de données. L’entrée d’un algorithme de classification est un ensemble d’exemples étiquetés, où chaque étiquette est un entier ayant pour valeur 0 ou 1. La sortie d’un algorithme de classification binaire est un classifieur, que vous pouvez utiliser pour prédire la classe de nouvelles instances sans étiquette. Voici quelques exemples de scénarios de classification binaire :

* [Déterminer si des commentaires Twitter](../tutorials/sentiment-analysis.md) sont « positifs » ou « négatifs ».
* Diagnostiquer si un patient est atteint ou non d’une certaine maladie.
* Décider si un e-mail doit être considéré comme « spam » ou non.
* Déterminer si une photo contient un article particulier ou non, comme un chien ou un fruit.

Pour plus d’informations, consultez l’article Wikipédia [Classification binaire](https://en.wikipedia.org/wiki/Binary_classification).

### <a name="binary-classification-trainers"></a>Entraîneurs de classification binaire

Vous pouvez entraîner un modèle de classification binaire en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a>Entrées et sorties de classification binaire

Pour tirer le meilleur parti de la classification binaire, vous devez équilibrer les données d’entraînement (autrement dit, avoir le même nombre de données d’entraînement positives que négatives). Les valeurs manquantes doivent être traitées avant l’entraînement.

Les données de la colonne d’étiquettes d’entrée doivent être <xref:System.Boolean>.
Les données de la colonne des caractéristiques d’entrée doivent être un vecteur de taille fixe de <xref:System.Single>.

Ces formateurs en extradent les colonnes suivantes :

| Nom de colonne de sortie | Type de colonne | Description|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Score brut calculé par le modèle|
| `PredictedLabel` | <xref:System.Boolean> | Étiquette prédite, en fonction du signe du score. Un score négatif est mappé à `false`, tandis qu’un score positif est mappé à `true`.|

## <a name="multiclass-classification"></a>Classification multiclasse

Une tâche [Apprentissage automatique supervisé](glossary.md#supervised-machine-learning) utilisée pour prédire la classe (catégorie) d’une instance de données. L’entrée d’un algorithme de classification est un ensemble d’exemples étiquetés. Chaque étiquette démarre normalement en tant que texte. Elle est ensuite exécutée via TermTransform, qui la convertit en un type de clé (numérique). La sortie d’un algorithme de classification est un classifieur, que vous pouvez utiliser pour prédire la classe de nouvelles instances sans étiquette. Voici quelques exemples de scénarios de classification multiclasse :

* Déterminer la race d’un chien, par exemple « Husky de Sibérie », « Golden Retriever », « Caniche », etc.
* Déterminer si des critiques d’un film sont « positives », « neutres » ou « négatives ».
* Classer les évaluations d’un hôtel par « situation géographique », « prix », « propreté », etc.

Pour plus d’informations, consultez l’article Wikipédia [Classification multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification).

>[!NOTE]
>OvA (One vs all, Un comparé à tous) met à niveau les [learners de classification binaire](#binary-classification) pour agir sur les jeux de données multiclasses. Pour plus d’informations, consultez l’article [Wikipédia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-trainers"></a>Entraîneurs de classification multiclasse

Vous pouvez entraîner un modèle de classification multiclasse en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a>Entrées et sorties de classification multiclasse

Les données de la colonne d’étiquettes d’entrée doivent être de type [clé](xref:Microsoft.ML.Data.KeyDataViewType).
La colonne des caractéristiques doit être un vecteur de taille fixe de <xref:System.Single>.

Cet entraîneur génère la sortie suivante :

| Nom de sortie | Type | Description|
| -- | -- | -- |
| `Score` | Vecteur de <xref:System.Single> | Les scores de toutes les classes. Une valeur supérieure signifie une plus forte probabilité d’appartenir à la classe associée. Si l’i-ème élément a la plus grande valeur, l’index de l’étiquette prédite est i. Notez que i est l’index de base zéro. |
| `PredictedLabel` | type [clé](xref:Microsoft.ML.Data.KeyDataViewType) | Index de l’étiquette prédite. Si sa valeur est i, l’étiquette réelle est la i-ème catégorie dans le type d’étiquette d’entrée avec une valeur de clé. |

## <a name="regression"></a>régression ;

Une tâche [Apprentissage automatique supervisée](glossary.md#supervised-machine-learning) utilisée pour prédire la valeur de l’étiquette d’un ensemble de fonctionnalités connexes. L’étiquette peut avoir n’importe quelle valeur réelle et ne provient pas d’un ensemble fini de valeurs comme dans les tâches de classification. Les algorithmes de régression modèlent la dépendance de l’étiquette sur ses fonctionnalités connexes pour déterminer la façon dont l’étiquette change avec des valeurs de fonctionnalités différentes. L’entrée d’un algorithme de régression est un ensemble d’exemples avec des étiquettes de valeurs connues. La sortie d’un algorithme de régression est une fonction, que vous pouvez utiliser pour prédire la valeur de l’étiquette pour tout nouvel ensemble de fonctionnalités d’entrée. Voici quelques exemples de scénarios de régression :

* Prédire le prix d’une maison selon ses attributs, par exemple le nombre de chambres, l’emplacement ou la taille.
* Prédire le cours d’actions en fonction de données historiques et des tendances du marché actuel.
* Prédire les ventes d’un produit en fonction d’un budget publicitaire.

### <a name="regression-trainers"></a>Entraîneurs de régression

Vous pouvez entraîner un modèle de régression en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Entrées et sorties de régression

Les données de la colonne d’étiquettes d’entrée doivent être <xref:System.Single>.

Les entraîneurs pour cette tâche génèrent le résultat suivant :

| Nom de sortie | Type | Description|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Score brut prédit par le modèle |

## <a name="clustering"></a>Clustering

Une tâche [Apprentissage automatique non supervisé](glossary.md#unsupervised-machine-learning) utilisée pour regrouper des instances de données dans des clusters contenant des caractéristiques similaires. Le clustering permet également d’identifier, dans un jeu de données, les relations qui peuvent ne pas être logiquement dérivées par navigation ou simple observation. Les entrées et sorties d’un algorithme de clustering dépendent de la méthode choisie. Vous pouvez adopter une approche de type distribution, centroïde, connectivité ou basée sur la densité. ML.NET prend actuellement en charge une approche de type centroïde à l’aide du clustering K-Means. Voici quelques exemples de scénarios de clustering :

* Évaluer les segments d’une clientèle d’hôtel en fonction de leurs habitudes et des caractéristiques de l’hôtel.
* Identifier les segments d’une clientèle et les données démographiques pour faciliter la mise en œuvre de campagnes publicitaires ciblées.
* Classer un inventaire en fonction de métriques de fabrication.

### <a name="clustering-trainer"></a>Entraîneur de clustering

Vous pouvez entraîner un modèle de clustering en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a>Entrées et sorties de clustering

Les données de caractéristiques d’entrée doivent être <xref:System.Single>. Aucune étiquette n’est nécessaire.

Cet entraîneur génère la sortie suivante :

| Nom de sortie | Type | Description|
| -- | -- | -- |
| `Score` | Vecteur de <xref:System.Single> | Distances entre le point de données spécifique et les centroïdes de tous les clusters |
| `PredictedLabel` | type [clé](xref:Microsoft.ML.Data.KeyDataViewType) | Index du cluster le plus proche prédit par le modèle. |

## <a name="anomaly-detection"></a>Détection des anomalies

Cette tâche crée un modèle de détection d’anomalie à l’aide de la méthode Principal Component Analysis (PCA). La détection d’anomalie PCA vous permet de créer un modèle dans des scénarios où il est facile d’obtenir des données d’apprentissage à partir d’une classe, notamment des transactions valides, mais où il est difficile d’obtenir suffisamment d’échantillons d’anomalies ciblées.

Technique éprouvée dans l’apprentissage automatique (Machine Learning), la méthode PCA est fréquemment utilisée dans l’analyse exploratoire des données car elle révèle la structure interne des données et explique la variance dans les données. PCA fonctionne en analysant les données contenant plusieurs variables. Elle recherche des corrélations entre les variables et détermine la combinaison de valeurs qui identifie le mieux les différences dans les résultats. Ces valeurs de fonctionnalité combinées sont utilisées pour créer un espace de fonctionnalités plus compact, appelé principaux composants.

La détection d’anomalie englobe de nombreuses tâches importantes pour l’apprentissage automatique :

* Identification des transactions potentiellement frauduleuses.
* Modèles d’apprentissage signalant une intrusion sur le réseau.
* Recherche de clusters anormaux de patients.
* Vérification des valeurs entrées dans un système.

Les anomalies constituant, par définition, des événements rares, il peut être difficile de recueillir un échantillon représentatif des données à utiliser pour la modélisation. Les algorithmes inclus dans cette catégorie ont été spécialement conçus pour relever les défis de base qu’impliquent la création et l’apprentissage des modèles à l’aide de jeux de données déséquilibrés.

### <a name="anomaly-detection-trainer"></a>Entraîneur de détection d’anomalie

Vous pouvez entraîner un modèle de détection d’anomalie en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Sorties et entrées de la détection d’anomalie

Les caractéristiques d’entrée doivent être un vecteur de taille fixe de <xref:System.Single>.

Cet entraîneur génère la sortie suivante :

| Nom de sortie | Type | Description|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Score non négatif sans borne calculé par le modèle de détection d’anomalie |
| `PredictedLabel` | <xref:System.Boolean> | Une valeur vraie/fausse représentant si l’entrée est une anomalie (PredictedLabel-true) ou non (PredictedLabel-faux) |

## <a name="ranking"></a>Classement

Une tâche de classement établit un classement à partir d’un ensemble d’exemples étiquetés. Cet exemple d’ensemble se compose de groupes d’instances qui peuvent être évalués selon un critère donné. Les étiquettes de classement sont {0, 1, 2, 3, 4} pour chaque instance.  Le classement est formé pour trier les nouveaux groupes d’instance en attribuant un score inconnu à chaque instance. Les apprenants de classement ML.NET utilisent un [classement basé sur l’apprentissage automatique](https://en.wikipedia.org/wiki/Learning_to_rank).

### <a name="ranking-training-algorithms"></a>Algorithmes d’entraînement de classement

Vous pouvez entraîner un modèle de classement en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a>Entrées et sorties de classement

Le type de données des étiquettes d’entrée doit être de type [clé](xref:Microsoft.ML.Data.KeyDataViewType) ou <xref:System.Single>. La valeur de l’étiquette détermine la pertinence, une valeur supérieure indiquant une pertinence plus élevée. Si l’étiquette est un type [clé](xref:Microsoft.ML.Data.KeyDataViewType), l’index de clé est la valeur de la pertinence, le plus petit index étant le moins pertinent. Si l’étiquette est un <xref:System.Single>, une valeur plus grande indique une pertinence plus élevée.

Les données de caractéristique doivent être un vecteur de taille fixe de <xref:System.Single> et la colonne du groupe de lignes d’entrée doit être de type [clé](xref:Microsoft.ML.Data.KeyDataViewType).

Cet entraîneur génère la sortie suivante :

| Nom de sortie | Type | Description|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Score sans borne calculé par le modèle pour déterminer la prédiction |

## <a name="recommendation"></a>Recommandation

Une tâche de recommandation permet de dresser la liste des produits ou services recommandés. ML.NET utilise la méthode [Factorisation de matrice (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), un algorithme de [filtrage collaboratif](https://en.wikipedia.org/wiki/Collaborative_filtering) pour obtenir des recommandations lorsque votre catalogue contient des données d’évaluation de produit historiques. Par exemple, vous disposez des données d’évaluation de films historiques pour vos utilisateurs et souhaitez leur recommander d’autres vidéos.

### <a name="recommendation-training-algorithms"></a>Algorithmes d’entraînement de recommandation

Vous pouvez entraîner un modèle de recommandation en utilisant les algorithmes suivants :

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a>Prévisions

La tâche de prévision utilise les données passées des séries chronologiques pour faire des prédictions sur le comportement futur. Les scénarios applicables aux prévisions comprennent les prévisions météorologiques, les prévisions de ventes saisonnières et l’entretien prédictif,

### <a name="forecasting-trainers"></a>Formateurs de prévision

Vous pouvez former un modèle de prévision avec l’algorithme suivant :

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
