---
title: 'Didacticiel : créer un outil .NET'
description: Découvrez comment créer un outil .NET. Un outil est une application console installée à l’aide de l’interface CLI .NET.
ms.topic: tutorial
ms.date: 12/14/2020
ms.openlocfilehash: dc5cf014336848ff1a3035647a386419653a083b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633895"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a>Didacticiel : créer un outil .NET à l’aide de l’interface de commande .NET

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

Ce didacticiel vous apprend à créer et à empaqueter un outil .NET. L’interface de commande .NET vous permet de créer une application console en tant qu’outil, que d’autres peuvent installer et exécuter. Les outils .NET sont des packages NuGet qui sont installés à partir de l’interface CLI .NET. Pour plus d’informations sur les outils, consultez [vue d’ensemble des outils .net](global-tools.md).

L’outil que vous allez créer est une application console qui accepte un message comme entrée et affiche le message avec des lignes de texte qui créent l’image d’un robot.

Il s’agit de la première d’une série de trois didacticiels. Dans ce didacticiel, vous allez créer et empaqueter un outil. Dans les deux didacticiels suivants, vous [Utilisez l’outil comme un outil Global](global-tools-how-to-use.md) et vous [Utilisez l’outil comme outil local](local-tools-how-to-use.md). Les procédures de création d’un outil sont les mêmes que vous l’utilisiez comme outil Global ou comme outil local.

## <a name="prerequisites"></a>Prérequis

- [Kit de développement logiciel (SDK) .net 5.0.100](https://dotnet.microsoft.com/download) ou version ultérieure.

  Ce didacticiel utilise le kit de développement logiciel (SDK) .NET 5,0, mais les outils globaux sont disponibles à partir de kit SDK .NET Core 2,1. Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.

- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="create-a-project"></a>Création d’un projet

1. Ouvrez une invite de commandes et créez un dossier nommé *repository*.

1. Accédez au dossier du *référentiel* , puis entrez la commande suivante :

   ```dotnetcli
   dotnet new console -n microsoft.botsay -f net5.0
   ```

   La commande crée un nouveau dossier nommé *Microsoft. botsay* dans le dossier du *référentiel* .

   > [!NOTE]
   > Pour ce didacticiel, vous allez créer un outil qui cible .NET 5,0. Pour cibler une autre infrastructure, modifiez l' `-f|--framework` option. Pour cibler plusieurs frameworks, remplacez l' `TargetFramework` élément par un `TargetFrameworks` élément dans le fichier projet, comme indiqué dans l’exemple suivant :
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Accédez au dossier *Microsoft. botsay* .

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Ajouter le code

1. Ouvrez le `Program.cs` fichier à l’aide de votre éditeur de code.

1. Ajoutez la directive `using` suivante en haut du fichier :

   ```csharp
   using System.Reflection;
   ```

1. Remplacez la `Main` méthode par le code suivant pour traiter les arguments de ligne de commande de l’application.

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   Si aucun argument n’est passé, un bref message d’aide s’affiche. Sinon, tous les arguments sont concaténés dans une chaîne unique et imprimés en appelant la `ShowBot` méthode que vous créez à l’étape suivante.

1. Ajoutez une nouvelle méthode nommée `ShowBot` qui accepte un paramètre de chaîne. La méthode imprime le message et une image d’un robot à l’aide de lignes de texte.

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. Enregistrez vos modifications.

## <a name="test-the-application"></a>Test de l’application

Exécutez le projet et observez le résultat. Essayez ces variations sur la ligne de commande pour afficher des résultats différents :

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Tous les arguments après le délimiteur `--` sont passés à votre application.

## <a name="package-the-tool"></a>Empaqueter l’outil

Avant de pouvoir empaqueter et distribuer l’application en tant qu’outil, vous devez modifier le fichier projet.

1. Ouvrez le fichier *Microsoft. botsay. csproj* et ajoutez trois nouveaux nœuds XML à la fin du `<PropertyGroup>` nœud :

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` est un élément facultatif qui spécifie la commande qui appellera l’outil après son installation. Si cet élément n’est pas fourni, le nom de commande de l’outil est le nom du fichier projet sans l’extension *. csproj* .

   `<PackageOutputPath>` est un élément facultatif qui détermine où le package NuGet sera produit. Le package NuGet est ce que l’interface de commande .NET utilise pour installer votre outil.

   Le fichier projet se présente maintenant comme dans l’exemple suivant :

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>net5.0</TargetFramework>

       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>

     </PropertyGroup>

   </Project>
   ```

1. Créez un package NuGet en exécutant la commande [dotnet Pack](dotnet-pack.md) :

   ```dotnetcli
   dotnet pack
   ```

   Le fichier *Microsoft. botsay. 1.0.0. nupkg* est créé dans le dossier identifié par la `<PackageOutputPath>` valeur du fichier *Microsoft. botsay. csproj* , qui, dans cet exemple, est le dossier *./nupkg* .

   Lorsque vous souhaitez libérer un outil publiquement, vous pouvez le télécharger sur `https://www.nuget.org` . Une fois que l’outil est disponible sur NuGet, les développeurs peuvent installer l’outil à l’aide de la commande d’installation de l' [outil dotnet](dotnet-tool-install.md) . Pour ce didacticiel, vous installez le package directement à partir du dossier local *nupkg* . il n’est donc pas nécessaire de charger le package dans NuGet.

## <a name="troubleshoot"></a>Résoudre des problèmes

Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation des outils .net](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une application console et l’avez empaquetée en tant qu’outil. Pour savoir comment utiliser l’outil comme un outil Global, passez au didacticiel suivant.

> [!div class="nextstepaction"]
> [Installer et utiliser un outil Global](global-tools-how-to-use.md)

Si vous préférez, vous pouvez ignorer le didacticiel sur les outils globaux et accéder directement au didacticiel sur les outils locaux.

> [!div class="nextstepaction"]
> [Installer et utiliser un outil local](local-tools-how-to-use.md)
