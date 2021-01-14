---
title: Créer une application .NET Core avec des plug-ins
description: Découvrez comment créer une application .NET Core qui prend en charge les plug-ins.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: d3b532ae72a80eef9603fc6f3ada8c11cae966dd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187897"
---
# <a name="create-a-net-core-application-with-plugins"></a>Créer une application .NET Core avec des plug-ins

Ce didacticiel vous montre comment créer un personnalisé <xref:System.Runtime.Loader.AssemblyLoadContext> pour charger des plug-ins. Un <xref:System.Runtime.Loader.AssemblyDependencyResolver> est utilisé pour résoudre les dépendances du plug-in. Le didacticiel isole correctement les dépendances du plug-in à partir de l’application d’hébergement. Vous découvrirez comment effectuer les actions suivantes :

- Structurer un projet de façon à prendre en charge les plug-ins.
- Créer un <xref:System.Runtime.Loader.AssemblyLoadContext> personnalisé pour charger chaque plug-in.
- Utiliser le type <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> pour permettre aux plug-ins d’avoir des dépendances.
- Créer des plug-ins qui peuvent être facilement déployés en copiant simplement les artefacts de build.

## <a name="prerequisites"></a>Prérequis

- Installez le [Kit de développement logiciel (SDK) .net 5](https://dotnet.microsoft.com/download) ou une version plus récente.

> [!NOTE]
> L’exemple de code cible .NET 5, mais toutes les fonctionnalités qu’il utilise ont été introduites dans .NET Core 3,0 et sont disponibles dans toutes les versions de .NET depuis.

## <a name="create-the-application"></a>Création de l'application

La première étape consiste à créer l’application :

1. Créez un nouveau dossier et, dans ce dossier, exécutez la commande suivante :

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Pour faciliter la création du projet, créez un fichier solution Visual Studio dans le même dossier. Exécutez la commande suivante :

    ```dotnetcli
    dotnet new sln
    ```

3. Exécutez la commande suivante pour ajouter le projet d’application à la solution :

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Vous pouvez maintenant compléter la structure de votre application. Remplacez le code figurant dans le fichier *AppWithPlugin/Program.cs* par le code suivant :

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a>Créer les interfaces de plug-in

La prochaine étape de la procédure de création d’une application avec plug-ins consiste à définir l’interface que doivent implémenter les plug-ins. Nous vous suggérons de créer une bibliothèque de classes qui contient les types que vous prévoyez d’utiliser pour permettre la communication entre votre application et les plug-ins. Cette division vous permet de publier votre interface de plug-in en tant que package sans avoir à transmettre votre application complète.

Dans le dossier racine du projet, exécutez `dotnet new classlib -o PluginBase`. De même, exécutez `dotnet sln add PluginBase/PluginBase.csproj` pour ajouter le projet au fichier solution. Supprimez le fichier `PluginBase/Class1.cs` et créez-en un nouveau dans le dossier `PluginBase` sous le nom `ICommand.cs` avec la définition d’interface suivante :

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

Cette interface `ICommand` est l’interface que tous les plug-ins vont implémenter.

Maintenant que l’interface `ICommand` est définie, le projet d’application peut être davantage complété. Ajoutez une référence du projet `AppWithPlugin` au projet `PluginBase` avec la commande `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj` à partir du dossier racine.

Remplacez le commentaire `// Load commands from plugins` par l’extrait de code suivant pour lui permettre de charger les plug-ins à partir des chemins de fichiers donnés :

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

Remplacez ensuite le commentaire `// Output the loaded commands` par l’extrait de code suivant :

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Remplacez le commentaire `// Execute the command with the name passed as an argument` par l’extrait suivant :

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

Et enfin, ajoutez à la classe `Program` les méthodes statiques nommées `LoadPlugin` et `CreateCommands`, comme indiqué ici :

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a>Charger les plug-ins

Désormais, l’application peut charger et instancier correctement des commandes à partir d’assemblys de plug-in chargés, mais elle ne peut toujours pas charger les assemblys de plug-in. Créez un fichier nommé *PluginLoadContext.cs* dans le dossier *AppWithPlugin* avec le contenu suivant :

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

Le type `PluginLoadContext` dérive de <xref:System.Runtime.Loader.AssemblyLoadContext>. Le `AssemblyLoadContext` type est un type spécial dans le runtime qui permet aux développeurs d’isoler les assemblys chargés dans différents groupes pour s’assurer que les versions d’assembly ne sont pas en conflit. Par ailleurs, un `AssemblyLoadContext` personnalisé peut choisir les différents chemins à partir desquels les assemblys seront chargés et substituer le comportement par défaut. `PluginLoadContext` utilise une instance du type `AssemblyDependencyResolver` introduit dans .NET Core 3.0 pour résoudre les noms d’assembly en chemins. L’objet `AssemblyDependencyResolver` est construit avec le chemin d’une bibliothèque de classes .NET. Il résout les assemblys et les bibliothèques natives en leurs chemins d’accès relatifs en fonction de l' *.deps.jssur* le fichier de la bibliothèque de classes dont le chemin d’accès a été passé au `AssemblyDependencyResolver` constructeur. Le `AssemblyLoadContext` personnalisé permet aux plug-ins d’avoir leurs propres dépendances, tandis que `AssemblyDependencyResolver` facilite le chargement des dépendances.

Maintenant que le projet `AppWithPlugin` présente le type `PluginLoadContext`, mettez à jour la méthode `Program.LoadPlugin` avec le corps suivant :

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

En utilisant une instance `PluginLoadContext` différente pour chaque plug-in, les plug-ins peuvent avoir différentes dépendances, voire des dépendances en conflit sans que cela ne pose problème.

## <a name="simple-plugin-with-no-dependencies"></a>Plug-in simple sans dépendances

De retour dans le dossier racine, effectuez les opérations suivantes :

1. Exécutez la commande suivante pour créer un projet de bibliothèque de classes nommé `HelloPlugin` :

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Exécutez la commande suivante pour ajouter le projet à la `AppWithPlugin` solution :

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. Remplacez le fichier *HelloPlugin/Class1.cs* par un fichier nommé *HelloCommand.cs* avec le contenu suivant :

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

Ouvrez maintenant le fichier *HelloPlugin.csproj*. Celui-ci doit se présenter comme suit :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net5</TargetFramework>
  </PropertyGroup>

</Project>

```

Entre les balises `<Project>`, ajoutez les éléments suivants :

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

L' `<Private>false</Private>` élément est important. Il indique à MSBuild de ne pas copier *PluginBase.dll* dans le répertoire de sortie de HelloPlugin. Si l’assembly *PluginBase.dll* est présent dans le répertoire de sortie, `PluginLoadContext` l’y trouvera et le chargera en même temps que l’assembly *HelloPlugin.dll*. À ce stade, le type `HelloPlugin.HelloCommand` implémentera l’interface `ICommand` de l’assembly *PluginBase.dll* situé dans le répertoire de sortie du projet `HelloPlugin`, et non l’interface `ICommand` qui est chargée dans le contexte de chargement par défaut. Étant donné que le runtime voit ces deux types comme des types différents de différents assemblys, la `AppWithPlugin.Program.CreateCommands` méthode ne trouvera pas les commandes. De ce fait, les métadonnées `<Private>false</Private>` ne sont pas nécessaires pour la référence à l’assembly contenant les interfaces de plug-in.

De même, l' `<ExcludeAssets>runtime</ExcludeAssets>` élément est également important si le `PluginBase` référence d’autres packages. Ce paramètre a le même effet que, `<Private>false</Private>` mais fonctionne sur les références de package que le `PluginBase` projet ou l’une de ses dépendances peut inclure.

Maintenant que le `HelloPlugin` projet est terminé, vous devez mettre à jour le `AppWithPlugin` projet pour savoir où se `HelloPlugin` trouve le plug-in. Après le `// Paths to plugins to load` commentaire, ajoutez `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` (ce chemin d’accès peut être différent selon la version de .net Core que vous utilisez) en tant qu’élément du `pluginPaths` tableau.

## <a name="plugin-with-library-dependencies"></a>Plug-in avec dépendances de bibliothèque

Les plug-ins sont presque tous plus complexes qu’un simple « Hello World », et bon nombre de plug-ins ont des dépendances vis-à-vis d’autres bibliothèques. Les projets de plug-in `JsonPlugin` et `OldJson` de l’exemple montrent deux exemples de plug-ins avec des packages NuGet qui dépendent de `Newtonsoft.Json`. Les fichiers projet eux-mêmes n’ont pas d’informations spéciales pour les références de projet et (après avoir ajouté les chemins du plug-in au `pluginPaths` tableau) les plug-ins s’exécutent parfaitement, même s’ils sont exécutés dans la même exécution de l’application AppWithPlugin. Toutefois, ces projets ne copient pas les assemblys référencés dans leur répertoire de sortie. par conséquent, les assemblys doivent être présents sur l’ordinateur de l’utilisateur pour que les plug-ins fonctionnent. Il existe deux façons de contourner ce problème. La première consiste à utiliser la commande `dotnet publish` pour publier la bibliothèque de classes. Autrement, si vous souhaitez pouvoir utiliser la sortie de `dotnet build` pour votre plug-in, vous pouvez ajouter la propriété `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` entre les balises `<PropertyGroup>` dans le fichier projet du plug-in. Pour obtenir un exemple, consultez le projet de plug-in `XcopyablePlugin`.

## <a name="other-examples-in-the-sample"></a>Autres exemples de l’exemple

La totalité du code source de ce tutoriel se trouve dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). L’exemple terminé comprend d’autres illustrations du comportement `AssemblyDependencyResolver`. Par exemple, l’objet `AssemblyDependencyResolver` peut aussi résoudre les bibliothèques natives ainsi que les assemblys satellites localisés inclus dans les packages NuGet. Dans le référentiel d’exemples, `UVPlugin` et `FrenchPlugin` illustrent ces scénarios.

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a>Référencer une interface de plug-in à partir d’un package NuGet

