---
title: Bien démarrer avec .NET Core à l’aide de l’interface CLI
description: Un didacticiel pas à pas expliquant comment prendre en main .NET Core sur Windows, Linux ou macOS à l’aide de l’CLI .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240855"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="87621-103">Prise en main de .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="87621-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="87621-104">Cet article vous montre comment commencer à développer des applications .NET Core qui fonctionnent sur Windows, Linux et macOS à l’aide de l’CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87621-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="87621-105">Si vous n’êtes pas familiarisé avec le CLI .NET Core, consultez la [vue d’ensemble de CLI .net Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="87621-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87621-106">Composants requis</span><span class="sxs-lookup"><span data-stu-id="87621-106">Prerequisites</span></span>

- <span data-ttu-id="87621-107">[Kit SDK .NET Core 3,1](https://dotnet.microsoft.com/download) ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="87621-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="87621-108">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="87621-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="87621-109">Application console Hello</span><span class="sxs-lookup"><span data-stu-id="87621-109">Hello, Console App!</span></span>

<span data-ttu-id="87621-110">Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="87621-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="87621-111">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="87621-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="87621-112">Ouvrez une invite de commandes et créez un dossier nommé *Hello*.</span><span class="sxs-lookup"><span data-stu-id="87621-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="87621-113">Accédez au dossier que vous avez créé et tapez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="87621-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="87621-114">Suivons une procédure pas à pas rapide :</span><span class="sxs-lookup"><span data-stu-id="87621-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="87621-115">[dotnet New](../tools/dotnet-new.md) crée un fichier projet *Hello. csproj* à jour avec les dépendances nécessaires à la création d’une application console.</span><span class="sxs-lookup"><span data-stu-id="87621-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="87621-116">Il crée également un *Program.cs*, un fichier de base contenant le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="87621-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="87621-117">*Bonjour. csproj*:</span><span class="sxs-lookup"><span data-stu-id="87621-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="87621-118">Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.</span><span class="sxs-lookup"><span data-stu-id="87621-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="87621-119">L’élément `<OutputType>` spécifie que nous créons un exécutable, en d’autres termes une application console.</span><span class="sxs-lookup"><span data-stu-id="87621-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="87621-120">L’élément `<TargetFramework>` spécifie l’implémentation .NET que nous ciblons.</span><span class="sxs-lookup"><span data-stu-id="87621-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="87621-121">Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération.</span><span class="sxs-lookup"><span data-stu-id="87621-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="87621-122">Dans ce didacticiel, nous allons nous contenter de créer uniquement pour .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="87621-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="87621-123">*Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="87621-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="87621-124">Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ».</span><span class="sxs-lookup"><span data-stu-id="87621-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="87621-125">L’espace de noms `System` comprend la classe `Console`.</span><span class="sxs-lookup"><span data-stu-id="87621-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="87621-126">Ensuite, nous définissons un espace de noms appelé `Hello`.</span><span class="sxs-lookup"><span data-stu-id="87621-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="87621-127">Vous pouvez le modifier à votre gré.</span><span class="sxs-lookup"><span data-stu-id="87621-127">You can change this to anything you want.</span></span> <span data-ttu-id="87621-128">Une classe nommée `Program` est définie dans cet espace de noms, avec une méthode `Main` qui prend un tableau de chaînes nommé `args`.</span><span class="sxs-lookup"><span data-stu-id="87621-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="87621-129">Ce tableau contient la liste des arguments passés lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="87621-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="87621-130">Comme c’est le cas, ce tableau n’est pas utilisé et le programme écrit simplement le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="87621-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="87621-131">dans la console.</span><span class="sxs-lookup"><span data-stu-id="87621-131">to the console.</span></span> <span data-ttu-id="87621-132">Plus tard, nous apporterons des modifications au code qui utilisent cet argument.</span><span class="sxs-lookup"><span data-stu-id="87621-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="87621-133">`dotnet new` appelle [dotnet Restore](../tools/dotnet-restore.md) implicitement.</span><span class="sxs-lookup"><span data-stu-id="87621-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="87621-134">`dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances.</span><span class="sxs-lookup"><span data-stu-id="87621-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="87621-135">NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="87621-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="87621-136">[dotnet Run](../tools/dotnet-run.md) appelle [dotnet Build](../tools/dotnet-build.md) pour s’assurer que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.</span><span class="sxs-lookup"><span data-stu-id="87621-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="87621-137">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="87621-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="87621-138">Vous pouvez également exécuter `dotnet build` pour compiler le code sans exécuter les applications console de génération.</span><span class="sxs-lookup"><span data-stu-id="87621-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="87621-139">Il en résulte une application compilée, sous la forme d’un fichier DLL, en fonction du nom du projet.</span><span class="sxs-lookup"><span data-stu-id="87621-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="87621-140">Dans ce cas, le fichier créé est nommé *Hello. dll*.</span><span class="sxs-lookup"><span data-stu-id="87621-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="87621-141">Cette application peut être exécutée avec `dotnet bin\Debug\netcoreapp3.1\Hello.dll` sur Windows (utilisez `/` pour les systèmes non-Windows).</span><span class="sxs-lookup"><span data-stu-id="87621-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="87621-142">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="87621-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="87621-143">Lorsque l’application est compilée, un fichier exécutable spécifique au système d’exploitation a été créé avec l' `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="87621-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="87621-144">Sur Windows, ce serait `Hello.exe`; sur Linux ou macOS, ce serait `hello`.</span><span class="sxs-lookup"><span data-stu-id="87621-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="87621-145">Dans l’exemple ci-dessus, le fichier est nommé avec `Hello.exe` ou `Hello`.</span><span class="sxs-lookup"><span data-stu-id="87621-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="87621-146">Vous pouvez exécuter cet exécutable directement.</span><span class="sxs-lookup"><span data-stu-id="87621-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="87621-147">Modifier le programme</span><span class="sxs-lookup"><span data-stu-id="87621-147">Modify the program</span></span>

<span data-ttu-id="87621-148">Modifions un peu le programme.</span><span class="sxs-lookup"><span data-stu-id="87621-148">Let's change the program a bit.</span></span> <span data-ttu-id="87621-149">Les nombres Fibonacci sont amusants. nous allons donc l’ajouter et également utiliser l’argument pour accueillir la personne qui exécute l’application.</span><span class="sxs-lookup"><span data-stu-id="87621-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="87621-150">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="87621-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="87621-151">Exécutez [dotnet Build](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="87621-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="87621-152">Exécutez le programme en passant un paramètre à l’application.</span><span class="sxs-lookup"><span data-stu-id="87621-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="87621-153">Lorsque vous utilisez la commande `dotnet` pour exécuter une application, ajoutez `--` à la fin.</span><span class="sxs-lookup"><span data-stu-id="87621-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="87621-154">Tout ce qui se trouve à droite de `--` est passé en tant que paramètre à l’application.</span><span class="sxs-lookup"><span data-stu-id="87621-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="87621-155">Dans l’exemple suivant, la valeur `John` est passée à l’application.</span><span class="sxs-lookup"><span data-stu-id="87621-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="87621-156">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="87621-156">You get the following output.</span></span>

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

<span data-ttu-id="87621-157">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="87621-157">And that's it!</span></span> <span data-ttu-id="87621-158">Vous pouvez modifier *Program.cs* comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="87621-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="87621-159">Utilisation de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="87621-159">Working with multiple files</span></span>

<span data-ttu-id="87621-160">Les fichiers uniques conviennent parfaitement aux programmes simples et uniques, mais si vous créez une application plus complexe, vous aurez probablement plusieurs fichiers de code sur votre projet.</span><span class="sxs-lookup"><span data-stu-id="87621-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="87621-161">Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.</span><span class="sxs-lookup"><span data-stu-id="87621-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="87621-162">Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="87621-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="87621-163">Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="87621-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="87621-164">Exécutez [dotnet Build](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="87621-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="87621-165">Exécutez votre application en exécutant [dotnet Run](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="87621-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="87621-166">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="87621-166">You get the following output.</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="87621-167">Publier une application</span><span class="sxs-lookup"><span data-stu-id="87621-167">Publish your app</span></span>

<span data-ttu-id="87621-168">Une fois que vous êtes prêt à distribuer votre application, utilisez la commande [dotnet Publish](../tools/dotnet-publish.md) pour générer le dossier de _publication_ dans _bin\\Debug\\netcoreapp 3.1\\Publish\\_ (utilisez `/` pour les systèmes non-Windows).</span><span class="sxs-lookup"><span data-stu-id="87621-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="87621-169">Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.</span><span class="sxs-lookup"><span data-stu-id="87621-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="87621-170">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="87621-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="87621-171">La sortie ci-dessus peut varier en fonction de votre dossier actuel et du système d’exploitation, mais la sortie doit être similaire.</span><span class="sxs-lookup"><span data-stu-id="87621-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="87621-172">Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="87621-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="87621-173">Vous recevez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="87621-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="87621-174">Comme mentionné au début de cet article, un fichier exécutable spécifique au système d’exploitation a été créé avec l' `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="87621-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="87621-175">Sur Windows, ce serait `Hello.exe`; sur Linux ou macOS, ce serait `hello`.</span><span class="sxs-lookup"><span data-stu-id="87621-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="87621-176">Dans l’exemple ci-dessus, le fichier est nommé avec `Hello.exe` ou `Hello`.</span><span class="sxs-lookup"><span data-stu-id="87621-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="87621-177">Vous pouvez exécuter ce fichier exécutable publié directement.</span><span class="sxs-lookup"><span data-stu-id="87621-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="87621-178">Conclusion</span><span class="sxs-lookup"><span data-stu-id="87621-178">Conclusion</span></span>

<span data-ttu-id="87621-179">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="87621-179">And that's it!</span></span> <span data-ttu-id="87621-180">À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.</span><span class="sxs-lookup"><span data-stu-id="87621-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="87621-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87621-181">See also</span></span>

- [<span data-ttu-id="87621-182">Organisation et test de projets avec la CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="87621-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="87621-183">Publier des applications .NET Core avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="87621-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="87621-184">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="87621-184">.NET Core application deployment</span></span>](../deploying/index.md)
