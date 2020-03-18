---
title: ML.NET référence de commande de l’OPC
description: Vue d’ensemble, exemples et informations de référence sur la commande auto-train dans l’outil CLI ML.NET.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848923"
---
# <a name="the-mlnet-cli-command-reference"></a>La référence de commande ML.NET CLI

La commande `auto-train` est la commande principale fournie par l’outil CLI ML.NET. La commande vous permet de générer un modèle ML.NET de bonne qualité à l’aide de l’apprentissage automatique automatique (AutoML) ainsi que l’exemple de code C pour exécuter / marquer ce modèle. En outre, le code C pour former le modèle est généré pour vous de rechercher l’algorithme et les paramètres du modèle.

> [!NOTE]
> Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.

## <a name="overview"></a>Vue d’ensemble

Exemple d’utilisation :

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

La commande `mlnet auto-train` génère les ressources suivantes :

- Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.
- Code C POUR exécuter/score qui a généré le modèle.
- Code C avec le code de formation utilisé pour générer ce modèle.

Les deux premiers actifs peuvent être directement utilisés dans vos applications utilisateur final (ASP.NET’application Web Core, services, application de bureau et plus) pour faire des prédictions avec le modèle.

Le troisième actif, le code de formation, vous montre ce que ML.NET code API a été utilisé par le CLI pour former le modèle généré, afin que vous puissiez étudier l’algorithme spécifique et les paramètres du modèle.

## <a name="examples"></a>Exemples

La commande CLI la plus simple pour un problème de classification binaire (AutoML déduit la plupart de la configuration à partir des données fournies) :

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Autre commande CLI simple pour un problème de régression :

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Créer et entraîner un modèle de classification binaire avec un jeu de données d’entraînement, un jeu de données de test et des arguments explicites de personnalisation supplémentaire :

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Options de commande

`mlnet auto-train`forme plusieurs modèles en fonction de l’ensemble de données fourni et sélectionne enfin le meilleur modèle, l’enregistre comme un fichier .zip sérialisé plus génère le code C ' connexe pour la notation et la formation.

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

Les options d’entrée invalides font émettre à l’outil CLI une liste d’entrées valides et un message d’erreur.

## <a name="task"></a>Tâche

`--task | --mltask | -T` (chaîne)

Simple chaîne fournissant le problème de ML à résoudre. Par exemple, toutes les tâches suivantes (l’interface CLI est appelée à prendre en charge toutes les tâches prises en charge dans le moteur AutoML) :

- `regression` : choisissez cette tâche si vous envisagez d’utiliser le modèle ML pour prédire une valeur numérique.
- `binary-classification` : choisissez cette tâche si le résultat du modèle ML a deux valeurs booléennes de catégorie possibles (0 ou 1).
- `multiclass-classification` : choisissez cette tâche si le résultat du modèle ML a plusieurs valeurs de catégorie possibles.

Une seule tâche de ML doit être fournie dans cet argument.

## <a name="dataset"></a>Dataset

`--dataset | -d` (chaîne)

Cet argument fournit le chemin de l’une des options suivantes :

- *R: L’ensemble du fichier de jeu de données:* Si l’utilisation de cette `--test-dataset` option `--validation-dataset`et l’utilisateur ne fournit pas et, puis la validation croisée (k-fold, etc) ou automatisées approches de fractionnement de données seront utilisés en interne pour valider le modèle. Dans ce cas, l’utilisateur doit simplement fournir le chemin du jeu de données.

- *B : Le fichier de données de formation :* Si l’utilisateur fournit également des jeux `--test-dataset` de données `--validation-dataset`pour `--dataset` la validation du modèle (en utilisant et en option), alors l’argument signifie d’avoir uniquement le "jeu de données de formation". Par exemple, quand vous utilisez une approche 80 %-20 % pour valider la qualité du modèle et pour obtenir des métriques de précision, le « jeu de données d’entraînement » a 80 % des données, tandis que le « jeu de données de test » a 20 % des données.

## <a name="test-dataset"></a>Jeu de données de test

`--test-dataset | -t` (chaîne)

Chemin pointant vers le fichier de jeu de données de test, par exemple lors de l’utilisation d’une approche 80 %-20 % dans le cadre de validations régulières visant à obtenir des métriques de précision.

Si vous utilisez `--test-dataset`, `--dataset` est également requis.

L’argument `--test-dataset` est facultatif, sauf si l’option --validation-dataset est utilisée. Dans ce cas, l’utilisateur doit recourir aux trois arguments.

## <a name="validation-dataset"></a>Jeu de données de validation

`--validation-dataset | -v` (chaîne)

Chemin pointant vers le fichier de jeu de données de validation. Le jeu de données de validation est toujours facultatif.

Si vous utilisez un `validation dataset`, le comportement doit être le suivant :

- Les arguments `test-dataset` et `--dataset` sont également requis.

- Le jeu de données `validation-dataset` est utilisé pour estimer l’erreur de prédiction pour la sélection de modèle.

- `test-dataset` est utilisé pour l’évaluation de l’erreur de généralisation du dernier modèle choisi. Dans l’idéal, le jeu de test doit être conservé dans un « coffre » et récupéré uniquement à la fin de l’analyse des données.

Quand vous utilisez un `validation dataset` ainsi que `test dataset`, la phase de validation est divisée en deux parties :

1. Dans la première partie, vous examinez simplement vos modèles et sélectionnez l’approche la plus performante en utilisant les données de validation (=validation)
2. Ensuite, vous estimez la précision de l’approche sélectionnée (= test).

