---
title: 'Tutorial: Créer un outil .NET Core'
description: Apprenez à créer un outil .NET Core. Un outil est une application de console qui est installée en utilisant le CLI .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156723"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Tutorial: Créer un outil .NET Core en utilisant le CLI de base .NET

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

Ce tutoriel vous apprend à créer et à emballer un outil .NET Core. Le CLI Core .NET vous permet de créer une application de console comme un outil, que d’autres peuvent installer et exécuter. .NET Outils de base sont des paquets NuGet qui sont installés à partir de l’ICI CLI .NET Core. Pour plus d’informations sur les outils, voir [.NET Core outils aperçu](global-tools.md).

L’outil que vous allez créer est une application console qui prend un message comme entrée et affiche le message avec des lignes de texte qui créent l’image d’un robot.

C’est le premier d’une série de trois tutoriels. Dans ce tutoriel, vous créez et emballez un outil. Dans les deux prochains tutoriels, vous [utilisez l’outil comme un outil global](global-tools-how-to-use.md) et utiliser [l’outil comme un outil local](local-tools-how-to-use.md).

## <a name="prerequisites"></a>Conditions préalables requises

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou une version ultérieure.

  Ce tutoriel et le tutoriel suivant pour les [outils globaux](global-tools-how-to-use.md) s’appliquent à .NET Core SDK 2.1 et les versions ultérieures parce que les outils globaux sont disponibles à partir de cette version. Mais ce tutoriel suppose que vous avez installé 3.1 ou plus tard de sorte que vous avez la possibilité de continuer sur le [tutoriel outils locaux](local-tools-how-to-use.md). Les outils locaux sont disponibles à partir de .NET Core SDK 3.0. Les procédures de création d’un outil sont les mêmes que vous l’utilisiez comme un outil global ou comme un outil local.
  
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="create-a-project"></a>Création d’un projet

1. Ouvrez une invite de commande et créez un dossier nommé *référentiel.*

1. Naviguez vers le dossier *du dépôt* et entrez la commande suivante :

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   La commande crée un nouveau dossier nommé *microsoft.botsay* sous le dossier *de dépôt.*

1. Naviguez vers le dossier *microsoft.botsay.*

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Ajouter le code

1. Ouvrez `Program.cs` le fichier avec votre éditeur de code.

1. Ajoutez la directive `using` suivante en haut du fichier :

   ```csharp
   using System.Reflection;
   ```

1. Remplacez `Main` la méthode par le code suivant pour traiter les arguments de la ligne de commande pour l’application.

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

   Si aucun argument n’est adopté, un court message d’aide est affiché. Sinon, tous les arguments sont concatenated en une `ShowBot` seule chaîne et imprimés en appelant la méthode que vous créez dans l’étape suivante.

1. Ajoutez une nouvelle `ShowBot` méthode nommée qui prend un paramètre de chaîne. La méthode imprime le message et une image d’un robot à l’aide de lignes de texte.

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

Exécutez le projet et observez le résultat. Essayez ces variations à la ligne de commande pour voir les différents résultats :

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Tous les arguments après le délimiteur `--` sont passés à votre application.

## <a name="package-the-tool"></a>Emballez l’outil

Avant de pouvoir emballer et distribuer l’application comme outil, vous devez modifier le fichier de projet.

1. Ouvrez le fichier *microsoft.botsay.csproj* et ajoutez trois nouveaux `<PropertyGroup>` nœuds XML à la fin du nœud :

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`est un élément facultatif qui spécifie la commande qui invoquera l’outil après son installation. Si cet élément n’est pas fourni, le nom de commande de l’outil est le nom de fichier de projet sans l’extension *.csproj.*

   `<PackageOutputPath>`est un élément facultatif qui détermine où le paquet NuGet sera produit. Le paquet NuGet est ce que le CLI de base .NET utilise pour installer votre outil.

   Le dossier du projet ressemble maintenant à l’exemple suivant :

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

1. Créez un package NuGet en exécutant la commande [dotnet pack](dotnet-pack.md) :

   ```dotnetcli
   dotnet pack
   ```

   Le fichier *microsoft.botsay.1.0.0.nupkg* est créé dans `<PackageOutputPath>` le dossier identifié par la valeur du fichier *microsoft.botsay.csproj,* qui dans cet exemple est le dossier *./nupkg.*
  
   Lorsque vous souhaitez libérer un outil publiquement, `https://www.nuget.org`vous pouvez le télécharger à . Une fois que l’outil est disponible sur NuGet, les développeurs peuvent installer l’outil en utilisant la commande [d’installation d’outils dotnet.](dotnet-tool-install.md) Pour ce tutoriel, vous installez le paquet directement à partir du dossier *local nupkg,* il n’est donc pas nécessaire de télécharger le paquet sur NuGet.

## <a name="troubleshoot"></a>Dépanner

Si vous obtenez un message d’erreur tout en suivant le tutoriel, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé une application de console et l’avez emballée comme un outil. Pour apprendre à utiliser l’outil comme un outil global, passez au tutoriel suivant.

> [!div class="nextstepaction"]
> [Installer et utiliser un outil global](global-tools-how-to-use.md)

Si vous préférez, vous pouvez sauter le tutoriel d’outils globaux et aller directement au tutoriel d’outils locaux.

> [!div class="nextstepaction"]
> [Installer et utiliser un outil local](local-tools-how-to-use.md)
