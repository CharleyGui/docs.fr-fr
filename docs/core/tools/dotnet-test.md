---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624889"
---
# <a name="dotnet-test"></a>dotnet test

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Description

La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné. La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet. Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test. Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1. Pour les projets multi-ciblés, les tests sont exécutés pour chaque Framework ciblé. Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.

Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Arguments

- **`PROJECT | SOLUTION`**

  Chemin d’accès au projet de test ou à la solution. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

## <a name="options"></a>Options

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.

- **`--blame`**

  Exécute les tests en mode responsable. Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test. Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Active le collecteur de données pour la série de tests. Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.

- **`-f|--framework <FRAMEWORK>`**

  Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.

- **`--filter <EXPRESSION>`**

  Filtre les tests dans le projet actuel à l’aide de l’expression donnée. Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details). Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Spécifie un enregistreur d’événements pour les résultats de tests. Contrairement à MSBuild, dotnet test n’accepte pas les abréviations `-l "console;v=d"` : `-l "console;verbosity=detailed"`au lieu d’utiliser.

- **`--no-build`**

  Ne génère pas le projet de test avant son exécution. Il définit également implicitement l’indicateur `--no-restore` -.

- **`--nologo`**

  Exécuter les tests sans afficher la bannière Microsoft TestPlatform. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--no-restore`**

  N’effectue pas de restauration implicite à l’exécution de la commande.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Répertoire dans lequel rechercher les binaires à exécuter. S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.  Pour les projets avec plusieurs frameworks cibles (via `TargetFrameworks` la propriété), vous devez également définir `--framework` lorsque vous spécifiez cette option. `dotnet test`Exécutez toujours les tests à partir du répertoire de sortie. Vous pouvez utiliser <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pour consommer des ressources de test dans le répertoire de sortie.

- **`-r|--results-directory <PATH>`**

  Répertoire où les résultats de test doivent être placés. Si le répertoire spécifié n’existe pas, il est créé. La valeur par `TestResults` défaut se trouve dans le répertoire qui contient le fichier projet.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Runtime cible à tester.

- **`-s|--settings <SETTINGS_FILE>`**

  Fichier `.runsettings` à utiliser pour exécuter les tests. Notez que l' `TargetPlatform` élément (x86 | x64) n’a aucun effet `dotnet test`pour. Pour exécuter des tests ciblant x86, installez la version x86 de .NET Core. Le nombre de bits de *dotnet. exe* qui se trouve sur le chemin d’accès correspond à ce qui sera utilisé pour l’exécution des tests. Pour plus d’informations, consultez les ressources suivantes :

  - [Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Configurer une série de tests](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Répertorie tous les tests découverts dans le projet actuel.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Par défaut, il s’agit de `minimal`. Pour plus d’informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** arguments

  Les arguments sont passés `RunSettings` comme configurations pour le test. Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --). Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.

  Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Pour plus d’informations, consultez [transmission d’arguments RunSettings via la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Exemples

- Exécutez les tests du projet dans le répertoire actif :

  ```dotnetcli
  dotnet test
  ```

- Exécuter les tests dans le projet `test1` :

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de résultats de test au format trx :

  ```dotnetcli
  dotnet test --logger trx
  ```

- Exécutez les tests dans le projet dans le répertoire actif, puis consignez des commentaires détaillés sur la console :

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a>Détails de l’option de filtre

`--filter <EXPRESSION>`

`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.

`<property>` est un attribut de `Test Case`. Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :

| Framework de test | Propriétés prises en charge                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nom</li><li>ClassName</li><li>Priority</li><li>TestCategory</li></ul> |
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

Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Voir aussi

- [Infrastructures et cibles](../../standard/frameworks.md)
- [Catalogue d’identificateurs de runtime (RID) .NET Core](../rid-catalog.md)
- [Passage d’arguments RunSettings via la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
