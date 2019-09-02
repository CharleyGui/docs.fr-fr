---
title: Créer un Outil global .NET Core
description: Décrit comment créer un Outil global. Un Outil global est une application console qui est installée via la CLI .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: f60e26d14e89b6b7c34b32bf9a114fe4ad691981
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202766"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Créer un Outil global .NET Core avec la CLI .NET Core

Cet article vous explique comment créer et empaqueter un Outil global .NET Core. La CLI .NET Core vous permet de créer une application console comme un Outil global, que d’autres utilisateurs peuvent facilement installer et exécuter. Les Outils globaux .NET Core sont des packages NuGet qui sont installés à partir de la CLI .NET Core. Pour plus d’informations sur les Outils globaux, consultez [Vue d’ensemble des outils globaux .NET Core](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Créer un projet

Cet article utilise la CLI .NET Core pour créer et gérer un projet.

Notre exemple d’outil est une application console qui génère un bot ASCII et imprime un message. Pour commencer, créez une application console .NET Core.

```console
dotnet new console -o botsay
```

Accédez au répertoire `botsay` créé par la commande précédente.

## <a name="add-the-code"></a>Ajoutez le code

Ouvrez le fichier `Program.cs` avec votre éditeur de texte préféré, tel que `vim` ou [Visual Studio Code](https://code.visualstudio.com/).

Ajoutez la directive `using` suivante au début du fichier. Cela permet de raccourcir le code pour afficher les informations de version de l’application.

```csharp
using System.Reflection;
```

Ensuite, passez à la méthode `Main`. Remplacez la méthode par le code suivant afin de traiter les arguments de ligne de commande pour votre application. Si aucun argument n’a été passé, un court message d’aide s’affiche. Dans le cas contraire, tous ces arguments sont transformés en une chaîne et imprimés avec le robot.

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

### <a name="create-the-bot"></a>Créer le bot

Ensuite, ajoutez une nouvelle méthode nommée `ShowBot` qui accepte un paramètre de chaîne. Cette méthode imprime le message et le bot ASCII. Le code de bot ASCII a été pris dans l’exemple [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs).

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

### <a name="test-the-tool"></a>Tester l’outil

Exécutez le projet et observez le résultat. Essayez ces variations de la ligne de commande pour obtenir des résultats différents :

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Tous les arguments après le délimiteur `--` sont passés à votre application.

## <a name="setup-the-global-tool"></a>Configurer l’outil global

Avant de pouvoir compresser et distribuer l’application en tant qu’outil global, vous devez modifier le fichier projet. Ouvrez le fichier `botsay.csproj`, puis ajoutez trois nouveaux nœuds XML au nœud `<Project><PropertyGroup>` :

- `<PackAsTool>`\
[OBLIGATOIRE] Indique que l’application est empaquetée pour une installation en tant qu’outil global.

- `<ToolCommandName>`\
[FACULTATIF] Autre nom de l’outil, sinon le nom de commande de l’outil sera nommé après le fichier projet. Vous pouvez avoir plusieurs outils dans un package et choisir un nom unique et convivial vous aide à différencier les outils dans un même package.

- `<PackageOutputPath>`\
[FACULTATIF] Emplacement où le package NuGet sera produit. Le package NuGet est utilisé par les Outils globaux CLI .NET Core pour installer votre outil.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

Bien que `<PackageOutputPath>` soit facultatif, utilisez-le dans cet exemple. Veillez à le définir sur : `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Ensuite, créez un package NuGet pour votre application.

```console
dotnet pack
```

Le fichier `botsay.1.0.0.nupkg` est créé dans le dossier identifié par la valeur XML `<PackageOutputPath>` à partir du fichier `botsay.csproj`, qui dans cet exemple est le dossier `./nupkg`. Cela facilite l’installation et le test. Quand vous voulez distribuer un outil publiquement, chargez-le sur <https://www.nuget.org>. Une fois l’outil disponible sur NuGet, les développeurs peuvent l’installer à l’échelle de l’utilisateur en utilisant l’option `--global` de la commande [dotnet tool install](dotnet-tool-install.md).

Maintenant que vous avez un package, installez l’outil à partir de ce package :

```console
dotnet tool install --global --add-source ./nupkg botsay
```

Le paramètre `--add-source` indique à la CLI .NET Core d’utiliser temporairement le dossier `./nupkg` (notre dossier `<PackageOutputPath>`) comme source supplémentaire de flux pour les packages NuGet. Pour plus d’informations sur l’installation des Outils globaux, consultez [Vue d’ensemble des outils globaux .NET Core](global-tools.md).

Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Vous devez maintenant pouvoir taper `botsay` et obtenir une réponse à partir de l’outil.

> [!NOTE]
> Si l’installation a réussi, mais que vous ne pouvez pas utiliser la commande `botsay`, vous devrez peut-être ouvrir un nouveau terminal pour actualiser le chemin d’accès.

## <a name="remove-the-tool"></a>Supprimer l’outil

Une fois que vous avez fini de tester l’outil, vous pouvez le supprimer avec la commande suivante :

```console
dotnet tool uninstall -g botsay
```
