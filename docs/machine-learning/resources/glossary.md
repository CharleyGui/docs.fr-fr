---
title: Glossaire de l’apprentissage automatique
description: La liste suivante est une compilation des principaux termes Machine Learning, utiles lorsque vous générez vos modèles personnalisés.
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: 32ccb6df1cb08db45ebd25a0d1c0ea4396a6c50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398936"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Glossaire Machine Learning des principaux termes

La liste suivante est une compilation des principaux termes Machine Learning, utiles lorsque vous générez vos modèles personnalisés dans ML.NET.

## <a name="accuracy"></a>Précision

Dans la [classification](#classification), la précision correspond au nombre d’éléments correctement classifiés, divisé par le nombre total d’éléments dans le jeu de test. Cette valeur est comprise entre 0 (la moins précise) et 1 (la plus précise). La précision est une des métriques d’évaluation des performances du modèle. Utilisez-la conjointement avec les options [précision](#precision), [rappel](#recall) et [F-score](#f-score).

## <a name="area-under-the-curve-auc"></a>Zone sous la courbe (AUC)

Dans la [classification binaire](#binary-classification), une métrique d’évaluation qui correspond à la valeur de la zone sous la courbe qui trace le taux de vrais positifs (sur l’axe des y) par rapport au taux de faux positifs (sur l’axe des x). Cette valeur est comprise entre 0,5 (pire) et 1 (meilleur). Également appelée zone sous la courbe ROC (Receiver Operating Characteristic). Pour plus d’informations, consultez l’article Wikipédia [Courbe ROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic).

## <a name="binary-classification"></a>Classification binaire

Cas de [classification](#classification) où l’[étiquette](#label) provient uniquement d’une de deux classes. Pour plus d’informations, consultez la section [Classification binaire](tasks.md#binary-classification) de la rubrique [Tâches d’apprentissage automatique](tasks.md).

## <a name="calibration"></a>Étalonnage

L’étalonnage est le processus consistant à mapper un score brut à une appartenance de classe à des fins de classification binaire et multiclasse. Certains entraîneurs ML.NET ont un suffixe `NonCalibrated`. Ces algorithmes produisent un score brut qui doit ensuite être mappé à une probabilité de classe.

## <a name="catalog"></a>Catalogue

Dans ML.NET, un catalogue est une collection de fonctions d’extension, regroupées selon un objectif commun.

Par exemple, chaque tâche de machine learning (classification binaire, régression, classement, etc.) dispose d’un catalogue d’algorithmes de machine learning (entraîneurs). Le catalogue des entraîneurs de classification binaire est : <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>.

## <a name="classification"></a>classification ;

Lorsque les données sont utilisées pour prédire une catégorie, la tâche [Apprentissage automatique supervisé](#supervised-machine-learning) est appelée classification. [Classification binaire](#binary-classification) fait référence à la prédiction de deux catégories uniquement (par exemple, la classification d’une image en tant qu’image de « chat » ou de « chien »). [Classification multiclasse](#multiclass-classification) fait référence à la prédiction de plusieurs catégories (par exemple, lors de la classification d’une image en tant qu’image d’une race spécifique de chien).

## <a name="coefficient-of-determination"></a>Coefficient de détermination

Dans une [régression](#regression), une métrique d’évaluation qui indique la manière dont les données s’intègrent à un modèle. Cette valeur est comprise entre 0 et 1. Une valeur de 0 signifie que les données sont aléatoires ou ne s’intègrent pas au modèle. Une valeur de 1 signifie que le modèle correspond exactement aux données. Cette valeur est souvent désignée sous le terme r<sup>2</sup>, R<sup>2</sup> ou R carré.

## <a name="data"></a>Données

Les données sont essentielles à toute application de machine learning. Dans ML.NET, les données sont représentées par des objets <xref:Microsoft.ML.IDataView>. Les objets de vue de données :

- Sont composés de lignes et de colonnes
- Sont évalués tardivement, autrement dit ils ne chargent des données que quand une opération les demande
- Contiennent un schéma qui définit le type, le format et la longueur de chaque colonne

## <a name="estimator"></a>Estimateur

Classe dans ML.NET qui implémente l’interface <xref:Microsoft.ML.IEstimator%601>.

Un estimateur est une spécification d’une transformation (transformation de préparation des données et transformation d’entraînement de modèle Machine Learning). Les estimateurs peuvent être chaînés dans un pipeline des transformations. Les paramètres d’un estimateur ou d’un pipeline d’estimateurs sont appris quand <xref:Microsoft.ML.IEstimator%601.Fit%2A> est appelé. Le résultat de <xref:Microsoft.ML.IEstimator%601.Fit%2A> est un [transformer](#transformer).

## <a name="extension-method"></a>Méthode d’extension

Méthode .NET qui fait partie d’une classe, mais qui est définie en dehors de celle-ci. Le premier paramètre d’une méthode d’extension est une référence `this` statique à la classe à laquelle appartient la méthode d’extension.

Les méthodes d’extension sont largement utilisées dans ML.NET pour construire des instances d’[estimateurs](#estimator).

## <a name="feature"></a>Fonctionnalité

Propriété mesurable du phénomène mesuré, en général, une valeur (double) numérique. Plusieurs fonctionnalités sont appelées **vecteur de fonctionnalité** et sont généralement stockées en tant que `double[]`. Les fonctionnalités définissent les principales caractéristiques du phénomène mesuré. Pour plus d’informations, consultez l’article Wikipédia [Fonctionnalité](https://en.wikipedia.org/wiki/Feature_(machine_learning)).

## <a name="feature-engineering"></a>Ingénierie des caractéristiques

L’ingénierie de fonctionnalité est le processus qui consiste à définir un ensemble de [fonctionnalités](#feature) et à développer des logiciels qui produisent des vecteurs de fonctionnalité à partir des données de phénomène disponibles, par exemple, l’extraction d’une fonctionnalité. Pour plus d’informations, consultez l’article Wikipédia [Feature engineering](https://en.wikipedia.org/wiki/Feature_engineering).

## <a name="f-score"></a>F-score

Dans une [classification](#classification), une métrique d’évaluation qui équilibre [précision](#precision) et [rappel](#recall).

## <a name="hyperparameter"></a>Hyperparamètre

Un paramètre d’un algorithme d’apprentissage automatique. Par exemple, le nombre d’arbres à assimiler dans une forêt décisionnelle ou la taille d’étape dans un algorithme de jambage descendant dégradé. Les valeurs des *hyperparamètres* sont définies avant l’apprentissage du modèle et régissent le processus de recherche des paramètres de la fonction de prédiction, par exemple, les points de comparaison dans un arbre de décision ou les pondérations dans un modèle de régression linéaire. Pour plus d’informations, consultez l’article Wikipédia [Hyperparamètre](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)).

## <a name="label"></a>Étiquette

L’élément à prédire avec le modèle d’apprentissage automatique. Par exemple, la race d’un chien ou le futur cours d’une action.

## <a name="log-loss"></a>Perte du journal

Dans une [classification](#classification), une métrique d’évaluation qui caractérise la précision d’un classifieur. Plus la perte du journal est faible, plus un classifieur est précis.

## <a name="loss-function"></a>Fonction de perte

Une fonction de perte est la différence entre les valeurs d’étiquette d’entraînement et la prédiction effectuée par le modèle. Les paramètres du modèle sont estimés en réduisant la fonction de perte.

Différents entraîneurs peuvent être configurés avec différentes fonctions de perte.

## <a name="mean-absolute-error-mae"></a>Erreur d'absolue moyenne

Dans une [régression](#regression), une métrique d’évaluation qui représente la moyenne de toutes les erreurs du modèle, où l’erreur de modèle est la distance entre la valeur d’[étiquette](#label) prédite et la valeur d’étiquette correcte.

## <a name="model"></a>Modèle

En règle générale, les paramètres de la fonction de prédiction. Par exemple, les pondérations dans un modèle de régression linéaire ou les points de fractionnement dans un arbre de décision. Dans ML.NET, un modèle contient toutes les informations nécessaires pour prédire l’[étiquette](#label) d’un objet de domaine (par exemple, une image ou un texte). Cela signifie que les modèles ML.NET incluent les étapes de fonctionnalisation nécessaires ainsi que les paramètres de la fonction de prédiction.

## <a name="multiclass-classification"></a>Classification multiclasse

Cas de [classification](#classification) où l’[étiquette](#label) provient d’une de trois classes ou plus. Pour plus d’informations, consultez la section [Classification multiclasse](tasks.md#multiclass-classification) de la rubrique [Tâches d’apprentissage automatique](tasks.md).

## <a name="n-gram"></a>N-gramme

Un schéma d’extraction de fonctionnalité pour les données texte : toute séquence de N termes se transforme en une valeur [fonctionnalité](#feature).

## <a name="normalization"></a>Normalisation

La normalisation est le processus de mise à l’échelle des données à virgule flottante en valeurs comprises entre 0 et 1. La plupart des algorithmes d’entraînement utilisés dans ML.NET requièrent la normalisation des données de fonctionnalités d’entrée. ML.NET fournit une série de [transformations pour la normalisation](transforms.md#normalization-and-scaling)

## <a name="numerical-feature-vector"></a>Vecteur de fonctionnalité numérique

Un vecteur de [fonctionnalité](#feature) constitué uniquement de valeurs numériques. Cette valeur est similaire à `double[]`.

## <a name="pipeline"></a>Pipeline

Toutes les opérations nécessaires pour adapter un modèle à un jeu de données. Un pipeline se compose des étapes d’importation, de transformation, de fonctionnalisation et d’apprentissage des données. Une fois son apprentissage terminé, le pipeline se transforme en modèle.

## <a name="precision"></a>Precision

Dans une [classification](#classification), la précision d’une classe correspond au nombre d’éléments correctement prévus comme appartenant à cette classe, divisé par le nombre total d’éléments prévus comme appartenant à la classe.

## <a name="recall"></a>Rappel

Dans une [classification](#classification), le rappel d’une classe correspond au nombre d’éléments correctement prévus comme appartenant à cette classe, divisé par le nombre total d’éléments appartenant effectivement à la classe.

## <a name="regularization"></a>Régularisation

 La régularisation pénalise un modèle linéaire en raison de sa trop grande complexité. Il existe deux types de régularisation :

- La régularisation $L_1$ attribue une pondération nulle aux caractéristiques non significatives. La taille du modèle enregistré peut être plus petite après ce type de régularisation.
- la régularisation de $L 2 $ minimise la plage de poids pour les caractéristiques insignifiantes. Il s’agit d’un processus plus général et moins sensible aux valeurs aberrantes.

## <a name="regression"></a>régression ;

Une tâche [Apprentissage automatique supervisé](#supervised-machine-learning) où la sortie est une valeur réelle, par exemple, double. Exemple : prédiction de cours d’actions. Pour plus d’informations, consultez la section [Régression](tasks.md#regression) de la rubrique [Tâches d’apprentissage automatique](tasks.md).

## <a name="relative-absolute-error"></a>Erreur absolue relative

Dans une [régression](#regression), une métrique d’évaluation correspondant à la somme de toutes les erreurs absolues, divisée par la somme des distances entre les valeurs d’[étiquette](#label) correctes et la moyenne de toutes les valeurs d’étiquette correctes.

## <a name="relative-squared-error"></a>Erreur quadratique relative

Dans une [régression](#regression), une métrique d’évaluation correspondant à la somme de toutes les erreurs absolues quadratiques, divisée par la somme des distances quadratiques entre les valeurs d’[étiquette](#label) correctes et la moyenne de toutes les valeurs d’étiquette correctes.

## <a name="root-of-mean-squared-error-rmse"></a>Racine de l’erreur quadratique moyenne (RMSE)

Dans une [régression](#regression), une métrique d’évaluation correspondant à la racine carrée de la moyenne des carrés des erreurs.

## <a name="scoring"></a>Notation

Le score est le processus qui consiste à appliquer de nouvelles données à un modèle d’apprentissage automatique entraîné et à générer des prédictions. Le calcul des scores est également appelé « inférence ». Selon le type de modèle, le score peut être une valeur brute, une probabilité ou une catégorie.

## <a name="supervised-machine-learning"></a>Apprentissage automatique supervisé

Une sous-classe d’apprentissage automatique dans laquelle un modèle souhaité prévoit l’étiquette pour les données encore invisibles. Exemples : classification, régression et prédiction structurée. Pour plus d’informations, consultez l’article Wikipédia [Apprentissage supervisé](https://en.wikipedia.org/wiki/Supervised_learning).

## <a name="training"></a>Entrainement

Le processus d’identification d’un [modèle](#model) pour un jeu de données d’apprentissage spécifique. Pour un modèle linéaire, cela signifie rechercher les pondérations. Pour un arbre, cette opération implique l’identification des points de fractionnement.

## <a name="transformer"></a>Transformateur

Classe ML.NET qui implémente l’interface <xref:Microsoft.ML.ITransformer>.

Un transformateur transforme un <xref:Microsoft.ML.IDataView> en un autre. Un transformateur est créé par l’entraînement d’un [estimateur](#estimator) ou d’un pipeline d’estimateurs.

## <a name="unsupervised-machine-learning"></a>Apprentissage automatique non supervisé

Une sous-classe d’apprentissage automatique dans laquelle un modèle souhaité trouve une structure masquée (ou latente) dans les données. Exemples : clustering, modélisation de rubrique et réduction de dimensionnalité. Pour plus d’informations, consultez l’article Wikipédia [Apprentissage non supervisé](https://en.wikipedia.org/wiki/Unsupervised_learning).
