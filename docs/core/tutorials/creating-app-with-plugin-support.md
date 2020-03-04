---
title: Créer une application .NET Core avec des plug-ins
description: Découvrez comment créer une application .NET Core qui prend en charge les plug-ins.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: eae792ddaa6655bfdcd932d3cb695f9dafa68130
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240842"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="42c0f-103">Créer une application .NET Core avec des plug-ins</span><span class="sxs-lookup"><span data-stu-id="42c0f-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="42c0f-104">Ce didacticiel vous montre comment créer un <xref:System.Runtime.Loader.AssemblyLoadContext> personnalisé pour charger les plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="42c0f-105">Un <xref:System.Runtime.Loader.AssemblyDependencyResolver> est utilisé pour résoudre les dépendances du plug-in.</span><span class="sxs-lookup"><span data-stu-id="42c0f-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="42c0f-106">Le didacticiel isole correctement les dépendances du plug-in à partir de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="42c0f-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="42c0f-107">Vous découvrirez comment effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="42c0f-107">You'll learn how to:</span></span>

- <span data-ttu-id="42c0f-108">Structurer un projet de façon à prendre en charge les plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="42c0f-109">Créer un <xref:System.Runtime.Loader.AssemblyLoadContext> personnalisé pour charger chaque plug-in.</span><span class="sxs-lookup"><span data-stu-id="42c0f-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="42c0f-110">Utiliser le type <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> pour permettre aux plug-ins d’avoir des dépendances.</span><span class="sxs-lookup"><span data-stu-id="42c0f-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="42c0f-111">Créer des plug-ins qui peuvent être facilement déployés en copiant simplement les artefacts de build.</span><span class="sxs-lookup"><span data-stu-id="42c0f-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42c0f-112">Composants requis</span><span class="sxs-lookup"><span data-stu-id="42c0f-112">Prerequisites</span></span>

- <span data-ttu-id="42c0f-113">Installez le [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download) ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="42c0f-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="42c0f-114">Création de l'application</span><span class="sxs-lookup"><span data-stu-id="42c0f-114">Create the application</span></span>

<span data-ttu-id="42c0f-115">La première étape consiste à créer l’application :</span><span class="sxs-lookup"><span data-stu-id="42c0f-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="42c0f-116">Créez un nouveau dossier et, dans ce dossier, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="42c0f-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="42c0f-117">Pour faciliter la création du projet, créez un fichier solution Visual Studio dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="42c0f-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="42c0f-118">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="42c0f-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="42c0f-119">Exécutez la commande suivante pour ajouter le projet d’application à la solution :</span><span class="sxs-lookup"><span data-stu-id="42c0f-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="42c0f-120">Vous pouvez maintenant compléter la structure de votre application.</span><span class="sxs-lookup"><span data-stu-id="42c0f-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="42c0f-121">Remplacez le code figurant dans le fichier *AppWithPlugin/Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="42c0f-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="42c0f-122">Créer les interfaces de plug-in</span><span class="sxs-lookup"><span data-stu-id="42c0f-122">Create the plugin interfaces</span></span>

