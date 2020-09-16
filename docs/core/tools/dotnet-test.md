---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 04/29/2020
ms.openlocfilehash: 5ecfa24905537a663cd967142b765c258495fb22
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537733"
---
# <a name="dotnet-test"></a>dotnet test

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Name

`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Description

La `dotnet test` commande est utilisée pour exécuter des tests unitaires dans une solution donnée. La `dotnet test` commande génère la solution et exécute une application hôte de test pour chaque projet de test de la solution. L’hôte de test exécute des tests dans le projet donné à l’aide d’une infrastructure de test, par exemple, MSTest, NUnit ou xUnit, et signale la réussite ou l’échec de chaque test. Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.

Pour les projets multi-ciblés, les tests sont exécutés pour chaque Framework ciblé. L’hôte de test et l’infrastructure de tests unitaires sont empaquetés en tant que packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.

Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

Où `Microsoft.NET.Test.Sdk` est l’hôte de test, `xunit` est l’infrastructure de test. Et `xunit.runner.visualstudio` est un adaptateur de test, qui permet à l’infrastructure xUnit de fonctionner avec l’hôte de test.

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Arguments

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - Chemin du projet de test.
  - Chemin d’accès à la solution.
  - Chemin d’accès à un répertoire qui contient un projet ou une solution.
  - Chemin d’accès à un fichier *. dll* de projet de test.

  S’il n’est pas spécifié, il recherche un projet ou une solution dans le répertoire actif.

## <a name="options"></a>Options

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  Chemin d’accès à un répertoire dans lequel rechercher d’autres adaptateurs de test. Seuls les fichiers *. dll* avec suffixe `.TestAdapter.dll` sont inspectés. S’il n’est pas spécifié, la recherche s’effectue dans le répertoire du *fichier test. dll* .

- **`--blame`**

  Exécute les tests en mode responsable. Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test. Lorsqu’un incident est détecté, il crée un fichier de séquence dans `TestResults/<Guid>/<Guid>_Sequence.xml` qui capture l’ordre des tests qui ont été exécutés avant l’incident.

- **`--blame-crash`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)

  Exécute les tests en mode de responsabilité et collecte un vidage sur incident lorsque l’hôte de test s’arrête de manière inattendue. Cette option est uniquement prise en charge sur Windows. Un répertoire qui contient *procdump.exe* et *procdump64.exe* doit se trouver dans la variable d’environnement PATH ou PROCDUMP_PATH. [Téléchargez les outils](/sysinternals/downloads/procdump). Implique `--blame` .

- **`--blame-crash-dump-type <DUMP_TYPE>`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)

  Type de vidage sur incident à collecter. Implique `--blame-crash` .

- **`--blame-crash-collect-always`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)

  Collecte un vidage sur incident sur la sortie attendue et sur l’hôte de test inattendu.

- **`--blame-hang`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)

  Exécuter les tests en mode de responsabilité et collecter un vidage sur le blocage quand un test dépasse le délai d’attente donné.

- **`--blame-hang-dump-type <DUMP_TYPE>`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)

  Type de vidage sur incident à collecter. Il doit s’agir `full` de, `mini` ou `none` . Lorsque `none` est spécifié, l’hôte de test se termine à l’expiration du délai d’attente, mais aucun vidage n’est collecté. Implique `--blame-hang` .

- **`--blame-hang-timeout <TIMESPAN>`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)

  Délai d’attente par test, après lequel un vidage sur le blocage est déclenché et le processus hôte de test est terminé. La valeur du délai d’attente est spécifiée dans l’un des formats suivants :
  
  - 1.5 h
  - 90m
  - 5400
  - 5400000ms

  Quand aucune unité n’est utilisée (par exemple, 5,4 millions), la valeur est supposée être en millisecondes. Lorsqu’il est utilisé avec les tests pilotés par les données, le comportement du délai d’attente dépend de l’adaptateur de test utilisé. Pour xUnit et NUnit, le délai d’attente est renouvelé après chaque cas de test. Pour MSTest, le délai d’attente est utilisé pour tous les cas de test. Cette option est prise en charge sur Windows avec netcoreapp 2.1 et versions ultérieures, et sur Linux avec netcoreapp 3.1 et versions ultérieures. macOS n’est pas pris en charge.

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

- **`--collect <DATA_COLLECTOR_NAME>`**

  Active le collecteur de données pour la série de tests. Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).
  
  Pour collecter la couverture du code sur toutes les plateformes prises en charge par .NET Core, installez [coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) et utilisez l' `--collect:"XPlat Code Coverage"` option.

  Sur Windows, vous pouvez collecter la couverture du code à l’aide de l' `--collect "Code Coverage"` option. Cette option génère un fichier *. coverage* , qui peut être ouvert dans Visual Studio 2019 Enterprise. Pour plus d’informations, consultez Utilisation de la [couverture du code](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) et personnalisation de l’analyse de la [couverture du code](/visualstudio/test/customizing-code-coverage-analysis).

- **`-d|--diag <LOG_FILE>`**

  Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié et dans des fichiers à côté de celui-ci. Le processus d’enregistrement des messages détermine quels fichiers sont créés, par exemple `*.host_<date>.txt` pour le journal de l’hôte de test et `*.datacollector_<date>.txt` pour le journal du collecteur de données.

- **`-f|--framework <FRAMEWORK>`**

  Force l’utilisation de `dotnet` ou .NET Framework hôte de test pour les binaires de test. Cette option détermine uniquement le type d’hôte à utiliser. La version de .NET Framework à utiliser est déterminée par le *runtimeconfig.js* du projet de test. Lorsqu’il n’est pas spécifié, l' [attribut d’assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) est utilisé pour déterminer le type d’hôte. Lorsque cet attribut est supprimé du *fichier. dll*, l’hôte .NET Framework est utilisé.

- **`--filter <EXPRESSION>`**

  Filtre les tests dans le projet actuel à l’aide de l’expression donnée. Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details). Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-l|--logger <LOGGER>`**

  Spécifie un enregistreur d’événements pour les résultats de tests. Contrairement à MSBuild, dotnet test n’accepte pas les abréviations : au lieu d' `-l "console;v=d"` utiliser `-l "console;verbosity=detailed"` .

