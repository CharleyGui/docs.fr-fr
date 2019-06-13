---
title: Commande auto-train dans l’outil CLI ML.NET
description: Vue d’ensemble, exemples et informations de référence sur la commande auto-train dans l’outil CLI ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: ce5994f392c492e80676b9e65ce54fe010cf03ab
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722600"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>Commande « auto-train » dans l’outil CLI ML.NET

> [!NOTE]
> Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.

La commande `auto-train` est la commande principale fournie par l’outil CLI ML.NET. Cette commande vous permet de générer un modèle ML.NET de bonne qualité (fichier .zip de modèle sérialisé) ainsi que l’exemple de code C# nécessaire pour exécuter et évaluer ce modèle. Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches sur l’algorithme et les paramètres qu’il utilise pour ce « meilleur modèle » généré.

Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.

La CLI ML.NET prend en charge les tâches de ML suivantes :

- `binary-classification`
- `multiclass-classification`
- `regression`

- À l’avenir, elle prendra d’autres tâches de machine learning comme
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Exemple d’utilisation depuis l’invite de commandes :

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

La commande `mlnet auto-train` génère les ressources suivantes :

- Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.
- Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).
- Le code C# comportant le code d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage).

Les deux premières ressources peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.

La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par la CLI pour entraîner le modèle généré. Vous pouvez ainsi savoir quels entraîneur/algorithme et hyperparamètres spécifiques ont été sélectionnés par la CLI et le moteur AutoML ML.NET.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>La commande « auto-train » utilise le moteur AutoML

L’interface CLI utilise le moteur AutoML ML.NET (package NuGet) pour rechercher intelligemment les meilleurs modèles, comme le montre le diagramme suivant :

![image](./media/ml-net-automl-working-diagram.png "Fonctionnement du moteur AutoML dans la CLI ML.NET")

Quand vous exécutez l’outil CLI ML.NET avec la commande « auto-train », il essaie de nombreuses itérations avec différents algorithmes et combinaisons de configuration.

## <a name="reference-for-auto-train-command"></a>Informations de référence sur la commande « auto-train »

## <a name="examples"></a>Exemples

Commande CLI la plus simple pour un problème de classification binaire (le moteur AutoML doit déduire la majeure partie de la configuration des données fournies) :

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Autre commande CLI simple pour un problème de régression :

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Créer et entraîner un modèle de classification binaire avec un jeu de données d’entraînement, un jeu de données de test et des arguments explicites de personnalisation supplémentaire :

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Name

`mlnet auto-train` : entraîne plusieurs modèles (« n » itérations) en fonction du jeu de données fourni, puis sélectionne le meilleur modèle, l’enregistre dans un fichier .zip sérialisé et génère le code C# associé pour l’évaluation et l’entraînement.

## <a name="synopsis"></a>Résumé

