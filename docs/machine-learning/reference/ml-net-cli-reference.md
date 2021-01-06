---
title: Informations de référence sur les commandes CLI ML.NET
description: Vue d’ensemble, exemples et informations de référence sur la commande auto-train dans l’outil CLI ML.NET.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 6f07cd8b4237f8931bbc0ec97bc0bbe18c488f16
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856066"
---
# <a name="the-mlnet-cli-command-reference"></a>Informations de référence sur la commande CLI ML.NET

Les `classification` `regression` commandes, et `recommendation` sont les principales commandes fournies par l’outil CLI ml.net. Ces commandes vous permettent de générer des modèles ML.NET de bonne qualité pour la classification, la régression et les modèles de recommandation à l’aide d’Machine Learning automatisés (AutoML), ainsi que l’exemple de code C# pour exécuter/noter ce modèle. En outre, le code C# pour l’apprentissage du modèle est généré pour vous afin de Rechercher l’algorithme et les paramètres du modèle.

> [!NOTE]
> Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.

## <a name="overview"></a>Vue d’ensemble

Exemple d’utilisation :

```console
mlnet regression --dataset "cars.csv" --label-col price
```

Les `mlnet` commandes de tâche ml ( `classification` , `regression` et `recommendation` ) génèrent les ressources suivantes :

- Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.
- Code C# pour exécuter/noter le modèle généré.
- Code C# avec le code d’apprentissage utilisé pour générer ce modèle.

Les deux premières ressources peuvent être utilisées directement dans vos applications d’utilisateur final (ASP.NET Core application Web, services, application de bureau, etc.) pour faire des prédictions avec le modèle.

La troisième ressource, le code de formation, vous montre le code de l’API ML.NET utilisé par l’interface CLI pour former le modèle généré, ce qui vous permet d’examiner l’algorithme et les paramètres spécifiques du modèle.

## <a name="examples"></a>Exemples

La commande CLI la plus simple pour un problème de classification (AutoML déduit la majeure partie de la configuration à partir des données fournies) :

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

Autre commande CLI simple pour un problème de régression :

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

Créer et effectuer l’apprentissage d’un modèle de classification avec un jeu de données de formation, un jeu de données de test et d’autres arguments explicites de personnalisation :

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a>Options de commande

Les `mlnet` commandes de tâche ml ( `classification` , `regression` et `recommendation` ) entraînent plusieurs modèles en fonction du jeu de données fourni et des options de l’interface CLI ml.net. Ces commandes sélectionnent également le meilleur modèle, enregistrent le modèle sous forme de fichier. zip sérialisé et génèrent le code C# associé pour la notation et l’apprentissage.

### <a name="classification-options"></a>Options de classification

L’exécution `mlnet classification` de entraîne l’apprentissage d’un modèle de classification. Choisissez cette commande si vous souhaitez qu’un modèle ML classe les données dans au moins deux classes (par exemple, l’analyse des sentiments).

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a>Options de régression

L’exécution `mlnet regression` entraîne l’apprentissage d’un modèle de régression. Choisissez cette commande si vous souhaitez qu’un modèle ML prédise une valeur numérique (par exemple, la prédiction de prix).

```console
mlnet regression

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a>Options de recommandation

L’exécution `mlnet recommendation` entraîne l’apprentissage d’un modèle de recommandation.  Choisissez cette commande si vous souhaitez qu’un modèle ML recommande des éléments aux utilisateurs en fonction des évaluations (par exemple, recommandation du produit).

```console
mlnet recommendation

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

Les options d’entrée non valides entraînent l’émission par l’outil CLI d’une liste d’entrées valides et d’un message d’erreur.

## <a name="dataset"></a>Dataset

`--dataset | -d` (chaîne)

Cet argument fournit le chemin de l’une des options suivantes :

- *R : l’intégralité du fichier de jeu de données :* Si vous utilisez cette option et que l’utilisateur ne fournit pas `--test-dataset` et `--validation-dataset` , la validation croisée (RepList, etc.) ou les approches de fractionnement automatique des données sont utilisées en interne pour valider le modèle. Dans ce cas, l’utilisateur doit simplement fournir le chemin du jeu de données.

- *B : fichier de jeu de données d’apprentissage :* Si l’utilisateur fournit également des jeux de données pour la validation de modèle (à l’aide `--test-dataset` de et éventuellement `--validation-dataset` ), l' `--dataset` argument signifie uniquement que « jeu de données d’apprentissage ». Par exemple, quand vous utilisez une approche 80 %-20 % pour valider la qualité du modèle et pour obtenir des métriques de précision, le « jeu de données d’entraînement » a 80 % des données, tandis que le « jeu de données de test » a 20 % des données.

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

## <a name="label-column"></a>Colonne d'étiquette

`--label-col` (int ou String)

Avec cet argument, vous pouvez spécifier une colonne objective/Target (la variable que vous souhaitez prédire) à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).

Cet argument est utilisé pour les problèmes de *classification* et de *régression* .

## <a name="item-column"></a>Colonne d’élément

`--item-col` (int ou String)

