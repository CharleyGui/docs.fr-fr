---
title: Automatiser l’entraînement du modèle avec l’interface CLI ML.NET
description: Découvrez comment utiliser l’outil CLI ML.NET pour entraîner automatiquement le meilleur modèle à partir de la ligne de commande.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663924"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatiser l’entraînement du modèle avec l’interface CLI ML.NET

L’interface CLI ML.NET « démocratise » ML.NET auprès des développeurs .NET qui débutent avec ML.NET.

Pour utiliser l’API ML.NET seule (c’est-à-dire sans l’interface CLI AutoML ML.NET), vous devez choisir un entraîneur (implémentation d’un algorithme de machine learning pour une tâche particulière) ainsi que l’ensemble des transformations de données (ingénierie des caractéristiques) à appliquer à vos données. Le pipeline optimal varie en fonction de chaque jeu de données, et choisir l’algorithme optimal parmi toutes les options possibles accroît encore la complexité. De plus, chaque algorithme est associé à un ensemble d’hyperparamètres que vous devez régler. Bref, vous pouvez passer des semaines et parfois plusieurs mois à optimiser le modèle Machine Learning pour essayer de trouver les meilleures combinaisons possibles entre l’ingénierie des caractéristiques, les algorithmes d’apprentissage et les hyperparamètres.

Heureusement, ce processus peut être automatisé avec l’interface CLI ML.NET, qui implémente le moteur intelligent AutoML ML.NET.

> [!NOTE]
> Cette rubrique fait référence à l’interface **CLI** ML.NET et au moteur **AutoML** ML.NET, qui sont actuellement en préversion et donc susceptibles d’être modifiés.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Présentation de l’interface CLI ML.NET

Vous pouvez exécuter l’interface CLI ML.NET à partir de n’importe quelle invite de commandes (Windows, Mac ou Linux) et générer ensuite des modèles ML.NET et du code source de qualité sur la base de votre jeu de données d’entraînement.

Comme le montre l’illustration ci-dessous, vous pouvez facilement générer un modèle ML.NET de grande qualité (fichier .zip de modèle sérialisé) ainsi que le code C# nécessaire pour exécuter et évaluer ce modèle. Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches et des itérations sur l’algorithme et les paramètres appliqués pour ce « meilleur modèle » généré.

![image](media/automate-training-with-cli/cli-high-level-process.png "Fonctionnement du moteur AutoML dans la CLI ML.NET")

Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.

Actuellement, l’interface CLI ML.NET prend en charge les tâches ML suivantes :

- `binary-classification`
- `multiclass-classification`
- `regression`
- À l’avenir, elle prendra d’autres tâches de machine learning comme `recommendation`, `ranking`, `anomaly-detection`, `clustering`

Exemple d’utilisation :

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

Vous pouvez exécuter cette commande de la même façon sur *Windows PowerShell*, *macOS/Linux Bash ou *Windows CMD*. Toutefois, l’autocomplétion via la touche tab (suggestions de paramètres) ne fonctionne pas sur *Windows CMD*.

## <a name="output-assets-generated"></a>Ressources générées en sortie

La commande `auto-train` de l’interface CLI génère les ressources suivantes dans le dossier de sortie :

- Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé pour effectuer des prédictions.
- Une solution C# contenant :
  - Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).
  - Le code C# avec le code d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage ou de réentraînement du modèle).
- Un fichier journal contenant des informations sur l’ensemble des itérations/balayages effectués sur tous les algorithmes évalués, y compris les détails de leur pipeline/configuration.

Les deux premières ressources peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.

La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par l’interface CLI pour entraîner le modèle généré. Vous pouvez alors réentraîner votre modèle et effectuer des recherches/itérations sur l’entraîneur/algorithme et les hyperparamètres spécifiques qui avaient été automatiquement sélectionnés par l’interface CLI et AutoML.

## <a name="understanding-the-quality-of-the-model"></a>Déterminer la qualité du modèle

Quand vous générez un « meilleur modèle » avec l’outil CLI, vous voyez des métriques de qualité (telles que la précision et le coefficient de détermination) relatives à la tâche ML que vous ciblez.

Nous récapitulons ci-après toutes ces métriques par type de tâche ML, qui vous permettront de déterminer la qualité de votre « meilleur modèle » généré automatiquement.

### <a name="metrics-for-binary-classification-models"></a>Métriques pour les modèles de classification binaire

La capture d’écran suivante liste les métriques des tâches ML de classification binaire pour les cinq meilleurs modèles trouvés par l’outil CLI :

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

La précision (Accuracy) est une métrique couramment employée pour les problèmes de classification, mais elle ne constitue pas toujours la métrique la plus adaptée pour choisir le meilleur modèle, comme cela est expliqué dans la rubrique indiquée ci-dessous. Dans certains cas, vous aurez besoin d’évaluer la qualité de votre modèle à l’aide d’autres métriques.

Pour explorer et comprendre toutes les métriques fournies par l’outil CLI, consultez [Métriques pour la classification binaire](resources/metrics.md#metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Métriques pour les modèles de classification multiclasse

La capture d’écran suivante liste les métriques des tâches ML de classification multiclasse pour les cinq meilleurs modèles trouvés par l’outil CLI :

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Pour explorer et comprendre toutes les métriques fournies par l’outil CLI, consultez [Métriques pour la classification multiclasse](resources/metrics.md#metrics-for-multi-class-classification).

### <a name="metrics-for-regression-models"></a>Métriques pour les modèles de régression

Le modèle de régression est approprié dans les cas où les différences entre les valeurs observées et les valeurs prédites du modèle sont mineures et non biaisées. La régression peut être évaluée avec des métriques spécifiques.

Vous verrez une liste similaire de métriques pour les cinq meilleurs modèles trouvés par l’outil CLI. Cas particulier concernant une tâche ML de régression :

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Pour explorer et comprendre toutes les métriques fournies par l’outil CLI, consultez [Métriques pour la régression](resources/metrics.md#metrics-for-regression).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour installer l’outil CLI ML.NET](how-to-guides/install-ml-net-cli.md)
- [Tutoriel : Générer automatiquement un classifieur binaire à l’aide de la CLI ML.NET](tutorials/mlnet-cli.md)
- [Informations de référence sur les commandes de la CLI ML.NET](reference/ml-net-cli-reference.md)
- [Télémétrie dans la CLI ML.NET](resources/ml-net-cli-telemetry.md)