Ainsi, la séparation des données peut être 80/10/10 ou 75/15/10. Par exemple :

- Le fichier `training-dataset` doit avoir 75 % des données.
- Le fichier `validation-dataset` doit avoir 15 % des données.
- Le fichier `test-dataset` doit avoir 10 % des données.

Dans tous les cas, ces pourcentages sont déterminés par l’utilisateur à l’aide de l’interface CLI, qui fournit les fichiers déjà fractionnés.

## <a name="label-column-name"></a>Nom de colonne d’étiquette

`--label-column-name | -n` (chaîne)

Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant le nom de la colonne défini dans l’en-tête du jeu de données.

Cet argument est utilisé uniquement pour les tâches de ML supervisées telles qu’un *problème de classification*. Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.

## <a name="label-column-index"></a>Indice de colonne d’étiquette

`--label-column-index | -i` (entier)

Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 1).

*Note:* Si l’utilisateur utilise `--label-column-name`également `--label-column-name` le , c’est celui qui est utilisé.

Cet argument est utilisé uniquement pour une tâche de ML supervisée telle qu’un *problème de classification*. Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.

## <a name="ignore-columns"></a>Ignorer les colonnes

`--ignore-columns | -I` (chaîne)

Avec cet argument, vous pouvez ignorer des colonnes existantes dans le fichier de jeu de données afin qu’elles ne soient pas chargées et utilisées par les processus d’entraînement.

Spécifiez les noms des colonnes que vous souhaitez ignorer. Utilisez « ,  » (virgule avec espace) ou «   » (espace) pour séparer plusieurs noms de colonne. Vous pouvez utiliser des guillemets pour les noms de colonnes contenant des espaces (par exemple, "utilisateur connecté").

Exemple :

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>A en-tête

`--has-header | -h` (booléen)

Spécifiez si le ou les fichiers de jeu de données ont une ligne d’en-tête.
Les valeurs possibles sont les suivantes :

- `true`
- `false`

La valeur par défaut est `true` si cet argument n’est pas spécifié par l’utilisateur.

Pour que l’argument `--label-column-name` puisse être utilisé, le fichier de jeu de données doit avoir un en-tête et `--has-header` doit être défini sur `true` (paramétrage par défaut).

## <a name="max-exploration-time"></a>Temps d’exploration maximum

`--max-exploration-time | -x` (chaîne)

Par défaut, la durée maximale d’exploration est de 30 minutes.

Cet argument définit la durée maximale (en secondes) dont dispose le processus pour explorer plusieurs entraîneurs et configurations. La durée configurée peut être dépassée si la durée fournie est trop courte (par exemple, 2 secondes) pour une seule itération. Dans ce cas, la durée réelle est le temps nécessaire pour produire une seule configuration de modèle dans une seule itération.

La durée nécessaire pour les itérations peut varier selon la taille du jeu de données.

## <a name="cache"></a>Cache

`--cache | -c` (chaîne)

Si vous utilisez la mise en cache, le jeu de données d’entraînement entier est chargé en mémoire.

Pour les jeux de données petits et moyens, l’utilisation du cache peut considérablement améliorer les performances d’entraînement, ce qui signifie que la durée d’entraînement peut être plus courte que quand vous n’utilisez pas de cache.

Toutefois, pour les grands jeux de données, le chargement de toutes les données en mémoire peut avoir un impact négatif dans la mesure où vous risquez de manquer de mémoire. Si vous effectuez un entraînement avec de grands fichiers de jeu de données sans utiliser de cache, ML.NET récupère des blocs de données du lecteur sous forme de flux s’il doit charger davantage de données.

Vous pouvez spécifier les valeurs suivantes :

`on`: Force cache à utiliser lors de l’entraînement.
`off`: Force cache de ne pas être utilisé lors de l’entraînement.
`auto`: Selon l’heuristique AutoML, le cache sera utilisé ou non. En règle générale, si vous utilisez le choix `auto`, les jeux de données petits et moyens utilisent le cache, tandis que les grands jeux de données ne l’utilisent pas.

Si vous ne spécifiez pas le paramètre `--cache`, la configuration `auto` du cache est utilisée par défaut.

## <a name="name"></a>Nom

`--name | -N` (chaîne)

Nom de la solution ou du projet de sortie créé. Si aucun nom n’est spécifié, le nom `sample-{mltask}` est utilisé.

Le fichier de modèle ML.NET (fichier .ZIP) reçoit également le même nom.

## <a name="output-path"></a>Chemin de sortie

`--output-path | -o` (chaîne)

Emplacement/dossier racine où placer la sortie générée. L'emplacement par défaut est le répertoire actif.

## <a name="verbosity"></a>Commentaires

`--verbosity | -V` (chaîne)

Définit le niveau de détail de la sortie standard.

Les valeurs autorisées sont les suivantes :

- `q[uiet]`
- `m[inimal]` (par défaut)
- `diag[nostic]` (niveau d’informations de journalisation)

Par défaut, l’outil CLI doit afficher un minimum de commentaires quand il fonctionne ; il doit par exemple indiquer qu’il fonctionne et, si possible, le temps restant ou le pourcentage de temps écoulé.

## <a name="help"></a>Aide

`-h|--help`

Affiche l’aide de la commande avec une description de chacun de ses paramètres.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour installer l’outil CLI ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Aperçu du ML.NET CLI](../automate-training-with-cli.md)
- [Tutorial: Analyser le sentiment à l’aide de la ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [Télémétrie dans la CLI ML.NET](../resources/ml-net-cli-telemetry.md)
