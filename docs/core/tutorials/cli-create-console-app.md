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
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="0c2b3-103">Bien démarrer avec .NET Core sur Windows/Linux/macOS en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="0c2b3-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="0c2b3-104">Cet article vous montre comment commencer à développer des applications multiplateformes sur votre ordinateur à l’aide des outils de CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-104">This article will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="0c2b3-105">Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c2b3-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c2b3-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="0c2b3-106">Prerequisites</span></span>

- <span data-ttu-id="0c2b3-107">[Kit SDK .NET Core 3,1](https://dotnet.microsoft.com/download) ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="0c2b3-108">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="0c2b3-109">Application console Hello</span><span class="sxs-lookup"><span data-stu-id="0c2b3-109">Hello, Console App!</span></span>

<span data-ttu-id="0c2b3-110">Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="0c2b3-111">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0c2b3-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="0c2b3-112">Ouvrez une invite de commandes et créez un dossier nommé *Hello*.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="0c2b3-113">Accédez au dossier créé et tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-113">Navigate to the folder you created and type the following:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="0c2b3-114">Suivons une procédure pas à pas rapide :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="0c2b3-115">[dotnet New](../tools/dotnet-new.md) crée un fichier projet *Hello. csproj* à jour avec les dépendances nécessaires à la création d’une application console.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="0c2b3-116">Il crée également un *Program.cs*, un fichier de base contenant le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>
    
    <span data-ttu-id="0c2b3-117">*Bonjour. csproj*:</span><span class="sxs-lookup"><span data-stu-id="0c2b3-117">*Hello.csproj*:</span></span>
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    <span data-ttu-id="0c2b3-118">Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>
    
    - <span data-ttu-id="0c2b3-119">L’élément `<OutputType>` spécifie que nous créons un exécutable, en d’autres termes une application console.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="0c2b3-120">L’élément `<TargetFramework>` spécifie l’implémentation .NET que nous ciblons.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="0c2b3-121">Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="0c2b3-122">Dans ce didacticiel, nous allons nous contenter de créer uniquement pour .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>
    
    <span data-ttu-id="0c2b3-123">*Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-123">*Program.cs*:</span></span>
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    <span data-ttu-id="0c2b3-124">Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ».</span><span class="sxs-lookup"><span data-stu-id="0c2b3-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="0c2b3-125">L’espace de noms `System` comprend la classe `Console`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-125">The `System` namespace includes the `Console` class.</span></span>
    
    <span data-ttu-id="0c2b3-126">Ensuite, nous définissons un espace de noms appelé `Hello`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="0c2b3-127">Vous pouvez le modifier à votre gré.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-127">You can change this to anything you want.</span></span> <span data-ttu-id="0c2b3-128">Une classe nommée `Program` est définie dans cet espace de noms, avec une méthode `Main` qui prend un tableau de chaînes nommé `args`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="0c2b3-129">Ce tableau contient la liste des arguments passés lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="0c2b3-130">Comme c’est le cas, ce tableau n’est pas utilisé et le programme écrit simplement le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="0c2b3-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="0c2b3-131">dans la console.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-131">to the console.</span></span> <span data-ttu-id="0c2b3-132">Plus tard, nous apporterons des modifications au code qui utilisent cet argument.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-132">Later, we'll make changes to the code that will make use of this argument.</span></span>
    
    <span data-ttu-id="0c2b3-133">`dotnet new` appelle [dotnet Restore](../tools/dotnet-restore.md) implicitement.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="0c2b3-134">`dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="0c2b3-135">NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="0c2b3-136">[dotnet Run](../tools/dotnet-run.md) appelle [dotnet Build](../tools/dotnet-build.md) pour s’assurer que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
    
    ```console
    dotnet run

    Hello World!
    ```
    
    <span data-ttu-id="0c2b3-137">Vous pouvez également exécuter `dotnet build` pour compiler le code sans exécuter les applications console de génération.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-137">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="0c2b3-138">Il en résulte une application compilée, sous la forme d’un fichier DLL, en fonction du nom du projet.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-138">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="0c2b3-139">Dans ce cas, le fichier créé est nommé *Hello. dll*.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-139">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="0c2b3-140">Cette application peut être exécutée avec `dotnet bin\Debug\netcoreapp3.1\Hello.dll` sur Windows (utilisez `/` pour les systèmes non-Windows).</span><span class="sxs-lookup"><span data-stu-id="0c2b3-140">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    <span data-ttu-id="0c2b3-141">Lorsque l’application est compilée, un fichier exécutable spécifique au système d’exploitation a été créé avec l' `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-141">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="0c2b3-142">Sur Windows, ce serait `Hello.exe`; sur Linux ou macOS, ce serait `hello`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-142">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="0c2b3-143">Dans l’exemple ci-dessus, le fichier est nommé avec `Hello.exe` ou `Hello`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-143">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="0c2b3-144">Vous pouvez exécuter cet exécutable directement.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-144">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="0c2b3-145">Modifier le programme</span><span class="sxs-lookup"><span data-stu-id="0c2b3-145">Modify the program</span></span>

<span data-ttu-id="0c2b3-146">Modifions un peu le programme.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-146">Let's change the program a bit.</span></span> <span data-ttu-id="0c2b3-147">Les nombres Fibonacci sont amusants. nous allons donc l’ajouter et également utiliser l’argument pour accueillir la personne qui exécute l’application.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-147">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="0c2b3-148">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-148">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. <span data-ttu-id="0c2b3-149">Exécutez [dotnet Build](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-149">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="0c2b3-150">Exécutez le programme en passant un paramètre à l’application.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-150">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="0c2b3-151">Lorsque vous utilisez la commande `dotnet` pour exécuter une application, ajoutez `--` à la fin.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-151">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="0c2b3-152">Tout ce qui se trouve à droite de `--` est passé en tant que paramètre à l’application.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-152">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="0c2b3-153">Dans l’exemple suivant, la valeur `John` est passée à l’application.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-153">In the following example, the value `John` is passed to the app.</span></span>

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

<span data-ttu-id="0c2b3-154">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="0c2b3-154">And that's it!</span></span> <span data-ttu-id="0c2b3-155">Vous pouvez modifier *Program.cs* comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-155">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="0c2b3-156">Utilisation de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="0c2b3-156">Working with multiple files</span></span>

<span data-ttu-id="0c2b3-157">Les fichiers uniques conviennent parfaitement aux programmes simples et uniques, mais si vous créez une application plus complexe, vous aurez probablement plusieurs fichiers de code sur votre projet.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-157">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="0c2b3-158">Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-158">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="0c2b3-159">Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-159">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. <span data-ttu-id="0c2b3-160">Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-160">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. <span data-ttu-id="0c2b3-161">Exécutez [dotnet Build](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-161">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="0c2b3-162">Exécutez votre application en exécutant [dotnet Run](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="0c2b3-162">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span> <span data-ttu-id="0c2b3-163">Voici la sortie du programme :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-163">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="0c2b3-164">Publier une application</span><span class="sxs-lookup"><span data-stu-id="0c2b3-164">Publish your app</span></span>

<span data-ttu-id="0c2b3-165">Une fois que vous êtes prêt à distribuer votre application, utilisez la commande [dotnet Publish](../tools/dotnet-publish.md) pour générer le dossier de _publication_ dans _bin\\Debug\\netcoreapp 3.1\\Publish\\_ (utilisez `/` pour les systèmes non-Windows).</span><span class="sxs-lookup"><span data-stu-id="0c2b3-165">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="0c2b3-166">Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-166">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="0c2b3-167">La sortie ci-dessus peut varier en fonction de votre dossier actuel et du système d’exploitation, mais la sortie doit être similaire.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-167">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="0c2b3-168">Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="0c2b3-168">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

<span data-ttu-id="0c2b3-169">Comme mentionné au début de cet article, un fichier exécutable spécifique au système d’exploitation a été créé avec l' `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-169">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="0c2b3-170">Sur Windows, ce serait `Hello.exe`; sur Linux ou macOS, ce serait `hello`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-170">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="0c2b3-171">Dans l’exemple ci-dessus, le fichier est nommé avec `Hello.exe` ou `Hello`.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-171">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="0c2b3-172">Vous pouvez exécuter ce fichier exécutable publié directement.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-172">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="0c2b3-173">Conclusion</span><span class="sxs-lookup"><span data-stu-id="0c2b3-173">Conclusion</span></span>

<span data-ttu-id="0c2b3-174">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="0c2b3-174">And that's it!</span></span> <span data-ttu-id="0c2b3-175">À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.</span><span class="sxs-lookup"><span data-stu-id="0c2b3-175">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c2b3-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c2b3-176">See also</span></span>

- [<span data-ttu-id="0c2b3-177">Organisation et test de projets avec les outils CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="0c2b3-177">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="0c2b3-178">Publier des applications .NET Core avec l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="0c2b3-178">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="0c2b3-179">Pour en savoir plus sur le déploiement</span><span class="sxs-lookup"><span data-stu-id="0c2b3-179">Learn more about app deployment</span></span>](../deploying/index.md)
