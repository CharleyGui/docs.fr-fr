---
title: Bien démarrer avec .NET Core à l’aide de l’interface CLI
description: Un tutoriel étape par étape montrant comment commencer avec .NET Core sur Windows, Linux, ou macOS en utilisant le CLI .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240855"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="959c0-103">Démarrer avec .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="959c0-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="959c0-104">Cet article vous montrera comment commencer à développer des applications .NET Core qui fonctionnent sur Windows, Linux et macOS en utilisant le CLI Core .NET.</span><span class="sxs-lookup"><span data-stu-id="959c0-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="959c0-105">Si vous n’êtes pas familier avec le CLI de base .NET, voir la [vue d’ensemble .NET Core CLI](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="959c0-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="959c0-106">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="959c0-106">Prerequisites</span></span>

- <span data-ttu-id="959c0-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="959c0-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="959c0-108">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="959c0-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="959c0-109">Application console Hello</span><span class="sxs-lookup"><span data-stu-id="959c0-109">Hello, Console App!</span></span>

<span data-ttu-id="959c0-110">Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="959c0-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="959c0-111">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="959c0-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="959c0-112">Ouvrez une invite de commandes et créez un dossier nommé *Hello*.</span><span class="sxs-lookup"><span data-stu-id="959c0-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="959c0-113">Naviguez vers le dossier que vous avez créé et tapez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="959c0-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="959c0-114">Suivons une procédure pas à pas rapide :</span><span class="sxs-lookup"><span data-stu-id="959c0-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="959c0-115">[dotnet new](../tools/dotnet-new.md) crée un fichier de projet *Hello.csproj* à jour avec les dépendances nécessaires à la construction d’une application console.</span><span class="sxs-lookup"><span data-stu-id="959c0-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="959c0-116">Il crée également un *Program.cs*, un fichier de base contenant le point d’entrée pour l’application.</span><span class="sxs-lookup"><span data-stu-id="959c0-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="959c0-117">*Hello.csproj*:</span><span class="sxs-lookup"><span data-stu-id="959c0-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="959c0-118">Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.</span><span class="sxs-lookup"><span data-stu-id="959c0-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="959c0-119">L’élément `<OutputType>` spécifie que nous construisons une application exécutable, c’est-à-dire une application de console.</span><span class="sxs-lookup"><span data-stu-id="959c0-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="959c0-120">L’élément `<TargetFramework>` spécifie quelle mise en œuvre .NET nous ciblons.</span><span class="sxs-lookup"><span data-stu-id="959c0-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="959c0-121">Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération.</span><span class="sxs-lookup"><span data-stu-id="959c0-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="959c0-122">Dans ce tutoriel, nous allons nous en tenir à la construction que pour .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="959c0-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="959c0-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="959c0-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="959c0-124">Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ».</span><span class="sxs-lookup"><span data-stu-id="959c0-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="959c0-125">L’espace `System` de `Console` nom comprend la classe.</span><span class="sxs-lookup"><span data-stu-id="959c0-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="959c0-126">Ensuite, nous définissons un espace de noms appelé `Hello`.</span><span class="sxs-lookup"><span data-stu-id="959c0-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="959c0-127">Vous pouvez le modifier à votre gré.</span><span class="sxs-lookup"><span data-stu-id="959c0-127">You can change this to anything you want.</span></span> <span data-ttu-id="959c0-128">Une classe `Program` nommée est définie dans `Main` cet espace de nom, `args`avec une méthode qui prend un tableau de cordes nommées .</span><span class="sxs-lookup"><span data-stu-id="959c0-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="959c0-129">Ce tableau contient la liste des arguments adoptés lorsque le programme est exécuté.</span><span class="sxs-lookup"><span data-stu-id="959c0-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="959c0-130">Comme il est, ce tableau n’est pas utilisé et le programme écrit simplement le texte "Bonjour monde!"</span><span class="sxs-lookup"><span data-stu-id="959c0-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="959c0-131">dans la console.</span><span class="sxs-lookup"><span data-stu-id="959c0-131">to the console.</span></span> <span data-ttu-id="959c0-132">Plus tard, nous apporterons des modifications au code qui utilisent cet argument.</span><span class="sxs-lookup"><span data-stu-id="959c0-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="959c0-133">`dotnet new`appels [dotnet restaurer](../tools/dotnet-restore.md) implicitement.</span><span class="sxs-lookup"><span data-stu-id="959c0-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="959c0-134">`dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances.</span><span class="sxs-lookup"><span data-stu-id="959c0-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="959c0-135">NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="959c0-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="959c0-136">[dotnet exécuter](../tools/dotnet-run.md) les appels [dotnet construire](../tools/dotnet-build.md) pour s’assurer `dotnet <assembly.dll>` que les cibles de construction ont été construits, puis appelle pour exécuter l’application cible.</span><span class="sxs-lookup"><span data-stu-id="959c0-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="959c0-137">Vous obtenez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="959c0-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="959c0-138">Alternativement, vous pouvez `dotnet build` également exécuter pour compiler le code sans exécuter les applications de console de construction.</span><span class="sxs-lookup"><span data-stu-id="959c0-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="959c0-139">Il en résulte une application compilée, comme un fichier DLL, basé sur le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="959c0-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="959c0-140">Dans ce cas, le fichier créé est nommé *Hello.dll*.</span><span class="sxs-lookup"><span data-stu-id="959c0-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="959c0-141">Cette application peut `dotnet bin\Debug\netcoreapp3.1\Hello.dll` être exécutée `/` avec windows (utilisation pour les systèmes non Windows).</span><span class="sxs-lookup"><span data-stu-id="959c0-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="959c0-142">Vous obtenez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="959c0-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="959c0-143">Lorsque l’application est compilée, un système d’exploitation spécifique exécutable a été créé avec le `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="959c0-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="959c0-144">Sur Windows, ce `Hello.exe`serait ; sur Linux ou macOS, `hello`ce serait .</span><span class="sxs-lookup"><span data-stu-id="959c0-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="959c0-145">Avec l’exemple ci-dessus, `Hello.exe` `Hello`le fichier est nommé avec ou .</span><span class="sxs-lookup"><span data-stu-id="959c0-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="959c0-146">Vous pouvez exécuter ce exécutable directement.</span><span class="sxs-lookup"><span data-stu-id="959c0-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="959c0-147">Modifier le programme</span><span class="sxs-lookup"><span data-stu-id="959c0-147">Modify the program</span></span>

<span data-ttu-id="959c0-148">Modifions un peu le programme.</span><span class="sxs-lookup"><span data-stu-id="959c0-148">Let's change the program a bit.</span></span> <span data-ttu-id="959c0-149">Fibonacci nombres sont amusants, nous allons donc ajouter que et aussi d’utiliser l’argument pour saluer la personne en cours d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="959c0-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="959c0-150">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="959c0-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="959c0-151">Exécuter [dotnet construire](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="959c0-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="959c0-152">Exécutez le programme en passant un paramètre à l’application.</span><span class="sxs-lookup"><span data-stu-id="959c0-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="959c0-153">Lorsque vous `dotnet` utilisez la commande pour `--` exécuter une application, ajoutez à la fin.</span><span class="sxs-lookup"><span data-stu-id="959c0-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="959c0-154">Tout ce qui `--` est à droite sera transmis comme un paramètre à l’application.</span><span class="sxs-lookup"><span data-stu-id="959c0-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="959c0-155">Dans l’exemple suivant, la valeur `John` est transmise à l’application.</span><span class="sxs-lookup"><span data-stu-id="959c0-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="959c0-156">Vous obtenez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="959c0-156">You get the following output.</span></span>

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

<span data-ttu-id="959c0-157">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="959c0-157">And that's it!</span></span> <span data-ttu-id="959c0-158">Vous pouvez modifier *Program.cs* comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="959c0-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="959c0-159">Utilisation de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="959c0-159">Working with multiple files</span></span>

<span data-ttu-id="959c0-160">Les fichiers simples sont très bien pour les programmes simples et uniques, mais si vous construisez une application plus complexe, vous allez probablement avoir plusieurs fichiers de code sur votre projet.</span><span class="sxs-lookup"><span data-stu-id="959c0-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="959c0-161">Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.</span><span class="sxs-lookup"><span data-stu-id="959c0-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="959c0-162">Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="959c0-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="959c0-163">Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="959c0-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="959c0-164">Exécuter [dotnet construire](../tools/dotnet-build.md) pour compiler les modifications.</span><span class="sxs-lookup"><span data-stu-id="959c0-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="959c0-165">Exécutez votre application en exécutant [dotnet exécuter](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="959c0-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="959c0-166">Vous obtenez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="959c0-166">You get the following output.</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="959c0-167">Publier votre application</span><span class="sxs-lookup"><span data-stu-id="959c0-167">Publish your app</span></span>

<span data-ttu-id="959c0-168">Une fois que vous êtes prêt à distribuer votre application, utilisez la commande [de publication dotnet](../tools/dotnet-publish.md) pour générer `/` le dossier de _publication_ à _\\bin\\debug netcoreapp3.1\\publier\\ _ (utilisation pour les systèmes non Windows).</span><span class="sxs-lookup"><span data-stu-id="959c0-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="959c0-169">Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.</span><span class="sxs-lookup"><span data-stu-id="959c0-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="959c0-170">Vous obtenez la sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="959c0-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="959c0-171">La sortie ci-dessus peut différer en fonction de votre dossier actuel et le système d’exploitation, mais la sortie doit être similaire.</span><span class="sxs-lookup"><span data-stu-id="959c0-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="959c0-172">Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="959c0-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="959c0-173">Vous obtenez la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="959c0-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="959c0-174">Comme mentionné au début de cet article, un système d’exploitation spécifique exécutable a été créé avec le `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="959c0-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="959c0-175">Sur Windows, ce `Hello.exe`serait ; sur Linux ou macOS, `hello`ce serait .</span><span class="sxs-lookup"><span data-stu-id="959c0-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="959c0-176">Avec l’exemple ci-dessus, `Hello.exe` `Hello`le fichier est nommé avec ou .</span><span class="sxs-lookup"><span data-stu-id="959c0-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="959c0-177">Vous pouvez exécuter ce publiable directement.</span><span class="sxs-lookup"><span data-stu-id="959c0-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="959c0-178">Conclusion</span><span class="sxs-lookup"><span data-stu-id="959c0-178">Conclusion</span></span>

<span data-ttu-id="959c0-179">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="959c0-179">And that's it!</span></span> <span data-ttu-id="959c0-180">À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.</span><span class="sxs-lookup"><span data-stu-id="959c0-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="959c0-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="959c0-181">See also</span></span>

- [<span data-ttu-id="959c0-182">Organisation et test de projets avec le CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="959c0-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="959c0-183">Publier des applications .NET Core avec le CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="959c0-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="959c0-184">.NET Déploiement d’applications de base</span><span class="sxs-lookup"><span data-stu-id="959c0-184">.NET Core application deployment</span></span>](../deploying/index.md)
