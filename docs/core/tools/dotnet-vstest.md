---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 05/30/2018
ms.openlocfilehash: c3838617ed539cf56f2840b826e9de58833820fd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215311"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.

## <a name="synopsis"></a>Synopsis

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Description

La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Exécute les tests à partir des fichiers spécifiés. Séparez les noms d’assembly de test par des espaces.

## <a name="options"></a>Options

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Paramètres à utiliser durant l’exécution des tests.

`--Tests|/Tests:<Test Names>`

Exécutez les tests avec les noms qui correspondent aux valeurs fournies. Séparez les valeurs par des virgules.

`--TestAdapterPath|/TestAdapterPath`

Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.

`--Platform|/Platform:<Platform type>`

Architecture de plateforme cible utilisée pour l’exécution des tests. Les valeurs correctes sont `x86`, `x64` et `ARM`.

`--Framework|/Framework:<Framework Version>`

Version .NET Framework cible utilisée pour l’exécution des tests. Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.

`--Parallel|/Parallel`

Exécutez des tests en parallèle. Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables. Spécifiez un nombre de cœurs explicite en définissant la propriété MaxCpuCount sous le nœud RunConfiguration du fichier runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Exécutez les tests qui correspondent à l'expression donnée. `<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`. L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`. Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.

`-?|--Help|/?|/Help`

Affiche une aide brève pour la commande.

`--logger|/logger:<Logger Uri/FriendlyName>`

Spécifiez un journal pour les résultats de tests.

* Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`. Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné. Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Répertorie tous les tests découverts dans le conteneur de tests donné.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID du processus parent chargé de lancer le processus actif.

`--Port|/Port:<Port>`

Spécifie le port de la connexion de socket et la réception des messages d’événement.

`--Diag|/Diag:<Path to log file>`

Active les journaux détaillés de la plateforme de test. Les journaux sont écrits dans le fichier fourni.

`--Blame|/Blame`

Exécute les tests en mode responsable. Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte. Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.

`--InIsolation|/InIsolation`

Exécute les tests dans un processus isolé. De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.

`@<file>`

Lit le fichier réponse pour obtenir plus d’options.

`args`

Spécifie des arguments supplémentaires à passer à l’adaptateur. Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument. Utilisez un espace pour séparer plusieurs arguments.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Paramètres à utiliser durant l’exécution des tests.

`--Tests|/Tests:<Test Names>`

Exécutez les tests avec les noms qui correspondent aux valeurs fournies. Séparez les valeurs par des virgules.

`--TestAdapterPath|/TestAdapterPath`

Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.

`--Platform|/Platform:<Platform type>`

Architecture de plateforme cible utilisée pour l’exécution des tests. Les valeurs correctes sont `x86`, `x64` et `ARM`.

`--Framework|/Framework:<Framework Version>`

Version .NET Framework cible utilisée pour l’exécution des tests. Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Les valeurs `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.

`--Parallel|/Parallel`

Exécutez des tests en parallèle. Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables. Spécifiez un nombre de cœurs explicite en définissant la propriété MaxCpuCount sous le nœud RunConfiguration du fichier runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Exécutez les tests qui correspondent à l'expression donnée. `<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`. L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`. Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.

`-?|--Help|/?|/Help`

Affiche une aide brève pour la commande.

`--logger|/logger:<Logger Uri/FriendlyName>`

Spécifiez un journal pour les résultats de tests.

* Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`. Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné. Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Répertorie tous les tests découverts dans le conteneur de tests donné.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID du processus parent chargé de lancer le processus actif.

`--Port|/Port:<Port>`

Spécifie le port de la connexion de socket et la réception des messages d’événement.

`--Diag|/Diag:<Path to log file>`

Active les journaux détaillés de la plateforme de test. Les journaux sont écrits dans le fichier fourni.

`args`

Spécifie des arguments supplémentaires à passer à l’adaptateur. Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument. Utilisez un espace pour séparer plusieurs arguments.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Paramètres à utiliser durant l’exécution des tests.

`--Tests|/Tests:<Test Names>`

Exécutez les tests avec les noms qui correspondent aux valeurs fournies. Séparez les valeurs par des virgules.

`--TestAdapterPath|/TestAdapterPath`

Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.

`--Platform|/Platform:<Platform type>`

Architecture de plateforme cible utilisée pour l’exécution des tests. Les valeurs correctes sont `x86`, `x64` et `ARM`.

`--Framework|/Framework:<Framework Version>`

Version .NET Framework cible utilisée pour l’exécution des tests. Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Les valeurs `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.

`--Parallel|/Parallel`

Exécutez des tests en parallèle. Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables. Spécifiez un nombre de cœurs explicite en définissant la propriété MaxCpuCount sous le nœud RunConfiguration du fichier runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Exécutez les tests qui correspondent à l'expression donnée. `<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`. L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`. Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.

`-?|--Help|/?|/Help`

Affiche une aide brève pour la commande.

`--logger|/logger:<Logger Uri/FriendlyName>`

Spécifiez un journal pour les résultats de tests.

* Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`. Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné. Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Répertorie tous les tests découverts dans le conteneur de tests donné.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID du processus parent chargé de lancer le processus actif.

`--Port|/Port:<Port>`

Spécifie le port de la connexion de socket et la réception des messages d’événement.

`--Diag|/Diag:<Path to log file>`

Active les journaux détaillés de la plateforme de test. Les journaux sont écrits dans le fichier fourni.

`args`

Spécifie des arguments supplémentaires à passer à l’adaptateur. Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument. Utilisez un espace pour séparer plusieurs arguments.

---

## <a name="examples"></a>Exemples

Exécuter des tests dans `mytestproject.dll` :

`dotnet vstest mytestproject.dll`

Exécuter des tests dans `mytestproject.dll`, en exportant vers un dossier personnalisé avec un nom personnalisé :

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Exécuter des tests dans `mytestproject.dll` et `myothertestproject.exe` :

`dotnet vstest mytestproject.dll myothertestproject.exe`

Exécuter des tests `TestMethod1` :

`dotnet vstest /Tests:TestMethod1`

Exécuter des tests `TestMethod1` et `TestMethod2` :

`dotnet vstest /Tests:TestMethod1,TestMethod2`