<span data-ttu-id="42c0f-123">La prochaine étape de la procédure de création d’une application avec plug-ins consiste à définir l’interface que doivent implémenter les plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="42c0f-124">Nous vous suggérons de créer une bibliothèque de classes qui contient les types que vous prévoyez d’utiliser pour permettre la communication entre votre application et les plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="42c0f-125">Cette division vous permet de publier votre interface de plug-in en tant que package sans avoir à transmettre votre application complète.</span><span class="sxs-lookup"><span data-stu-id="42c0f-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="42c0f-126">Dans le dossier racine du projet, exécutez `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="42c0f-127">De même, exécutez `dotnet sln add PluginBase/PluginBase.csproj` pour ajouter le projet au fichier solution.</span><span class="sxs-lookup"><span data-stu-id="42c0f-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="42c0f-128">Supprimez le fichier `PluginBase/Class1.cs` et créez-en un nouveau dans le dossier `PluginBase` sous le nom `ICommand.cs` avec la définition d’interface suivante :</span><span class="sxs-lookup"><span data-stu-id="42c0f-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="42c0f-129">Cette interface `ICommand` est l’interface que tous les plug-ins vont implémenter.</span><span class="sxs-lookup"><span data-stu-id="42c0f-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="42c0f-130">Maintenant que l’interface `ICommand` est définie, le projet d’application peut être davantage complété.</span><span class="sxs-lookup"><span data-stu-id="42c0f-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="42c0f-131">Ajoutez une référence du projet `AppWithPlugin` au projet `PluginBase` avec la commande `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` à partir du dossier racine.</span><span class="sxs-lookup"><span data-stu-id="42c0f-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="42c0f-132">Remplacez le commentaire `// Load commands from plugins` par l’extrait de code suivant pour lui permettre de charger les plug-ins à partir des chemins de fichiers donnés :</span><span class="sxs-lookup"><span data-stu-id="42c0f-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="42c0f-133">Remplacez ensuite le commentaire `// Output the loaded commands` par l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="42c0f-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="42c0f-134">Remplacez le commentaire `// Execute the command with the name passed as an argument` par l’extrait suivant :</span><span class="sxs-lookup"><span data-stu-id="42c0f-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="42c0f-135">Et enfin, ajoutez à la classe `Program` les méthodes statiques nommées `LoadPlugin` et `CreateCommands`, comme indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="42c0f-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="42c0f-136">Charger les plug-ins</span><span class="sxs-lookup"><span data-stu-id="42c0f-136">Load plugins</span></span>

