---
title: 'Didacticiel : créer un outil .NET Core'
description: Découvrez comment créer un outil .NET Core. Un outil est une application console installée à l’aide de l’CLI .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156723"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Didacticiel : créer un outil .NET Core à l’aide de l’CLI .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

Ce didacticiel vous apprend à créer et à empaqueter un outil .NET Core. La CLI .NET Core vous permet de créer une application console en tant qu’outil, que d’autres peuvent installer et exécuter. Les outils .NET Core sont des packages NuGet qui sont installés à partir du CLI .NET Core. Pour plus d’informations sur les outils, consultez [vue d’ensemble des outils .net Core](global-tools.md).

L’outil que vous allez créer est une application console qui accepte un message comme entrée et affiche le message avec des lignes de texte qui créent l’image d’un robot.

Il s’agit de la première d’une série de trois didacticiels. Dans ce didacticiel, vous allez créer et empaqueter un outil. Dans les deux didacticiels suivants, vous [Utilisez l’outil comme un outil Global](global-tools-how-to-use.md) et vous [Utilisez l’outil comme outil local](local-tools-how-to-use.md).

## <a name="prerequisites"></a>Composants requis

- [Kit SDK .NET Core 3,1](https://dotnet.microsoft.com/download) ou une version ultérieure.

  Ce didacticiel et le [didacticiel sur les outils généraux](global-tools-how-to-use.md) s’appliquent à kit SDK .net Core 2,1 et versions ultérieures, car les outils globaux sont disponibles à partir de cette version. Toutefois, ce didacticiel suppose que vous avez installé 3,1 ou une version ultérieure afin de pouvoir passer au didacticiel sur les [Outils locaux](local-tools-how-to-use.md). Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0. Les procédures de création d’un outil sont les mêmes que vous l’utilisiez comme outil Global ou comme outil local.
  
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="create-a-project"></a>Créer un projet

1. Ouvrez une invite de commandes et créez un dossier nommé *repository*.

1. Accédez au dossier du *référentiel* , puis entrez la commande suivante :

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   La commande crée un nouveau dossier nommé *Microsoft. botsay* dans le dossier du *référentiel* .

1. Accédez au dossier *Microsoft. botsay* .

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Ajouter le code

1. Ouvrez le fichier `Program.cs` à l’aide de votre éditeur de code.

1. Ajoutez la directive `using` suivante en haut du fichier :

   ```csharp
   using System.Reflection;
   ```

1. Remplacez la méthode `Main` par le code suivant pour traiter les arguments de ligne de commande de l’application.

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

   Si aucun argument n’est passé, un bref message d’aide s’affiche. Sinon, tous les arguments sont concaténés dans une chaîne unique et imprimés en appelant la méthode `ShowBot` que vous créez à l’étape suivante.

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

## <a name="test-the-application"></a>Tester l'application

Exécutez le projet et observez le résultat. Essayez ces variations sur la ligne de commande pour afficher des résultats différents :

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Tous les arguments après le délimiteur `--` sont passés à votre application.

## <a name="package-the-tool"></a>Empaqueter l’outil

Avant de pouvoir empaqueter et distribuer l’application en tant qu’outil, vous devez modifier le fichier projet.

1. Ouvrez le fichier *Microsoft. botsay. csproj* et ajoutez trois nouveaux nœuds XML à la fin du nœud `<PropertyGroup>` :

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` est un élément facultatif qui spécifie la commande qui appellera l’outil après son installation. Si cet élément n’est pas fourni, le nom de commande de l’outil est le nom du fichier projet sans l’extension *. csproj* .

   `<PackageOutputPath>` est un élément facultatif qui détermine où le package NuGet sera produit. Le package NuGet est ce que le CLI .NET Core utilise pour installer votre outil.

   Le fichier projet se présente maintenant comme dans l’exemple suivant :

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
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

   Le fichier *Microsoft. botsay. 1.0.0. nupkg* est créé dans le dossier identifié par la valeur `<PackageOutputPath>` du fichier *Microsoft. botsay. csproj* , qui, dans cet exemple, est le dossier *./nupkg* .
  
   Lorsque vous souhaitez libérer un outil publiquement, vous pouvez le télécharger sur `https://www.nuget.org`. Une fois que l’outil est disponible sur NuGet, les développeurs peuvent installer l’outil à l’aide de la commande d’installation de l' [outil dotnet](dotnet-tool-install.md) . Pour ce didacticiel, vous installez le package directement à partir du dossier local *nupkg* . il n’est donc pas nécessaire de charger le package dans NuGet.

## <a name="troubleshoot"></a>Dépannage

Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Étapes suivantes :

Dans ce didacticiel, vous avez créé une application console et l’avez empaquetée en tant qu’outil. Pour savoir comment utiliser l’outil comme un outil Global, passez au didacticiel suivant.

> [!div class="nextstepaction"]
> [Installer et utiliser un outil Global](global-tools-how-to-use.md)

Si vous préférez, vous pouvez ignorer le didacticiel sur les outils globaux et accéder directement au didacticiel sur les outils locaux.

> [!div class="nextstepaction"]
> [Installer et utiliser un outil local](local-tools-how-to-use.md)
