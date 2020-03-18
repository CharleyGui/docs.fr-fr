---
title: Bien démarrer avec .NET Core à l’aide de l’interface CLI
description: Un tutoriel étape par étape montrant comment commencer avec .NET Core sur Windows, Linux, ou macOS en utilisant le CLI .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240855"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Démarrer avec .NET Core en utilisant le CLI .NET Core

Cet article vous montrera comment commencer à développer des applications .NET Core qui fonctionnent sur Windows, Linux et macOS en utilisant le CLI Core .NET.

Si vous n’êtes pas familier avec le CLI de base .NET, voir la [vue d’ensemble .NET Core CLI](../tools/index.md).

## <a name="prerequisites"></a>Conditions préalables requises

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou versions ultérieures.
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="hello-console-app"></a>Application console Hello

Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Ouvrez une invite de commandes et créez un dossier nommé *Hello*. Naviguez vers le dossier que vous avez créé et tapez ce qui suit.

```dotnetcli
dotnet new console
dotnet run
```

Suivons une procédure pas à pas rapide :

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md) crée un fichier de projet *Hello.csproj* à jour avec les dépendances nécessaires à la construction d’une application console. Il crée également un *Program.cs*, un fichier de base contenant le point d’entrée pour l’application.

    *Hello.csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.

    - L’élément `<OutputType>` spécifie que nous construisons une application exécutable, c’est-à-dire une application de console.
    - L’élément `<TargetFramework>` spécifie quelle mise en œuvre .NET nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération. Dans ce tutoriel, nous allons nous en tenir à la construction que pour .NET Core 3.1.

    *Program.cs*:

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ». L’espace `System` de `Console` nom comprend la classe.

    Ensuite, nous définissons un espace de noms appelé `Hello`. Vous pouvez le modifier à votre gré. Une classe `Program` nommée est définie dans `Main` cet espace de nom, `args`avec une méthode qui prend un tableau de cordes nommées . Ce tableau contient la liste des arguments adoptés lorsque le programme est exécuté. Comme il est, ce tableau n’est pas utilisé et le programme écrit simplement le texte "Bonjour monde!" dans la console. Plus tard, nous apporterons des modifications au code qui utilisent cet argument.

    `dotnet new`appels [dotnet restaurer](../tools/dotnet-restore.md) implicitement. `dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances. NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.

02. `dotnet run`

    [dotnet exécuter](../tools/dotnet-run.md) les appels [dotnet construire](../tools/dotnet-build.md) pour s’assurer `dotnet <assembly.dll>` que les cibles de construction ont été construits, puis appelle pour exécuter l’application cible.

    ```dotnetcli
    dotnet run
    ```

    Vous obtenez la sortie suivante.

    ```console
    Hello World!
    ```

    Alternativement, vous pouvez `dotnet build` également exécuter pour compiler le code sans exécuter les applications de console de construction. Il en résulte une application compilée, comme un fichier DLL, basé sur le nom du projet. Dans ce cas, le fichier créé est nommé *Hello.dll*. Cette application peut `dotnet bin\Debug\netcoreapp3.1\Hello.dll` être exécutée `/` avec windows (utilisation pour les systèmes non Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Vous obtenez la sortie suivante.

    ```console
    Hello World!
    ```

    Lorsque l’application est compilée, un système d’exploitation spécifique exécutable a été créé avec le `Hello.dll`. Sur Windows, ce `Hello.exe`serait ; sur Linux ou macOS, `hello`ce serait . Avec l’exemple ci-dessus, `Hello.exe` `Hello`le fichier est nommé avec ou . Vous pouvez exécuter ce exécutable directement.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modifier le programme

Modifions un peu le programme. Fibonacci nombres sont amusants, nous allons donc ajouter que et aussi d’utiliser l’argument pour saluer la personne en cours d’exécution de l’application.

01. Remplacez le contenu du fichier *Program.cs* par le code suivant :

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Exécuter [dotnet construire](../tools/dotnet-build.md) pour compiler les modifications.

03. Exécutez le programme en passant un paramètre à l’application. Lorsque vous `dotnet` utilisez la commande pour `--` exécuter une application, ajoutez à la fin. Tout ce qui `--` est à droite sera transmis comme un paramètre à l’application. Dans l’exemple suivant, la valeur `John` est transmise à l’application.

    ```dotnetcli
    dotnet run -- John
    ```

    Vous obtenez la sortie suivante.

    ```console
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

Et le tour est joué ! Vous pouvez modifier *Program.cs* comme vous le souhaitez.

## <a name="working-with-multiple-files"></a>Utilisation de plusieurs fichiers

Les fichiers simples sont très bien pour les programmes simples et uniques, mais si vous construisez une application plus complexe, vous allez probablement avoir plusieurs fichiers de code sur votre projet. Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.

01. Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Exécuter [dotnet construire](../tools/dotnet-build.md) pour compiler les modifications.

04. Exécutez votre application en exécutant [dotnet exécuter](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Vous obtenez la sortie suivante.

    ```console
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a>Publier votre application

Une fois que vous êtes prêt à distribuer votre application, utilisez la commande [de publication dotnet](../tools/dotnet-publish.md) pour générer `/` le dossier de _publication_ à _\\bin\\debug netcoreapp3.1\\publier\\ _ (utilisation pour les systèmes non Windows). Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.

```dotnetcli
dotnet publish
```

Vous obtenez la sortie similaire à ce qui suit.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

La sortie ci-dessus peut différer en fonction de votre dossier actuel et le système d’exploitation, mais la sortie doit être similaire.

Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Vous obtenez la sortie suivante.

```console
Hello World!
```

Comme mentionné au début de cet article, un système d’exploitation spécifique exécutable a été créé avec le `Hello.dll`. Sur Windows, ce `Hello.exe`serait ; sur Linux ou macOS, `hello`ce serait . Avec l’exemple ci-dessus, `Hello.exe` `Hello`le fichier est nommé avec ou . Vous pouvez exécuter ce publiable directement.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Conclusion

Et le tour est joué ! À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.

## <a name="see-also"></a>Voir aussi

- [Organisation et test de projets avec le CLI core .NET](testing-with-cli.md)
- [Publier des applications .NET Core avec le CLI core .NET](../deploying/deploy-with-cli.md)
- [.NET Déploiement d’applications de base](../deploying/index.md)
