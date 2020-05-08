---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975392"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

> [!IMPORTANT]
> La `dotnet vstest` commande est remplacée par `dotnet test`, qui peut maintenant être utilisée pour exécuter des assemblys. Voir [`dotnet test`](dotnet-test.md).

## <a name="name"></a>Nom

`dotnet-vstest`-Exécute les tests à partir des assemblys spécifiés.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a>Description

La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.

## <a name="arguments"></a>Arguments

- **`TEST_FILE_NAMES`**

  Exécute les tests à partir des fichiers spécifiés. Séparez les noms d’assembly de test par des espaces. Les caractères génériques sont pris en charge.

## <a name="options"></a>Options

- **`--Blame`**

  Exécute les tests en mode responsable. Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte. Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.

- **`--Diag <PATH_TO_LOG_FILE>`**

  Active les journaux détaillés de la plateforme de test. Les journaux sont écrits dans le fichier fourni.

- **`--Framework <FRAMEWORK>`**

  Version .NET Framework cible utilisée pour l’exécution des tests. Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.

- **`--InIsolation`**

  Exécute les tests dans un processus isolé. De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.

- **`-lt|--ListTests <FILE_NAME>`**

  Répertorie tous les tests découverts dans le conteneur de tests donné.

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

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

- **`--Parallel`**

  Exécuter les tests en parallèle. Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables. Spécifiez un nombre de cœurs explicite en définissant `MaxCpuCount` la propriété sous `RunConfiguration` le nœud dans le fichier *RunSettings* .

- **`--ParentProcessId <PROCESS_ID>`**

  ID du processus parent chargé de lancer le processus actif.

- **`--Platform <PLATFORM_TYPE>`**

  Architecture de plateforme cible utilisée pour l’exécution des tests. Les valeurs correctes sont `x86`, `x64` et `ARM`.

- **`--Port <PORT>`**

  Spécifie le port de la connexion de socket et la réception des messages d’événement.

- **`--ResultsDirectory:<PATH>`**

  Un répertoire de résultats de test sera créé dans le chemin d’accès spécifié s’il n’en existe pas.

- **`--Settings <SETTINGS_FILE>`**

  Paramètres à utiliser durant l’exécution des tests.

- **`--TestAdapterPath <PATH>`**

  Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.

- **`--TestCaseFilter <EXPRESSION>`**

  Exécutez les tests qui correspondent à l'expression donnée. `<EXPRESSION>` est au format `<property>Operator<value>[|&<EXPRESSION>]`, où l’opérateur est `=`, `!=` ou `~`. L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`. `()` Les parenthèses sont utilisées pour regrouper des sous-expressions. Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <TEST_NAMES>`**

  Exécutez les tests avec les noms qui correspondent aux valeurs fournies. Séparez les valeurs par des virgules.

- **`-?|--Help`**

  Affiche une aide brève pour la commande.

- **`@<file>`**

  Lit le fichier réponse pour obtenir plus d’options.

- **`args`**

  Spécifie des arguments supplémentaires à passer à l’adaptateur. Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument. Utilisez un espace pour séparer plusieurs arguments.

## <a name="examples"></a>Exemples

Exécuter les tests dans *MyTestProject. dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Exécutez les tests dans *MyTestProject. dll*, en les exportant vers un dossier personnalisé avec un nom personnalisé :

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Exécuter les tests dans *MyTestProject. dll* et *myothertestproject. exe*:

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

## <a name="see-also"></a>Voir aussi

- [Options de ligne de commande VSTest.Console.exe](/visualstudio/test/vstest-console-options)
