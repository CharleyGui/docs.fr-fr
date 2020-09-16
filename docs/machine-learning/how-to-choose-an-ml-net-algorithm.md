---
title: Guide pratique pour choisir un algorithme ML.NET
description: Découvrez comment choisir un algorithme ML.NET pour votre modèle Machine Learning
ms.topic: overview
ms.date: 06/05/2019
ms.openlocfilehash: 8af89800485f8f8ac35ee17df10a5e3c039da42d
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679636"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>Guide pratique pour choisir un algorithme ML.NET

Pour chaque [tâche ML.NET](resources/tasks.md), il existe plusieurs algorithmes d’entraînement possibles. Le choix de l’algorithme dépend du problème que vous essayez de résoudre, des caractéristiques de vos données ainsi que des ressources de calcul et de stockage à votre disposition. Il est important de savoir que l’entraînement d’un modèle Machine Learning est un processus itératif. Vous devrez peut-être essayer plusieurs algorithmes avant de trouver celui qui marche le mieux.

Les algorithmes fonctionnent avec des **caractéristiques**. Les caractéristiques sont des valeurs numériques calculées à partir de vos données d’entrée. Elles constituent des entrées optimales pour les algorithmes de machine learning. Vous transformez vos données d’entrée brutes en caractéristiques par le biais d’une ou de plusieurs [transformations de données](resources/transforms.md). Par exemple, les données texte sont transformées en un certain nombre de mots et de combinaisons de mots. Une fois que les caractéristiques ont été extraites d’un type de données brutes à l’aide de transformations de données, elles sont dites **caractérisées**. Par exemple, du texte caractérisé ou des données image caractérisées.

## <a name="trainer--algorithm--task"></a>Entraîneur = algorithme + tâche

Un algorithme est une opération mathématique qui s’exécute pour produire un **modèle**. Différents algorithmes produisent des modèles avec des caractéristiques différentes.

Avec ML.NET, il est possible d’appliquer le même algorithme à différentes tâches. Par exemple, l’algorithme Stochastic Dual Coordinated Ascent peut s’appliquer aux tâches de classification binaire, de classification multiclasse et de régression. Le changement se trouve dans l’interprétation de la sortie de l’algorithme par rapport à la tâche.

Pour chaque combinaison algorithme/tâche, ML.NET fournit un composant qui exécute l’algorithme d’entraînement et interprète la sortie. Ces composants sont appelés des « entraîneurs ». Par exemple, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> utilise l’algorithme **StochasticDualCoordinatedAscent** appliqué à la tâche de **régression**.

## <a name="linear-algorithms"></a>Algorithmes linéaires

Les algorithmes linéaires produisent un modèle qui calcule des **scores** à partir d’une combinaison linéaire des données d’entrée et d’un ensemble de **pondérations**. Les pondérations sont des paramètres du modèle qui sont évalués au moment de l’entraînement.

Les algorithmes linéaires fonctionnent bien avec des caractéristiques [séparables de façon linéaire](https://en.wikipedia.org/wiki/Linear_separability).

Préalablement à l’entraînement avec un algorithme linéaire, les caractéristiques doivent être normalisées. Cela évite qu’une caractéristique ait plus d’influence que les autres sur le résultat.

En général, les algorithmes linéaires sont scalables, rapides à exécuter, et peu coûteux à entraîner et à prédire. Ils s’adaptent selon le nombre de caractéristiques et approximativement selon la taille du jeu de données d’entraînement.

Les algorithmes linéaires font plusieurs passages sur les données d’entraînement. Si votre jeu de données tient en mémoire, l’ajout d’un [point de contrôle du cache](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) à votre pipeline ML.NET avant d’ajouter l’entraîneur accélère le processus d’entraînement.

**Entraîneurs linéaires**

|Algorithm|Propriétés|Entraîneurs|
|---------|----------|--------|
|Averaged perceptron|Idéal pour la classification de texte|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stochastic Dual coordinated ascent|Performances par défaut satisfaisantes sans réglage nécessaire|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|À utiliser quand il y a beaucoup de caractéristiques. Génère des statistiques sur l’entraînement de régression logistique, mais est moins scalable que l’algorithme AveragedPerceptronTrainer|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Symbolic stochastic gradient descent|Entraîneur de classification binaire linéaire le plus rapide et le plus précis. S’adapte bien à divers processeurs|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Algorithmes d’arbre de décision

Les algorithmes d’arbre de décision créent un modèle qui contient une série de décisions : en réalité, c’est un organigramme de valeurs de données.

Les caractéristiques n’ont pas besoin d’être séparables de façon linéaire pour utiliser ce type d’algorithme. Elles n’ont pas non plus besoin d’être normalisées, car chaque valeur dans le vecteur de caractéristiques est utilisée indépendamment dans le processus de décision.

Les algorithmes d’arbre de décision sont généralement très précis.

À l’exception des modèles additifs généralisés, les modèles d’arbre sont parfois moins explicables quand le nombre de caractéristiques est élevé.

Les algorithmes d’arbre de décision consomment davantage de ressources et ne s’adaptent pas aussi bien que les algorithmes linéaires. Ils donnent de bons résultats sur les jeux de données tenant en mémoire.

Les arbres de décision boostés sont un ensemble de petits arbres où chaque arbre évalue les données d’entrée, puis passe le score à l’arbre suivant pour produire un meilleur score, et ainsi de suite. Chaque arbre de l’ensemble représente une amélioration par rapport à l’arbre précédent.

**Entraîneurs d’arbre de décision**

|Algorithm|Propriétés|Entraîneurs|
|---------|----------|--------|
|Light gradient boosted machine|Entraîneur d’arbre de classification binaire le plus rapide et le plus précis. Hautement réglable|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Fast tree|À utiliser pour les données d’image caractérisées. Résilient aux données non équilibrées. Hautement réglable | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Fast forest|Fonctionne bien avec les données bruyantes|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|GAM (modèle additif généralisé)|Idéal pour les problèmes avec des algorithmes d’arbre où l’explicabilité est une priorité|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Factorisation de matrice

|Propriétés|Entraîneurs|
|----------|--------|
|Idéal pour les données de catégories éparses, dans des jeux de données volumineux|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Méta-algorithmes

Ces entraîneurs créent un entraîneur multiclasse à partir d’un entraîneur binaire. À utiliser avec <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.

|Algorithm|Propriétés|Entraîneurs|
|---------|----------|--------|
|One versus all|Ce classifieur multiclasse entraîne un seul classifieur binaire par classe, ce qui distingue cette classe de toutes les autres classes. Adaptation limitée selon le nombre de classes à catégoriser|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Pairwise coupling|Ce classifieur multiclasse entraîne un algorithme de classification binaire sur chaque paire de classes. Adaptation limitée selon le nombre de classes, du fait que chaque combinaison de deux classes doit être entraînée.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-Means

|Propriétés|Entraîneurs|
|----------|--------|
|À utiliser pour le clustering|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Principal Component Analysis (PCA)

|Propriétés|Entraîneurs|
|----------|--------|
|À utiliser pour la détection d’anomalie|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Naive Bayes

|Propriétés|Entraîneurs|
|----------|--------|
|Cet entraîneur de classification multiclasse s’utilise avec des caractéristiques indépendantes et un petit jeu de données d’entraînement.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Prior Trainer

|Propriétés|Entraîneurs|
|----------|--------|
|Cet entraîneur de classification binaire s’utilise comme base de référence des performances des autres entraîneurs. Pour être efficace, les métriques des autres entraîneurs doivent être meilleures que l’entraîneur précédent. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