```console
> mlnet auto-train

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

Les options d’entrée non valides doivent amener l’outil CLI à émettre une liste d’entrées valides et un message d’erreur expliquant quel argument est éventuellement manquant.

## <a name="options"></a>Options

 ----------------------------------------------------------

`--task | --mltask | -T` (chaîne)

Simple chaîne fournissant le problème de ML à résoudre. Par exemple, toutes les tâches suivantes (l’interface CLI est appelée à prendre en charge toutes les tâches prises en charge dans le moteur AutoML) :

- `regression` : choisissez cette tâche si vous envisagez d’utiliser le modèle ML pour prédire une valeur numérique.
- `binary-classification` : choisissez cette tâche si le résultat du modèle ML a deux valeurs booléennes de catégorie possibles (0 ou 1).
- `multiclass-classification` : choisissez cette tâche si le résultat du modèle ML a plusieurs valeurs de catégorie possibles.

Dans les versions futures, des tâches et scénarios de ML supplémentaires tels que `recommendations`, `clustering` et `ranking` seront pris en charge.

 Une seule tâche de ML doit être fournie dans cet argument.

 ----------------------------------------------------------

`--dataset | -d` (chaîne)

Cet argument fournit le chemin de l’une des options suivantes :

- *A : le fichier de jeu de données entier :* si vous utilisez cette option et que l’utilisateur ne fournit pas `--test-dataset` et `--validation-dataset`, des approches de validation croisée (k sous-échantillon, etc.) ou de fractionnement automatisé des données sont utilisées en interne pour la validation du modèle. Dans ce cas, l’utilisateur doit simplement fournir le chemin du jeu de données.

- *B : le fichier de jeu de données d’entraînement :* si l’utilisateur fournit également des jeux de données pour la validation du modèle (à l’aide de `--test-dataset` et éventuellement de `--validation-dataset`), l’argument `--dataset` revient à avoir uniquement le jeu de données d’entraînement. Par exemple, quand vous utilisez une approche 80 %-20 % pour valider la qualité du modèle et pour obtenir des métriques de précision, le « jeu de données d’entraînement » a 80 % des données, tandis que le « jeu de données de test » a 20 % des données.

----------------------------------------------------------

`--test-dataset | -t` (chaîne)

Chemin pointant vers le fichier de jeu de données de test, par exemple lors de l’utilisation d’une approche 80 %-20 % dans le cadre de validations régulières visant à obtenir des métriques de précision.

Si vous utilisez `--test-dataset`, `--dataset` est également requis.

L’argument `--test-dataset` est facultatif, sauf si l’option --validation-dataset est utilisée. Dans ce cas, l’utilisateur doit recourir aux trois arguments.

----------------------------------------------------------

`--validation-dataset | -v` (chaîne)

Chemin pointant vers le fichier de jeu de données de validation. Le jeu de données de validation est toujours facultatif.

Si vous utilisez un `validation dataset`, le comportement doit être le suivant :

- Les arguments `test-dataset` et `--dataset` sont également requis.

- Le jeu de données `validation-dataset` est utilisé pour estimer l’erreur de prédiction pour la sélection de modèle.

- `test-dataset` est utilisé pour l’évaluation de l’erreur de généralisation du dernier modèle choisi. Dans l’idéal, le jeu de test doit être conservé dans un « coffre » et récupéré uniquement à la fin de l’analyse des données.

Quand vous utilisez un `validation dataset` ainsi que `test dataset`, la phase de validation est divisée en deux parties :

1. Dans la première partie, vous examinez simplement vos modèles et sélectionnez l’approche la plus performante en utilisant les données de validation (=validation)
2. Ensuite, vous estimez la précision de l’approche sélectionnée (= test).

Ainsi, la séparation des données peut être 80/10/10 ou 75/15/10. Par exemple :

- Le fichier `training-dataset` doit avoir 75 % des données.
- Le fichier `validation-dataset` doit avoir 15 % des données.
- Le fichier `test-dataset` doit avoir 10 % des données.

Dans tous les cas, ces pourcentages sont déterminés par l’utilisateur à l’aide de l’interface CLI, qui fournit les fichiers déjà fractionnés.

----------------------------------------------------------

`--label-column-name | -n` (chaîne)

Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant le nom de la colonne défini dans l’en-tête du jeu de données.

Cet argument est utilisé uniquement pour les tâches de ML supervisées telles qu’un *problème de classification*. Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.

----------------------------------------------------------

`--label-column-index | -i` (entier)

Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 1).

*Remarque :* Si l’utilisateur recourt également à l’argument `--label-column-name`, c’est celui-ci qui est utilisé.

Cet argument est utilisé uniquement pour une tâche de ML supervisée telle qu’un *problème de classification*. Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.

----------------------------------------------------------

`--ignore-columns | -I` (chaîne)

Avec cet argument, vous pouvez ignorer des colonnes existantes dans le fichier de jeu de données afin qu’elles ne soient pas chargées et utilisées par les processus d’entraînement.

Spécifiez les noms des colonnes que vous souhaitez ignorer. Utilisez « ,  » (virgule avec espace) ou «   » (espace) pour séparer plusieurs noms de colonne. Vous pouvez utiliser des guillemets pour les noms de colonnes contenant des espaces (par exemple, "utilisateur connecté").

Exemple :

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h` (booléen)