- **`--no-build`**

  Ne génère pas le projet de test avant son exécution. Il définit également implicitement l' `--no-restore` indicateur-.

- **`--nologo`**

  Exécuter les tests sans afficher la bannière Microsoft TestPlatform. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--no-restore`**

  N’effectue pas de restauration implicite à l’exécution de la commande.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Répertoire dans lequel rechercher les binaires à exécuter. S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.  Pour les projets avec plusieurs frameworks cibles (via la `TargetFrameworks` propriété), vous devez également définir `--framework` lorsque vous spécifiez cette option. `dotnet test` exécute toujours les tests à partir du répertoire de sortie. Vous pouvez utiliser <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pour consommer des ressources de test dans le répertoire de sortie.

- **`-r|--results-directory <RESULTS_DIR>`**

  Répertoire où les résultats de test doivent être placés. Si le répertoire spécifié n’existe pas, il est créé. La valeur par défaut se trouve `TestResults` dans le répertoire qui contient le fichier projet.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Runtime cible à tester.

- **`-s|--settings <SETTINGS_FILE>`**

  Fichier `.runsettings` à utiliser pour exécuter les tests. L' `TargetPlatform` élément (x86 | x64) n’a aucun effet pour `dotnet test` . Pour exécuter des tests ciblant x86, installez la version x86 de .NET Core. Le nombre de bits de l' *dotnet.exe* qui se trouve sur le chemin d’accès correspond à ce qui sera utilisé pour l’exécution des tests. Pour plus d’informations, consultez les ressources suivantes :

  - [Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Configurer une série de tests](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Répertoriez les tests découverts au lieu d’exécuter les tests.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `minimal`. Pour plus d'informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** arguments

 Inline `RunSettings` sont passés comme derniers arguments sur la ligne de commande après « -- » (Notez l’espace après--). Inline `RunSettings` sont spécifiés en tant que `[name]=[value]` paires. Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.

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

- Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de couverture du code (après l’installation de l’intégration des collecteurs [coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) ) :

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de couverture du code (Windows uniquement) :

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- Exécutez les tests dans le projet dans le répertoire actif, puis consignez des commentaires détaillés sur la console :

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- Exécutez les tests dans le projet dans le répertoire actif et testez les tests qui étaient en cours lorsque l’hôte de test s’est arrêté :

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a>Détails de l’option de filtre

`--filter <EXPRESSION>`

`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.

`<property>` est un attribut de `Test Case`. Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :

| Framework de test | Propriétés prises en charge                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Name</li><li>ClassName</li><li>Priorité</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Caractéristiques</li></ul>                                   |
| NUnit          | <ul><li>FullyQualifiedName</li><li>Name</li><li>TestCategory</li><li>Priorité</li></ul>                                   |

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
- [Catalogue d’identificateurs de Runtime (RID) .NET Core](../rid-catalog.md)
- [Passage d’arguments RunSettings via la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
