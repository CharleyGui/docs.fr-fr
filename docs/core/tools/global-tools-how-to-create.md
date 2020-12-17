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
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="5b9bf-104">Didacticiel : créer un outil .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="5b9bf-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="5b9bf-105">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5b9bf-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="5b9bf-106">Ce didacticiel vous apprend à créer et à empaqueter un outil .NET.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="5b9bf-107">L’interface de commande .NET vous permet de créer une application console en tant qu’outil, que d’autres peuvent installer et exécuter.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="5b9bf-108">Les outils .NET sont des packages NuGet qui sont installés à partir de l’interface CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="5b9bf-109">Pour plus d’informations sur les outils, consultez [vue d’ensemble des outils .net](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5b9bf-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="5b9bf-110">L’outil que vous allez créer est une application console qui accepte un message comme entrée et affiche le message avec des lignes de texte qui créent l’image d’un robot.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="5b9bf-111">Il s’agit de la première d’une série de trois didacticiels.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="5b9bf-112">Dans ce didacticiel, vous allez créer et empaqueter un outil.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="5b9bf-113">Dans les deux didacticiels suivants, vous [Utilisez l’outil comme un outil Global](global-tools-how-to-use.md) et vous [Utilisez l’outil comme outil local](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="5b9bf-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span> <span data-ttu-id="5b9bf-114">Les procédures de création d’un outil sont les mêmes que vous l’utilisiez comme outil Global ou comme outil local.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-114">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b9bf-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="5b9bf-115">Prerequisites</span></span>