Supposons qu’il existe une application A dont l’interface de plug-in est définie dans le package NuGet nommé `A.PluginBase`. Comment référencer le package dans le projet de plug-in ? Pour les références de projet, l’utilisation des métadonnées `<Private>false</Private>` dans l’élément `ProjectReference` du fichier projet a empêché la copie de la dll dans la sortie.

Pour référencer correctement le package `A.PluginBase`, il convient de remplacer l’élément `<PackageReference>` dans le fichier projet par ce qui suit :

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Cela empêche la copie des assemblys `A.PluginBase` dans le répertoire de sortie du plug-in et garantit que celui-ci utilisera la version de `A.PluginBase` de l’application A.

## <a name="plugin-target-framework-recommendations"></a>Recommandations concernant le framework cible des plug-ins

Étant donné que le chargement des dépendances de plug-in utilise le *.deps.jssur* le fichier, il existe un piège lié au Framework cible du plug-in. Plus précisément, vos plug-ins doivent cibler un Runtime, tel que .NET 5, au lieu d’une version de .NET Standard. Le fichier *.deps.json* est généré en fonction du framework cible du projet, et comme de nombreux packages compatibles avec .NET Standard intègrent des assemblys de référence pour développer par rapport à .NET Standard et aux assemblys d’implémentation de runtimes spécifiques, il se peut que *.deps.json* ne voie pas correctement les assemblys d’implémentation ou qu’il s’empare de la version .NET Standard d’un assembly au lieu de la version .NET Core attendue.

## <a name="plugin-framework-references"></a>Références de l’infrastructure de plug-in

Actuellement, les plug-ins ne peuvent pas introduire de nouveaux frameworks dans le processus. Par exemple, vous ne pouvez pas charger un plug-in qui utilise le `Microsoft.AspNetCore.App` Framework dans une application qui utilise uniquement le `Microsoft.NETCore.App` Framework racine. L’application hôte doit déclarer des références à tous les frameworks requis par les plug-ins.
