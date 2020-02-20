---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 05/29/2018
ms.openlocfilehash: 909815151265117395c6d8d13b4443a245c05f9e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451192"
---
# <a name="dotnet-test"></a>dotnet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.

## <a name="synopsis"></a>Synopsis

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a>Description

La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné. La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet. Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test. Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1. Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.

Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Chemin du projet de test. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

## <a name="options"></a>Options

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.

`--blame`

Exécute les tests en mode responsable. Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte. Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Active le collecteur de données pour la série de tests. Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.

`-f|--framework <FRAMEWORK>`

Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.

`--filter <EXPRESSION>`

Filtre les tests dans le projet actuel à l’aide de l’expression donnée. Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details). Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

`-h|--help`

Affiche une aide brève pour la commande.

`-l|--logger <LoggerUri/FriendlyName>`

Spécifie un enregistreur d’événements pour les résultats de tests.

`--no-build`

Ne génère pas le projet de test avant son exécution. L’indicateur `--no-restore` est également défini implicitement.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel rechercher les binaires à exécuter.

`-r|--results-directory <PATH>`

Répertoire où les résultats de test doivent être placés. Si le répertoire spécifié n’existe pas, il est créé.

`-s|--settings <SETTINGS_FILE>`

Fichier `.runsettings` à utiliser pour exécuter les tests. [Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

Répertorie tous les tests découverts dans le projet actuel.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`RunSettings arguments`

Arguments passés en tant que paramètres RunSettings pour le test. Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --). Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.

Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

Pour plus d’informations sur RunSettings, consultez [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Active le collecteur de données pour la série de tests. Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.

`-f|--framework <FRAMEWORK>`

Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.

`--filter <EXPRESSION>`

Filtre les tests dans le projet actuel à l’aide de l’expression donnée. Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details). Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

`-h|--help`

Affiche une aide brève pour la commande.

`-l|--logger <LoggerUri/FriendlyName>`

Spécifie un enregistreur d’événements pour les résultats de tests.

`--no-build`

Ne génère pas le projet de test avant son exécution. L’indicateur `--no-restore` est également défini implicitement.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel rechercher les binaires à exécuter.

`-r|--results-directory <PATH>`

Répertoire où les résultats de test doivent être placés. Si le répertoire spécifié n’existe pas, il est créé.

`-s|--settings <SETTINGS_FILE>`

Fichier `.runsettings` à utiliser pour exécuter les tests. [Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

Répertorie tous les tests découverts dans le projet actuel.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.

`-f|--framework <FRAMEWORK>`

Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.

`--filter <EXPRESSION>`

Filtre les tests dans le projet actuel à l’aide de l’expression donnée. Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details). Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

`-h|--help`

Affiche une aide brève pour la commande.

`-l|--logger <LoggerUri/FriendlyName>`

Spécifie un enregistreur d’événements pour les résultats de tests.

`--no-build`

Ne génère pas le projet de test avant son exécution.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel rechercher les binaires à exécuter.

`-s|--settings <SETTINGS_FILE>`

Fichier `.runsettings` à utiliser pour exécuter les tests. [Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

Répertorie tous les tests découverts dans le projet actuel.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

---

## <a name="examples"></a>Exemples

Exécutez les tests du projet dans le répertoire actif :

`dotnet test`

Exécuter les tests dans le projet `test1` :

`dotnet test ~/projects/test1/test1.csproj`

Exécutez les tests du projet dans le répertoire actif et générez un fichier de résultats des tests au format trx :

`dotnet test --logger trx`

## <a name="filter-option-details"></a>Détails de l’option de filtre

`--filter <EXPRESSION>`

`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.

`<property>` est un attribut de `Test Case`. Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :

| Infrastructure de test | Propriétés prises en charge                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Name</li><li>ClassName</li><li>Priority</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Caractéristiques</li></ul>                                   |

La section `<operator>` décrit la relation entre la propriété et la valeur :

| Opérateur | Fonction        |
| :------: | --------------- |
| `=`      | Concordance exacte     |
| `!=`     | Pas de correspondance exacte |
| `~`      | Contient        |
| `!~`     | Ne contient pas    |

`<value>` est une chaîne. Toutes les recherches respectent la casse.

Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).

Les expressions peuvent être associées à des opérateurs conditionnels :

| Opérateur            | Fonction |
| ------------------- | -------- |
| <code>&#124;</code> | OR       |
| `&`                 | AND      |

Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).

Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Voir aussi

- [Infrastructures et cibles](../../standard/frameworks.md)
- [Catalogue d’identificateurs de runtime (RID) .NET Core](../rid-catalog.md)