Spécifiez si le ou les fichiers de jeu de données ont une ligne d’en-tête.
Les valeurs possibles sont :
- `true`
- `false`

La valeur par défaut est `true` si cet argument n’est pas spécifié par l’utilisateur.

Pour que l’argument `--label-column-name` puisse être utilisé, le fichier de jeu de données doit avoir un en-tête et `--has-header` doit être défini sur `true` (paramétrage par défaut).

----------------------------------------------------------

`--max-exploration-time | -x` (chaîne)

Par défaut, la durée maximale d’exploration est de 30 minutes.

Cet argument définit la durée maximale (en secondes) dont dispose le processus pour explorer plusieurs entraîneurs et configurations. La durée configurée peut être dépassée si la durée fournie est trop courte (par exemple, 2 secondes) pour une seule itération. Dans ce cas, la durée réelle est le temps nécessaire pour produire une seule configuration de modèle dans une seule itération.

La durée nécessaire pour les itérations peut varier selon la taille du jeu de données.

----------------------------------------------------------

`--cache | -c` (chaîne)

Si vous utilisez la mise en cache, le jeu de données d’entraînement entier est chargé en mémoire.

Pour les jeux de données petits et moyens, l’utilisation du cache peut considérablement améliorer les performances d’entraînement, ce qui signifie que la durée d’entraînement peut être plus courte que quand vous n’utilisez pas de cache.

Toutefois, pour les grands jeux de données, le chargement de toutes les données en mémoire peut avoir un impact négatif dans la mesure où vous risquez de manquer de mémoire. Si vous effectuez un entraînement avec de grands fichiers de jeu de données sans utiliser de cache, ML.NET récupère des blocs de données du lecteur sous forme de flux s’il doit charger davantage de données.

Vous pouvez indiquer les valeurs suivantes :

`on`: impose l’utilisation du cache lors de l’entraînement.
`off`: impose la non-utilisation du cache lors de l’entraînement.
`auto`: selon l’heuristique du moteur AutoML, le cache est utilisé ou non. En règle générale, si vous utilisez le choix `auto`, les jeux de données petits et moyens utilisent le cache, tandis que les grands jeux de données ne l’utilisent pas.

Si vous ne spécifiez pas le paramètre `--cache`, la configuration `auto` du cache est utilisée par défaut.

----------------------------------------------------------

`--name | -N` (chaîne)

Nom de la solution ou du projet de sortie créé. Si aucun nom n’est spécifié, le nom `sample-{mltask}` est utilisé.

Le fichier de modèle ML.NET (fichier .ZIP) reçoit également le même nom.

----------------------------------------------------------

`--output-path | -o` (chaîne)

Emplacement/dossier racine où placer la sortie générée. La valeur par défaut correspond au répertoire actif.

----------------------------------------------------------

`--verbosity | -V` (chaîne)

Définit le niveau de détail de la sortie standard.

Les valeurs autorisées sont :

- `q[uiet]`
- `m[inimal]` (par défaut)
- `diag[nostic]` (niveau d’informations de journalisation)

Par défaut, l’outil CLI doit afficher un minimum de commentaires quand il fonctionne ; il doit par exemple indiquer qu’il fonctionne et, si possible, le temps restant ou le pourcentage de temps écoulé.

----------------------------------------------------------

`-h|--help`

Affiche l’aide de la commande avec une description de chacun de ses paramètres.

----------------------------------------------------------

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour installer l’outil CLI ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Automatiser l’entraînement du modèle avec la CLI ML.NET](../automate-training-with-cli.md)
- [Tutoriel : Générer automatiquement un classifieur binaire à l’aide de la CLI ML.NET](../tutorials/mlnet-cli.md)
- [Télémétrie dans la CLI ML.NET](../resources/ml-net-cli-telemetry.md)
