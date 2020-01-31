---
title: Prise en main de .NET Core à l’aide de l’interface CLI-CLI .NET Core
description: Didacticiel pas à pas montrant comment démarrer avec .NET Core sur Windows, Linux ou Mac OS à l’aide de l’interface de ligne de commande (CLI) .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 4285ed3c0488ea615ca89b0b771bf09c8c29b318
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739128"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Bien démarrer avec .NET Core sur Windows/Linux/macOS en ligne de commande

Cet article vous montre comment commencer à développer des applications multiplateformes sur votre ordinateur à l’aide des outils de CLI .NET Core.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).

## <a name="prerequisites"></a>Prerequisites

- [Kit SDK .NET Core 3,1](https://dotnet.microsoft.com/download) ou versions ultérieures.
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="hello-console-app"></a>Application console Hello

Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Ouvrez une invite de commandes et créez un dossier nommé *Hello*. Accédez au dossier créé et tapez ce qui suit :

```dotnetcli
dotnet new console
dotnet run
```

Suivons une procédure pas à pas rapide :

01. `dotnet new console`

    [dotnet New](../tools/dotnet-new.md) crée un fichier projet *Hello. csproj* à jour avec les dépendances nécessaires à la création d’une application console. Il crée également un *Program.cs*, un fichier de base contenant le point d’entrée de l’application.
    
    *Bonjour. csproj*:
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.
    
    - L’élément `<OutputType>` spécifie que nous créons un exécutable, en d’autres termes une application console.
    - L’élément `<TargetFramework>` spécifie l’implémentation .NET que nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération. Dans ce didacticiel, nous allons nous contenter de créer uniquement pour .NET Core 3,1.
    
    *Program.cs* :
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ». L’espace de noms `System` comprend la classe `Console`.
    
    Ensuite, nous définissons un espace de noms appelé `Hello`. Vous pouvez le modifier à votre gré. Une classe nommée `Program` est définie dans cet espace de noms, avec une méthode `Main` qui prend un tableau de chaînes nommé `args`. Ce tableau contient la liste des arguments passés lors de l’exécution du programme. Comme c’est le cas, ce tableau n’est pas utilisé et le programme écrit simplement le texte « Hello World ! » dans la console. Plus tard, nous apporterons des modifications au code qui utilisent cet argument.
    
    `dotnet new` appelle [dotnet Restore](../tools/dotnet-restore.md) implicitement. `dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances. NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.

02. `dotnet run`

    [dotnet Run](../tools/dotnet-run.md) appelle [dotnet Build](../tools/dotnet-build.md) pour s’assurer que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.
    
    ```console
    dotnet run

    Hello World!
    ```
    
    Vous pouvez également exécuter `dotnet build` pour compiler le code sans exécuter les applications console de génération. Il en résulte une application compilée, sous la forme d’un fichier DLL, en fonction du nom du projet. Dans ce cas, le fichier créé est nommé *Hello. dll*. Cette application peut être exécutée avec `dotnet bin\Debug\netcoreapp3.1\Hello.dll` sur Windows (utilisez `/` pour les systèmes non-Windows).
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    Lorsque l’application est compilée, un fichier exécutable spécifique au système d’exploitation a été créé avec l' `Hello.dll`. Sur Windows, ce serait `Hello.exe`; sur Linux ou macOS, ce serait `hello`. Dans l’exemple ci-dessus, le fichier est nommé avec `Hello.exe` ou `Hello`. Vous pouvez exécuter cet exécutable directement.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modifier le programme

Modifions un peu le programme. Les nombres Fibonacci sont amusants. nous allons donc l’ajouter et également utiliser l’argument pour accueillir la personne qui exécute l’application.

01. Remplacez le contenu du fichier *Program.cs* par le code suivant :

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. Exécutez [dotnet Build](../tools/dotnet-build.md) pour compiler les modifications.

03. Exécutez le programme en passant un paramètre à l’application. Lorsque vous utilisez la commande `dotnet` pour exécuter une application, ajoutez `--` à la fin. Tout ce qui se trouve à droite de `--` est passé en tant que paramètre à l’application. Dans l’exemple suivant, la valeur `John` est passée à l’application.

    ```console
    $ dotnet run -- John
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

Et voilà ! Vous pouvez modifier *Program.cs* comme vous le souhaitez.

## <a name="working-with-multiple-files"></a>Utilisation de plusieurs fichiers

Les fichiers uniques conviennent parfaitement aux programmes simples et uniques, mais si vous créez une application plus complexe, vous aurez probablement plusieurs fichiers de code sur votre projet. Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.

01. Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. Exécutez [dotnet Build](../tools/dotnet-build.md) pour compiler les modifications.

04. Exécutez votre application en exécutant [dotnet Run](../tools/dotnet-run.md). Voici la sortie du programme :

    ```console
    $ dotnet run
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

## <a name="publish-your-app"></a>Publier une application

Une fois que vous êtes prêt à distribuer votre application, utilisez la commande [dotnet Publish](../tools/dotnet-publish.md) pour générer le dossier de _publication_ dans _bin\\Debug\\netcoreapp 3.1\\Publish\\_ (utilisez `/` pour les systèmes non-Windows). Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

La sortie ci-dessus peut varier en fonction de votre dossier actuel et du système d’exploitation, mais la sortie doit être similaire.

Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

Comme mentionné au début de cet article, un fichier exécutable spécifique au système d’exploitation a été créé avec l' `Hello.dll`. Sur Windows, ce serait `Hello.exe`; sur Linux ou macOS, ce serait `hello`. Dans l’exemple ci-dessus, le fichier est nommé avec `Hello.exe` ou `Hello`. Vous pouvez exécuter ce fichier exécutable publié directement.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Conclusion

Et voilà ! À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.

## <a name="see-also"></a>Voir aussi

- [Organisation et test de projets avec les outils CLI .NET Core](testing-with-cli.md)
- [Publier des applications .NET Core avec l’interface CLI](../deploying/deploy-with-cli.md)
- [Pour en savoir plus sur le déploiement](../deploying/index.md)
