---
title: Automatiser l’entraînement du modèle avec l’interface CLI ML.NET
description: Découvrez comment utiliser l’outil CLI ML.NET pour entraîner automatiquement le meilleur modèle à partir de la ligne de commande.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185883"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatiser l’entraînement du modèle avec l’interface CLI ML.NET

Le ML.NET CLI automatise la génération de modèles pour les développeurs .NET.

Pour utiliser l’API ML.NET seule (c’est-à-dire sans l’interface CLI AutoML ML.NET), vous devez choisir un entraîneur (implémentation d’un algorithme de machine learning pour une tâche particulière) ainsi que l’ensemble des transformations de données (ingénierie des caractéristiques) à appliquer à vos données. Le pipeline optimal varie en fonction de chaque jeu de données, et choisir l’algorithme optimal parmi toutes les options possibles accroît encore la complexité. De plus, chaque algorithme est associé à un ensemble d’hyperparamètres que vous devez régler. Bref, vous pouvez passer des semaines et parfois plusieurs mois à optimiser le modèle Machine Learning pour essayer de trouver les meilleures combinaisons possibles entre l’ingénierie des caractéristiques, les algorithmes d’apprentissage et les hyperparamètres.

L’ML.NET CLI simplifie ce processus à l’aide de l’apprentissage automatique automatique (AutoML).

> [!NOTE]
> Cette rubrique fait référence à l’interface **CLI** ML.NET et au moteur **AutoML** ML.NET, qui sont actuellement en préversion et donc susceptibles d’être modifiés.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Quelle est l’interface ML.NET de la ligne de commande (CLI)?

Le ML.NET CLI est un [outil .NET Core](../core/tools/global-tools.md). Une fois installé, vous lui donnez une tâche d’apprentissage automatique et un jeu de données de formation, et il génère un modèle ML.NET, ainsi que le code C ' pour exécuter pour utiliser le modèle dans votre application.

Comme le montre le chiffre suivant, il est simple de générer un modèle ML.NET de haute qualité (fichier photo .zip modèle sérialisé) ainsi que l’échantillon de code C pour exécuter/ marquer ce modèle. Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches et des itérations sur l’algorithme et les paramètres appliqués pour ce « meilleur modèle » généré.

![Image](media/automate-training-with-cli/cli-high-level-process.png "Moteur AutoML fonctionnant à l’intérieur du ML.NET CLI")

Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.

La CLI ML.NET prend en charge les tâches de ML suivantes :

- `binary-classification`
- `multiclass-classification`
- `regression`
- À l’avenir, elle prendra d’autres tâches de machine learning comme `recommendation`, `ranking`, `anomaly-detection`, `clustering`

Exemple d'utilisation :

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
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

Lorsque vous générez un « meilleur modèle » avec l’outil CLI, vous voyez des mesures de qualité (telles que la précision et R-Squared) comme appropriées pour la tâche ML que vous ciblez.

Ici, ces mesures sont résumées groupées par la tâche ML afin que vous puissiez comprendre la qualité de votre auto-généré «meilleur modèle».

### <a name="metrics-for-binary-classification-models"></a>Métriques pour les modèles de classification binaire

La capture d’écran suivante liste les métriques des tâches ML de classification binaire pour les cinq meilleurs modèles trouvés par l’outil CLI :

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

La précision est une mesure populaire pour les problèmes de classification, mais la précision n’est pas toujours la meilleure mesure pour sélectionner le meilleur modèle à partir comme expliqué dans les références suivantes. Dans certains cas, vous aurez besoin d’évaluer la qualité de votre modèle à l’aide d’autres métriques.

Pour explorer et comprendre les mesures qui sont produites par le CLI, voir [les mesures d’évaluation pour la classification binaire](resources/metrics.md#evaluation-metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Métriques pour les modèles de classification multiclasse

La capture d’écran suivante liste les métriques des tâches ML de classification multiclasse pour les cinq meilleurs modèles trouvés par l’outil CLI :

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Pour explorer et comprendre les mesures qui sont produites par l’ICIC, voir [les mesures d’évaluation pour la classification multiclasse](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Mesures pour les modèles de régression et de recommandation

Le modèle de régression est approprié dans les cas où les différences entre les valeurs observées et les valeurs prédites du modèle sont mineures et non biaisées. La régression peut être évaluée avec des métriques spécifiques.

Vous verrez une liste similaire de mesures pour les cinq meilleurs modèles de qualité trouvés par le CLI. Cas particulier concernant une tâche ML de régression :

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Pour explorer et comprendre les mesures qui sont produites par l’ICIC, voir [les mesures d’évaluation pour la régression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour installer l’outil CLI ML.NET](how-to-guides/install-ml-net-cli.md)
- [Tutorial: Analyser le sentiment à l’aide de la ML.NET CLI](tutorials/sentiment-analysis-cli.md)
- [Informations de référence sur les commandes de la CLI ML.NET](reference/ml-net-cli-reference.md)
- [Télémétrie dans la CLI ML.NET](resources/ml-net-cli-telemetry.md)
