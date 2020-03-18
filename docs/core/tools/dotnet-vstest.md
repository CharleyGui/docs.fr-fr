---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156931"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Description

La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.

## <a name="arguments"></a>Arguments

- **`TEST_FILE_NAMES`**

  Exécute les tests à partir des fichiers spécifiés. Séparez les noms d’assembly de test par des espaces. Les caractères génériques sont pris en charge.

## <a name="options"></a>Options

- **`--Settings <Settings File>`**

  Paramètres à utiliser durant l’exécution des tests.

- **`--Tests <Test Names>`**

  Exécutez les tests avec les noms qui correspondent aux valeurs fournies. Séparez les valeurs par des virgules.

- **`--TestAdapterPath`**

  Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.

- **`--Platform <Platform type>`**

  Architecture de plateforme cible utilisée pour l’exécution des tests. Les valeurs correctes sont `x86`, `x64` et `ARM`.

- **`--Framework <Framework Version>`**

  Version .NET Framework cible utilisée pour l’exécution des tests. Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.

- **`--Parallel`**

  Exécuter des tests en parallèle. Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables. Spécifier un nombre explicite `MaxCpuCount` de `RunConfiguration` cœurs en plaçant la propriété sous le nœud dans le fichier *runsettings.*

- **`--TestCaseFilter <Expression>`**

  Exécutez les tests qui correspondent à l'expression donnée. `<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`. L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`. La parenthèse `()` est utilisée pour regrouper les sous-exemples.

- **`-?|--Help`**

  Affiche une aide brève pour la commande.

- **`--logger <Logger Uri/FriendlyName>`**

  Spécifiez un journal pour les résultats de tests.

  - Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`. Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné. Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Répertorie tous les tests découverts dans le conteneur de tests donné.

- **`--ParentProcessId <ParentProcessId>`**

  ID du processus parent chargé de lancer le processus actif.

- **`--Port <Port>`**

  Spécifie le port de la connexion de socket et la réception des messages d’événement.

- **`--Diag <Path to log file>`**

  Active les journaux détaillés de la plateforme de test. Les journaux sont écrits dans le fichier fourni.

- **`--Blame`**

  Exécute les tests en mode responsable. Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte. Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.

- **`--InIsolation`**

  Exécute les tests dans un processus isolé. De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.

- **`@<file>`**

  Lit le fichier réponse pour obtenir plus d’options.

- **`args`**

  Spécifie des arguments supplémentaires à passer à l’adaptateur. Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument. Utilisez un espace pour séparer plusieurs arguments.

## <a name="examples"></a>Exemples

Exécuter des tests dans *mytestproject.dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Exécuter des tests dans *mytestproject.dll*, l’exportation vers le dossier personnalisé avec le nom personnalisé:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Exécuter des tests dans *mytestproject.dll* et *myothertestproject.exe:*

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Exécuter des tests `TestMethod1` :

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Exécuter des tests `TestMethod1` et `TestMethod2` :

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