La colonne élément contient la liste des éléments que les utilisateurs évaluent (les éléments sont recommandés pour les utilisateurs). Cette colonne peut être spécifiée à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).

Cet argument est utilisé uniquement pour la tâche de *recommandation* .

## <a name="rating-column"></a>Colonne d’évaluation

`--rating-col` (int ou String)

La colonne évaluation contient la liste des évaluations accordées aux éléments par les utilisateurs. Cette colonne peut être spécifiée à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).

Cet argument est utilisé uniquement pour la tâche de *recommandation* .

## <a name="user-column"></a>Colonne de l’utilisateur

`--user-col` (int ou String)

La colonne utilisateur contient la liste des utilisateurs qui attribuent des évaluations aux éléments. Cette colonne peut être spécifiée à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).

Cet argument est utilisé uniquement pour la tâche de *recommandation* .

## <a name="ignore-columns"></a>Ignorer les colonnes

`--ignore-columns` (chaîne)

Avec cet argument, vous pouvez ignorer des colonnes existantes dans le fichier de jeu de données afin qu’elles ne soient pas chargées et utilisées par les processus d’entraînement.

Spécifiez les noms des colonnes que vous souhaitez ignorer. Utilisez « ,  » (virgule avec espace) ou «   » (espace) pour séparer plusieurs noms de colonne. Vous pouvez utiliser des guillemets pour les noms de colonnes contenant des espaces (par exemple, "utilisateur connecté").

Exemple :

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>A un en-tête

`--has-header` (booléen)

Spécifiez si le ou les fichiers de jeu de données ont une ligne d’en-tête.
Les valeurs possibles sont les suivantes :

- `true`
- `false`

L’interface CLI ML.NET essaiera de détecter cette propriété si cet argument n’est pas spécifié par l’utilisateur.

## <a name="train-time"></a>Temps de formation

`--train-time` (chaîne)

Par défaut, la durée maximale d’exploration/formation est de 30 minutes.

Cet argument définit la durée maximale (en secondes) dont dispose le processus pour explorer plusieurs entraîneurs et configurations. La durée configurée peut être dépassée si la durée fournie est trop courte (par exemple, 2 secondes) pour une seule itération. Dans ce cas, la durée réelle est le temps nécessaire pour produire une seule configuration de modèle dans une seule itération.

La durée nécessaire pour les itérations peut varier selon la taille du jeu de données.

## <a name="cache"></a>Cache

`--cache` (chaîne)

Si vous utilisez la mise en cache, le jeu de données d’entraînement entier est chargé en mémoire.

Pour les jeux de données petits et moyens, l’utilisation du cache peut considérablement améliorer les performances d’entraînement, ce qui signifie que la durée d’entraînement peut être plus courte que quand vous n’utilisez pas de cache.

Toutefois, pour les grands jeux de données, le chargement de toutes les données en mémoire peut avoir un impact négatif dans la mesure où vous risquez de manquer de mémoire. Si vous effectuez un entraînement avec de grands fichiers de jeu de données sans utiliser de cache, ML.NET récupère des blocs de données du lecteur sous forme de flux s’il doit charger davantage de données.

Vous pouvez spécifier les valeurs suivantes :

`on`: Force l’utilisation du cache lors de l’apprentissage.
`off`: Force le cache à ne pas être utilisé lors de l’apprentissage.
`auto`: En fonction de l’heuristique AutoML, le cache est utilisé ou non. En règle générale, si vous utilisez le choix `auto`, les jeux de données petits et moyens utilisent le cache, tandis que les grands jeux de données ne l’utilisent pas.

Si vous ne spécifiez pas le paramètre `--cache`, la configuration `auto` du cache est utilisée par défaut.

## <a name="name"></a>Nom

`--name` (chaîne)

Nom de la solution ou du projet de sortie créé. Si aucun nom n’est spécifié, le nom `sample-{mltask}` est utilisé.

Le fichier de modèle ML.NET (fichier .ZIP) reçoit également le même nom.

## <a name="output-path"></a>Chemin de sortie

`--output | -o` (chaîne)

Emplacement/dossier racine où placer la sortie générée. L'emplacement par défaut est le répertoire actif.

## <a name="verbosity"></a>Commentaires

`--verbosity | -v` (chaîne)

Définit le niveau de détail de la sortie standard.

Les valeurs autorisées sont les suivantes :

- `q[uiet]`
- `m[inimal]` (par défaut)
- `diag[nostic]` (niveau d’informations de journalisation)

Par défaut, l’outil CLI doit afficher un minimum de commentaires ( `minimal` ) lorsque vous travaillez, par exemple pour mentionner qu’il fonctionne et, si possible, le temps restant ou le pourcentage de temps écoulé.

## <a name="help"></a>Aide

`-h |--help`

Affiche l’aide de la commande avec une description de chacun de ses paramètres.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour installer l’outil CLI ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Vue d’ensemble de l’interface CLI ML.NET](../automate-training-with-cli.md)
- [Didacticiel : analyser le sentiment à l’aide de l’interface CLI ML.NET](../tutorials/sentiment-analysis-cli.md)
- [Télémétrie dans la CLI ML.NET](../resources/ml-net-cli-telemetry.md)
