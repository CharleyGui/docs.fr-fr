---
title: Bien démarrer avec .NET Core à l’aide de l’interface CLI
description: Didacticiel pas à pas montrant comment démarrer avec .NET Core sur Windows, Linux ou Mac OS à l’aide de l’interface de ligne de commande (CLI) .NET Core.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: a680a4b58927d915e887eea43a72983a5b349682
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105058"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="d355e-103">Bien démarrer avec .NET Core sur Windows/Linux/macOS en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="d355e-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="d355e-104">Cette rubrique décrit comment commencer à développer des applications multiplateformes sur votre ordinateur à l’aide des outils CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d355e-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="d355e-105">Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d355e-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d355e-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d355e-106">Prerequisites</span></span>

- <span data-ttu-id="d355e-107">[.NET Core SDK 2.1](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="d355e-107">[.NET Core SDK 2.1](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="d355e-108">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="d355e-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="d355e-109">Application console Hello</span><span class="sxs-lookup"><span data-stu-id="d355e-109">Hello, Console App!</span></span>

<span data-ttu-id="d355e-110">Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="d355e-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="d355e-111">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d355e-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="d355e-112">Ouvrez une invite de commandes et créez un dossier nommé *Hello*.</span><span class="sxs-lookup"><span data-stu-id="d355e-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="d355e-113">Accédez au dossier créé et tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d355e-113">Navigate to the folder you created and type the following:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="d355e-114">Suivons une procédure pas à pas rapide :</span><span class="sxs-lookup"><span data-stu-id="d355e-114">Let's do a quick walkthrough:</span></span>

1. `dotnet new console`

   <span data-ttu-id="d355e-115">[`dotnet new`](../tools/dotnet-new.md) crée un fichier projet `Hello.csproj` à jour avec les dépendances nécessaires pour générer une application console.</span><span class="sxs-lookup"><span data-stu-id="d355e-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="d355e-116">Il crée également `Program.cs`, un fichier de base contenant le point d’entrée pour l’application.</span><span class="sxs-lookup"><span data-stu-id="d355e-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="d355e-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="d355e-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="d355e-118">Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.</span><span class="sxs-lookup"><span data-stu-id="d355e-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   - <span data-ttu-id="d355e-119">La balise `OutputType` spécifie que nous générons un fichier exécutable, autrement dit une application console.</span><span class="sxs-lookup"><span data-stu-id="d355e-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   - <span data-ttu-id="d355e-120">La balise `TargetFramework` spécifie l’implémentation .NET que nous ciblons.</span><span class="sxs-lookup"><span data-stu-id="d355e-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="d355e-121">Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération.</span><span class="sxs-lookup"><span data-stu-id="d355e-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="d355e-122">Dans ce tutoriel, nous nous en tiendrons à une génération limitée à .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="d355e-122">In this tutorial, we'll stick to building only for .NET Core 2.1.</span></span>

   <span data-ttu-id="d355e-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="d355e-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="d355e-124">Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ».</span><span class="sxs-lookup"><span data-stu-id="d355e-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="d355e-125">L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.</span><span class="sxs-lookup"><span data-stu-id="d355e-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="d355e-126">Ensuite, nous définissons un espace de noms appelé `Hello`.</span><span class="sxs-lookup"><span data-stu-id="d355e-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="d355e-127">Vous pouvez le modifier à votre gré.</span><span class="sxs-lookup"><span data-stu-id="d355e-127">You can change this to anything you want.</span></span> <span data-ttu-id="d355e-128">Une classe nommée `Program` est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument.</span><span class="sxs-lookup"><span data-stu-id="d355e-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="d355e-129">Ce tableau contient la liste des arguments passés quand le programme compilé est appelé.</span><span class="sxs-lookup"><span data-stu-id="d355e-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="d355e-130">Tel quel, ce tableau n’est pas utilisé : le programme se limite à écrire « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="d355e-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="d355e-131">dans la console.</span><span class="sxs-lookup"><span data-stu-id="d355e-131">to the console.</span></span> <span data-ttu-id="d355e-132">Plus tard, nous apporterons des modifications au code qui utilisent cet argument.</span><span class="sxs-lookup"><span data-stu-id="d355e-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   <span data-ttu-id="d355e-133">`dotnet new` appelle [`dotnet restore`](../tools/dotnet-restore.md) implicitement.</span><span class="sxs-lookup"><span data-stu-id="d355e-133">`dotnet new` calls [`dotnet restore`](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="d355e-134">`dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances.</span><span class="sxs-lookup"><span data-stu-id="d355e-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="d355e-135">NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d355e-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="d355e-136">Si vous utilisez une version .NET Core 1.x du SDK, vous devrez appeler `dotnet restore` vous-même après l’appel de `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="d355e-136">If you're using a .NET Core 1.x version of the SDK, you'll have to call `dotnet restore` yourself after calling `dotnet new`.</span></span>

2. `dotnet run`

   <span data-ttu-id="d355e-137">[`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour garantir que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.</span><span class="sxs-lookup"><span data-stu-id="d355e-137">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="d355e-138">Si vous préférez, vous pouvez exécuter [`dotnet build`](../tools/dotnet-build.md) pour compiler le code sans exécuter les applications console de la build.</span><span class="sxs-lookup"><span data-stu-id="d355e-138">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="d355e-139">Il en résulte une application compilée sous forme de fichier DLL qui peut être exécutée avec `dotnet bin\Debug\netcoreapp2.1\Hello.dll` sur Windows (utilisez `/` sur les autres systèmes).</span><span class="sxs-lookup"><span data-stu-id="d355e-139">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp2.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="d355e-140">Vous pouvez également spécifier des arguments pour l’application, comme nous le verrons par la suite dans la rubrique.</span><span class="sxs-lookup"><span data-stu-id="d355e-140">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="d355e-141">Dans le cadre d’un scénario avancé, vous pouvez générer l’application comme un ensemble autonome de fichiers spécifiques à la plateforme qui peuvent être déployés et exécutés sur un ordinateur sur lequel .NET Core n’est pas nécessairement installé.</span><span class="sxs-lookup"><span data-stu-id="d355e-141">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="d355e-142">Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d355e-142">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="d355e-143">Augmentation du programme</span><span class="sxs-lookup"><span data-stu-id="d355e-143">Augmenting the program</span></span>

<span data-ttu-id="d355e-144">Modifions un peu le programme.</span><span class="sxs-lookup"><span data-stu-id="d355e-144">Let's change the program a bit.</span></span> <span data-ttu-id="d355e-145">Les nombres de Fibonacci sont amusants, nous allons donc les ajouter en plus de l’argument pour accueillir la personne qui exécute l’application.</span><span class="sxs-lookup"><span data-stu-id="d355e-145">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="d355e-146">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d355e-146">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="d355e-147">Exécutez [`dotnet build`](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="d355e-147">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="d355e-148">Exécutez le programme en passant un paramètre à l’application :</span><span class="sxs-lookup"><span data-stu-id="d355e-148">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="d355e-149">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="d355e-149">And that's it!</span></span>  <span data-ttu-id="d355e-150">Vous pouvez augmenter `Program.cs` comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="d355e-150">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="d355e-151">Utilisation de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="d355e-151">Working with multiple files</span></span>

<span data-ttu-id="d355e-152">Les fichiers uniques conviennent à des programmes simples et ponctuels, mais si vous créez une application plus complexe, vous avez probablement plusieurs fichiers sources dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="d355e-152">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project.</span></span>
<span data-ttu-id="d355e-153">Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.</span><span class="sxs-lookup"><span data-stu-id="d355e-153">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="d355e-154">Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d355e-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="d355e-155">Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d355e-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="d355e-156">Exécutez [`dotnet build`](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="d355e-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="d355e-157">Exécutez votre application en exécutant [`dotnet run`](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="d355e-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="d355e-158">Voici la sortie du programme :</span><span class="sxs-lookup"><span data-stu-id="d355e-158">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="d355e-159">Publier votre application</span><span class="sxs-lookup"><span data-stu-id="d355e-159">Publish your app</span></span>

<span data-ttu-id="d355e-160">Lorsque vous êtes prêt à distribuer votre application, utilisez la commande [`dotnet publish`](../tools/dotnet-publish.md) pour générer le dossier _publish_ dans _bin\\debug\\netcoreapp2.1\\publish\\_ (utilisez `/` pour les systèmes non Windows).</span><span class="sxs-lookup"><span data-stu-id="d355e-160">Once you're ready to distribute your app, use the [`dotnet publish`](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp2.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="d355e-161">Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.</span><span class="sxs-lookup"><span data-stu-id="d355e-161">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

<span data-ttu-id="d355e-162">Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="d355e-162">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="d355e-163">Conclusion</span><span class="sxs-lookup"><span data-stu-id="d355e-163">Conclusion</span></span>

<span data-ttu-id="d355e-164">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="d355e-164">And that's it!</span></span> <span data-ttu-id="d355e-165">À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.</span><span class="sxs-lookup"><span data-stu-id="d355e-165">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d355e-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d355e-166">See also</span></span>

- [<span data-ttu-id="d355e-167">Organisation et test de projets avec les outils CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="d355e-167">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="d355e-168">Publier des applications .NET Core avec l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="d355e-168">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="d355e-169">Pour en savoir plus sur le déploiement</span><span class="sxs-lookup"><span data-stu-id="d355e-169">Learn more about app deployment</span></span>](../deploying/index.md)