- <span data-ttu-id="5b9bf-116">[Kit de développement logiciel (SDK) .net 5.0.100](https://dotnet.microsoft.com/download) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-116">[.NET SDK 5.0.100](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="5b9bf-117">Ce didacticiel utilise le kit de développement logiciel (SDK) .NET 5,0, mais les outils globaux sont disponibles à partir de kit SDK .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-117">This tutorial uses .NET SDK 5.0, but global tools are available starting in .NET Core SDK 2.1.</span></span> <span data-ttu-id="5b9bf-118">Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-118">Local tools are available starting in .NET Core SDK 3.0.</span></span>

- <span data-ttu-id="5b9bf-119">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-119">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="5b9bf-120">Création d’un projet</span><span class="sxs-lookup"><span data-stu-id="5b9bf-120">Create a project</span></span>

1. <span data-ttu-id="5b9bf-121">Ouvrez une invite de commandes et créez un dossier nommé *repository*.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-121">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="5b9bf-122">Accédez au dossier du *référentiel* , puis entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-122">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay -f net5.0
   ```

   <span data-ttu-id="5b9bf-123">La commande crée un nouveau dossier nommé *Microsoft. botsay* dans le dossier du *référentiel* .</span><span class="sxs-lookup"><span data-stu-id="5b9bf-123">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5b9bf-124">Pour ce didacticiel, vous allez créer un outil qui cible .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-124">For this tutorial you create a tool that targets .NET 5.0.</span></span> <span data-ttu-id="5b9bf-125">Pour cibler une autre infrastructure, modifiez l' `-f|--framework` option.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-125">To target a different framework, change the `-f|--framework` option.</span></span> <span data-ttu-id="5b9bf-126">Pour cibler plusieurs frameworks, remplacez l' `TargetFramework` élément par un `TargetFrameworks` élément dans le fichier projet, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-126">To target multiple frameworks, change the `TargetFramework` element to a `TargetFrameworks` element in the project file, as shown in the following example:</span></span>
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>
   >   </PropertyGroup>
   > </Project>
   > ```

1. <span data-ttu-id="5b9bf-127">Accédez au dossier *Microsoft. botsay* .</span><span class="sxs-lookup"><span data-stu-id="5b9bf-127">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="5b9bf-128">Ajouter le code</span><span class="sxs-lookup"><span data-stu-id="5b9bf-128">Add the code</span></span>

1. <span data-ttu-id="5b9bf-129">Ouvrez le `Program.cs` fichier à l’aide de votre éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-129">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="5b9bf-130">Ajoutez la directive `using` suivante en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-130">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="5b9bf-131">Remplacez la `Main` méthode par le code suivant pour traiter les arguments de ligne de commande de l’application.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-131">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="5b9bf-132">Si aucun argument n’est passé, un bref message d’aide s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-132">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="5b9bf-133">Sinon, tous les arguments sont concaténés dans une chaîne unique et imprimés en appelant la `ShowBot` méthode que vous créez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-133">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="5b9bf-134">Ajoutez une nouvelle méthode nommée `ShowBot` qui accepte un paramètre de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-134">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="5b9bf-135">La méthode imprime le message et une image d’un robot à l’aide de lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-135">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="5b9bf-136">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-136">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="5b9bf-137">Test de l’application</span><span class="sxs-lookup"><span data-stu-id="5b9bf-137">Test the application</span></span>

<span data-ttu-id="5b9bf-138">Exécutez le projet et observez le résultat.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-138">Run the project and see the output.</span></span> <span data-ttu-id="5b9bf-139">Essayez ces variations sur la ligne de commande pour afficher des résultats différents :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-139">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="5b9bf-140">Tous les arguments après le délimiteur `--` sont passés à votre application.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-140">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="5b9bf-141">Empaqueter l’outil</span><span class="sxs-lookup"><span data-stu-id="5b9bf-141">Package the tool</span></span>

<span data-ttu-id="5b9bf-142">Avant de pouvoir empaqueter et distribuer l’application en tant qu’outil, vous devez modifier le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-142">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="5b9bf-143">Ouvrez le fichier *Microsoft. botsay. csproj* et ajoutez trois nouveaux nœuds XML à la fin du `<PropertyGroup>` nœud :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-143">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="5b9bf-144">`<ToolCommandName>` est un élément facultatif qui spécifie la commande qui appellera l’outil après son installation.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-144">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="5b9bf-145">Si cet élément n’est pas fourni, le nom de commande de l’outil est le nom du fichier projet sans l’extension *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="5b9bf-145">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="5b9bf-146">`<PackageOutputPath>` est un élément facultatif qui détermine où le package NuGet sera produit.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-146">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="5b9bf-147">Le package NuGet est ce que l’interface de commande .NET utilise pour installer votre outil.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-147">The NuGet package is what the .NET CLI uses to install your tool.</span></span>

   <span data-ttu-id="5b9bf-148">Le fichier projet se présente maintenant comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-148">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="5b9bf-149">Créez un package NuGet en exécutant la commande [dotnet Pack](dotnet-pack.md) :</span><span class="sxs-lookup"><span data-stu-id="5b9bf-149">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="5b9bf-150">Le fichier *Microsoft. botsay. 1.0.0. nupkg* est créé dans le dossier identifié par la `<PackageOutputPath>` valeur du fichier *Microsoft. botsay. csproj* , qui, dans cet exemple, est le dossier *./nupkg* .</span><span class="sxs-lookup"><span data-stu-id="5b9bf-150">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>

   <span data-ttu-id="5b9bf-151">Lorsque vous souhaitez libérer un outil publiquement, vous pouvez le télécharger sur `https://www.nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="5b9bf-151">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="5b9bf-152">Une fois que l’outil est disponible sur NuGet, les développeurs peuvent installer l’outil à l’aide de la commande d’installation de l' [outil dotnet](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="5b9bf-152">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="5b9bf-153">Pour ce didacticiel, vous installez le package directement à partir du dossier local *nupkg* . il n’est donc pas nécessaire de charger le package dans NuGet.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-153">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="5b9bf-154">Résoudre des problèmes</span><span class="sxs-lookup"><span data-stu-id="5b9bf-154">Troubleshoot</span></span>

<span data-ttu-id="5b9bf-155">Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation des outils .net](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="5b9bf-155">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5b9bf-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5b9bf-156">Next steps</span></span>

<span data-ttu-id="5b9bf-157">Dans ce didacticiel, vous avez créé une application console et l’avez empaquetée en tant qu’outil.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-157">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="5b9bf-158">Pour savoir comment utiliser l’outil comme un outil Global, passez au didacticiel suivant.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-158">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b9bf-159">Installer et utiliser un outil Global</span><span class="sxs-lookup"><span data-stu-id="5b9bf-159">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="5b9bf-160">Si vous préférez, vous pouvez ignorer le didacticiel sur les outils globaux et accéder directement au didacticiel sur les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="5b9bf-160">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b9bf-161">Installer et utiliser un outil local</span><span class="sxs-lookup"><span data-stu-id="5b9bf-161">Install and use a local tool</span></span>](local-tools-how-to-use.md)