<span data-ttu-id="42c0f-137">Désormais, l’application peut charger et instancier correctement des commandes à partir d’assemblys de plug-in chargés, mais elle ne peut toujours pas charger les assemblys de plug-in.</span><span class="sxs-lookup"><span data-stu-id="42c0f-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="42c0f-138">Créez un fichier nommé *PluginLoadContext.cs* dans le dossier *AppWithPlugin* avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="42c0f-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="42c0f-139">Le type `PluginLoadContext` dérive de <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="42c0f-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="42c0f-140">Le type de `AssemblyLoadContext` est un type spécial dans le runtime qui permet aux développeurs d’isoler les assemblys chargés dans différents groupes pour s’assurer que les versions d’assembly ne sont pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="42c0f-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="42c0f-141">Par ailleurs, un `AssemblyLoadContext` personnalisé peut choisir les différents chemins à partir desquels les assemblys seront chargés et substituer le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="42c0f-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="42c0f-142">`PluginLoadContext` utilise une instance du type `AssemblyDependencyResolver` introduit dans .NET Core 3.0 pour résoudre les noms d’assembly en chemins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="42c0f-143">L’objet `AssemblyDependencyResolver` est construit avec le chemin d’une bibliothèque de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="42c0f-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="42c0f-144">Il résout les assemblys et les bibliothèques natives dans leurs chemins relatifs en se basant sur le fichier *.deps.json* de la bibliothèque de classes dont le chemin a été transmis au constructeur `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="42c0f-145">Le `AssemblyLoadContext` personnalisé permet aux plug-ins d’avoir leurs propres dépendances, tandis que `AssemblyDependencyResolver` facilite le chargement des dépendances.</span><span class="sxs-lookup"><span data-stu-id="42c0f-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="42c0f-146">Maintenant que le projet `AppWithPlugin` présente le type `PluginLoadContext`, mettez à jour la méthode `Program.LoadPlugin` avec le corps suivant :</span><span class="sxs-lookup"><span data-stu-id="42c0f-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="42c0f-147">En utilisant une instance `PluginLoadContext` différente pour chaque plug-in, les plug-ins peuvent avoir différentes dépendances, voire des dépendances en conflit sans que cela ne pose problème.</span><span class="sxs-lookup"><span data-stu-id="42c0f-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="42c0f-148">Plug-in simple sans dépendances</span><span class="sxs-lookup"><span data-stu-id="42c0f-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="42c0f-149">De retour dans le dossier racine, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="42c0f-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="42c0f-150">Exécutez la commande suivante pour créer un projet de bibliothèque de classes nommé `HelloPlugin`:</span><span class="sxs-lookup"><span data-stu-id="42c0f-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="42c0f-151">Exécutez la commande suivante pour ajouter le projet à la solution `AppWithPlugin` :</span><span class="sxs-lookup"><span data-stu-id="42c0f-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="42c0f-152">Remplacez le fichier *HelloPlugin/Class1.cs* par un fichier nommé *HelloCommand.cs* avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="42c0f-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="42c0f-153">Ouvrez maintenant le fichier *HelloPlugin.csproj*.</span><span class="sxs-lookup"><span data-stu-id="42c0f-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="42c0f-154">Celui-ci doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="42c0f-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="42c0f-155">Entre les balises `<Project>`, ajoutez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="42c0f-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="42c0f-156">L’élément `<Private>false</Private>` est important.</span><span class="sxs-lookup"><span data-stu-id="42c0f-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="42c0f-157">Il indique à MSBuild de ne pas copier *PluginBase.dll* dans le répertoire de sortie de HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="42c0f-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="42c0f-158">Si l’assembly *PluginBase.dll* est présent dans le répertoire de sortie, `PluginLoadContext` l’y trouvera et le chargera en même temps que l’assembly *HelloPlugin.dll*.</span><span class="sxs-lookup"><span data-stu-id="42c0f-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="42c0f-159">À ce stade, le type `HelloPlugin.HelloCommand` implémentera l’interface `ICommand` de l’assembly *PluginBase.dll* situé dans le répertoire de sortie du projet `HelloPlugin`, et non l’interface `ICommand` qui est chargée dans le contexte de chargement par défaut.</span><span class="sxs-lookup"><span data-stu-id="42c0f-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="42c0f-160">Étant donné que le runtime voit ces deux types comme des types différents de différents assemblys, la méthode `AppWithPlugin.Program.CreateCommands` ne trouvera pas les commandes.</span><span class="sxs-lookup"><span data-stu-id="42c0f-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="42c0f-161">De ce fait, les métadonnées `<Private>false</Private>` ne sont pas nécessaires pour la référence à l’assembly contenant les interfaces de plug-in.</span><span class="sxs-lookup"><span data-stu-id="42c0f-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="42c0f-162">De même, l’élément `<ExcludeAssets>runtime</ExcludeAssets>` est également important si le `PluginBase` fait référence à d’autres packages.</span><span class="sxs-lookup"><span data-stu-id="42c0f-162">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="42c0f-163">Ce paramètre a le même effet que `<Private>false</Private>`, mais fonctionne sur les références de package que le projet `PluginBase` ou l’une de ses dépendances peut inclure.</span><span class="sxs-lookup"><span data-stu-id="42c0f-163">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="42c0f-164">Maintenant que le projet de `HelloPlugin` est terminé, vous devez mettre à jour le projet `AppWithPlugin` pour savoir où se trouve le plug-in `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-164">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="42c0f-165">Après le commentaire `// Paths to plugins to load`, ajoutez `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` comme élément du tableau `pluginPaths`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-165">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="42c0f-166">Plug-in avec dépendances de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="42c0f-166">Plugin with library dependencies</span></span>

