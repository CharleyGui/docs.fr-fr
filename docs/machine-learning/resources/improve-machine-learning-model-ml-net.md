---
title: 'Comment faire : Améliorer la précision du modèle'
description: Découvrez comment améliorer la précision du modèle
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75739575"
---
# <a name="improve-mlnet-model-accuracy"></a>Améliorer la précision du modèle ML.NET

Découvrez comment améliorer la précision de votre modèle.

## <a name="reframe-the-problem"></a>Redéfinir le problème

Parfois, l’amélioration d’un modèle peut n’avoir rien à voir avec les données ou techniques utilisées pour entraîner le modèle. En effet, il se peut simplement que la question posée ne soit pas la bonne. Envisagez d’examiner le problème sous différents angles et exploitez les données pour extraire les indicateurs latents et les relations masquées afin d’affiner la question.

## <a name="provide-more-data-samples"></a>Fournir davantage d’échantillons de données

Comme dans le cas des êtres humains, plus les algorithmes sont entraînés, plus les performances sont susceptibles de s’améliorer. Une façon d’améliorer les performances d’un modèle consiste à fournir aux algorithmes davantage d’échantillons de données d’entraînement. Plus un modèle dispose de données d’entraînement, plus il peut correctement identifier des observations.

## <a name="add-context-to-the-data"></a>Ajouter un contexte aux données

La signification d’un seul point de données peut être difficile à interpréter. La génération d’un contexte autour des points de données améliore les prises de décision des algorithmes et experts en la matière. Par exemple, le fait qu’une maison a trois chambres n’est pas en soi une bonne indication de son prix. Toutefois, si vous ajoutez le contexte et que vous savez maintenant qu’elle se trouve dans une banlieue d’une grande zone métropolitaine où l’âge moyen est de 38 ans, le revenu moyen des ménages est de 80 000 € et les écoles se trouvent dans le 20ème centile supérieur, l’algorithme a plus d’informations sur lesquelles baser ses décisions. Tout ce contexte peut être ajouté en tant qu’entrée au modèle Machine Learning sous la forme de caractéristiques.

## <a name="use-meaningful-data-and-features"></a>Utiliser des données et des caractéristiques significatives

Bien que l’ajout d’échantillons de données et de caractéristiques puisse aider à améliorer la précision du modèle, cela peut également introduire du bruit, dans la mesure où toutes les données et caractéristiques ne sont pas significatives. Ainsi, il est important de comprendre quelles sont les caractéristiques qui impactent le plus les décisions prises par l’algorithme. L’utilisation de techniques telles que PFI (Permutation Feature Importance) peut aider à identifier ces caractéristiques déterminantes, à expliquer le modèle, mais aussi à utiliser la sortie comme méthode de sélection de caractéristiques pour réduire la quantité de caractéristiques bruyantes introduites dans le processus d’entraînement.

Pour plus d’informations sur l’utilisation de PFI, voir [expliquer les prédictions du modèle en utilisant Permutation Feature Importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

## <a name="cross-validation"></a>Validation croisée

La validation croisée est une technique d’entraînement et d’évaluation de modèle qui fractionne les données en plusieurs partitions sur lesquelles elle entraîne plusieurs algorithmes. Cette technique améliore la robustesse du modèle en réservant des données à partir du processus d’entraînement. Outre améliorer les performances sur les observations invisibles, dans les environnements limités en données, cette technique peut être un outil efficace pour entraîner des modèles avec un jeu de données plus petit.

Consultez le lien suivant pour savoir [comment utiliser la validation croisée dans ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md).

## <a name="hyperparameter-tuning"></a>Optimisation des hyperparamètres

L’entraînement des modèles Machine Learning est un processus itératif et exploratoire. Par exemple, quel est le nombre optimal de clusters quand un modèle est entraîné à l’aide de l’algorithme k-moyennes ? La réponse dépend de nombreux facteurs tels que la structure des données. La recherche de ce nombre nécessiterait d’expérimenter différentes valeurs pour k, puis d’évaluer les performances afin de déterminer la meilleure valeur. La pratique de l’ajustement de ces paramètres pour rechercher un modèle optimal est appelée ajustement des hyperparamètres.

## <a name="choose-a-different-algorithm"></a>Choisir un algorithme différent

Les tâches de machine learning comme la régression et la classification contiennent diverses implémentations d’algorithmes. Il est possible que le problème que vous essayez de résoudre et que la structure de vos données ne soient pas réellement compatibles avec l’algorithme actuel. Dans ce cas, envisagez d’utiliser un algorithme différent pour votre tâche pour voir s’il apprend mieux à partir de vos données.

Le lien suivant fournit plus de [conseils sur l’algorithme à choisir](../how-to-choose-an-ml-net-algorithm.md).