<span data-ttu-id="42c0f-167">Les plug-ins sont presque tous plus complexes qu’un simple « Hello World », et bon nombre de plug-ins ont des dépendances vis-à-vis d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="42c0f-167">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="42c0f-168">Les projets de plug-in `JsonPlugin` et `OldJson` de l’exemple montrent deux exemples de plug-ins avec des packages NuGet qui dépendent de `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-168">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="42c0f-169">Les fichiers projet eux-mêmes n’ont pas d’informations spéciales pour les références de projet et (après avoir ajouté les chemins du plug-in au tableau `pluginPaths`) les plug-ins s’exécutent parfaitement, même s’ils sont exécutés dans la même exécution de l’application AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="42c0f-169">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="42c0f-170">Toutefois, ces projets ne copient pas les assemblys référencés dans leur répertoire de sortie. par conséquent, les assemblys doivent être présents sur l’ordinateur de l’utilisateur pour que les plug-ins fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="42c0f-170">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="42c0f-171">Il existe deux façons de contourner ce problème.</span><span class="sxs-lookup"><span data-stu-id="42c0f-171">There are two ways to work around this problem.</span></span> <span data-ttu-id="42c0f-172">La première consiste à utiliser la commande `dotnet publish` pour publier la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="42c0f-172">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="42c0f-173">Autrement, si vous souhaitez pouvoir utiliser la sortie de `dotnet build` pour votre plug-in, vous pouvez ajouter la propriété `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` entre les balises `<PropertyGroup>` dans le fichier projet du plug-in.</span><span class="sxs-lookup"><span data-stu-id="42c0f-173">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="42c0f-174">Pour obtenir un exemple, consultez le projet de plug-in `XcopyablePlugin`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-174">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="42c0f-175">Autres exemples de l’exemple</span><span class="sxs-lookup"><span data-stu-id="42c0f-175">Other examples in the sample</span></span>

<span data-ttu-id="42c0f-176">La totalité du code source de ce tutoriel se trouve dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="42c0f-176">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="42c0f-177">L’exemple terminé comprend d’autres illustrations du comportement `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-177">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="42c0f-178">Par exemple, l’objet `AssemblyDependencyResolver` peut aussi résoudre les bibliothèques natives ainsi que les assemblys satellites localisés inclus dans les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="42c0f-178">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="42c0f-179">Dans le référentiel d’exemples, `UVPlugin` et `FrenchPlugin` illustrent ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="42c0f-179">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="42c0f-180">Référencer une interface de plug-in à partir d’un package NuGet</span><span class="sxs-lookup"><span data-stu-id="42c0f-180">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="42c0f-181">Supposons qu’il existe une application A dont l’interface de plug-in est définie dans le package NuGet nommé `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-181">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="42c0f-182">Comment référencer le package dans le projet de plug-in ?</span><span class="sxs-lookup"><span data-stu-id="42c0f-182">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="42c0f-183">Pour les références de projet, l’utilisation des métadonnées `<Private>false</Private>` dans l’élément `ProjectReference` du fichier projet a empêché la copie de la dll dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="42c0f-183">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="42c0f-184">Pour référencer correctement le package `A.PluginBase`, il convient de remplacer l’élément `<PackageReference>` dans le fichier projet par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="42c0f-184">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="42c0f-185">Cela empêche la copie des assemblys `A.PluginBase` dans le répertoire de sortie du plug-in et garantit que celui-ci utilisera la version de `A.PluginBase` de l’application A.</span><span class="sxs-lookup"><span data-stu-id="42c0f-185">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="42c0f-186">Recommandations concernant le framework cible des plug-ins</span><span class="sxs-lookup"><span data-stu-id="42c0f-186">Plugin target framework recommendations</span></span>

<span data-ttu-id="42c0f-187">Sachant que le chargement des dépendances de plug-in utilise le fichier *.deps.json*, il existe un piège lié au framework cible des plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-187">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="42c0f-188">Plus précisément, vos plug-ins doivent cibler un runtime, comme .NET Core 3.0, et non une version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="42c0f-188">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="42c0f-189">Le fichier *.deps.json* est généré en fonction du framework cible du projet, et comme de nombreux packages compatibles avec .NET Standard intègrent des assemblys de référence pour développer par rapport à .NET Standard et aux assemblys d’implémentation de runtimes spécifiques, il se peut que *.deps.json* ne voie pas correctement les assemblys d’implémentation ou qu’il s’empare de la version .NET Standard d’un assembly au lieu de la version .NET Core attendue.</span><span class="sxs-lookup"><span data-stu-id="42c0f-189">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="42c0f-190">Références de l’infrastructure de plug-in</span><span class="sxs-lookup"><span data-stu-id="42c0f-190">Plugin framework references</span></span>

<span data-ttu-id="42c0f-191">Actuellement, les plug-ins ne peuvent pas introduire de nouveaux frameworks dans le processus.</span><span class="sxs-lookup"><span data-stu-id="42c0f-191">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="42c0f-192">Par exemple, vous ne pouvez pas charger un plug-in qui utilise le Framework `Microsoft.AspNetCore.App` dans une application qui utilise uniquement l’infrastructure racine `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="42c0f-192">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="42c0f-193">L’application hôte doit déclarer des références à tous les frameworks requis par les plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42c0f-193">The host application must declare references to all frameworks needed by plugins.</span></span>
