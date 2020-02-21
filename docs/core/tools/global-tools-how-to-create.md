---
title: 'Didacticiel : créer un outil .NET Core'
description: Découvrez comment créer un outil .NET Core. Un outil est une application console installée à l’aide de l’CLI .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543402"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="793c4-104">Didacticiel : créer un outil .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="793c4-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="793c4-105">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="793c4-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="793c4-106">Ce didacticiel vous apprend à créer et à empaqueter un outil .NET Core.</span><span class="sxs-lookup"><span data-stu-id="793c4-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="793c4-107">La CLI .NET Core vous permet de créer une application console en tant qu’outil, que d’autres peuvent installer et exécuter.</span><span class="sxs-lookup"><span data-stu-id="793c4-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="793c4-108">Les outils .NET Core sont des packages NuGet qui sont installés à partir du CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="793c4-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="793c4-109">Pour plus d’informations sur les outils, consultez [vue d’ensemble des outils .net Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="793c4-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="793c4-110">L’outil que vous allez créer est une application console qui accepte un message comme entrée et affiche le message avec des lignes de texte qui créent l’image d’un robot.</span><span class="sxs-lookup"><span data-stu-id="793c4-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="793c4-111">Il s’agit de la première d’une série de trois didacticiels.</span><span class="sxs-lookup"><span data-stu-id="793c4-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="793c4-112">Dans ce didacticiel, vous allez créer et empaqueter un outil.</span><span class="sxs-lookup"><span data-stu-id="793c4-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="793c4-113">Dans les deux didacticiels suivants, vous [Utilisez l’outil comme un outil Global](global-tools-how-to-use.md) et vous [Utilisez l’outil comme outil local](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="793c4-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="793c4-114">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="793c4-114">Prerequisites</span></span>

- <span data-ttu-id="793c4-115">[Kit SDK .NET Core 3,1](https://dotnet.microsoft.com/download) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="793c4-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="793c4-116">Ce didacticiel et le [didacticiel sur les outils généraux](global-tools-how-to-use.md) s’appliquent à kit SDK .net Core 2,1 et versions ultérieures, car les outils globaux sont disponibles à partir de cette version.</span><span class="sxs-lookup"><span data-stu-id="793c4-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="793c4-117">Toutefois, ce didacticiel suppose que vous avez installé 3,1 ou une version ultérieure afin de pouvoir passer au didacticiel sur les [Outils locaux](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="793c4-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="793c4-118">Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="793c4-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="793c4-119">Les procédures de création d’un outil sont les mêmes que vous l’utilisiez comme outil Global ou comme outil local.</span><span class="sxs-lookup"><span data-stu-id="793c4-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="793c4-120">Un éditeur de texte ou un éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="793c4-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="793c4-121">Création d’un projet</span><span class="sxs-lookup"><span data-stu-id="793c4-121">Create a project</span></span>

1. <span data-ttu-id="793c4-122">Ouvrez une invite de commandes et créez un dossier nommé *repository*.</span><span class="sxs-lookup"><span data-stu-id="793c4-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="793c4-123">Accédez au dossier du *référentiel* et entrez la commande suivante, en remplaçant `<name>` par une valeur unique pour que le nom du projet soit unique.</span><span class="sxs-lookup"><span data-stu-id="793c4-123">Navigate to the *repository* folder and enter the following command, replacing `<name>` with a unique value to make the project name unique.</span></span> 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   <span data-ttu-id="793c4-124">Par exemple, vous pouvez exécuter la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="793c4-124">For example, you could run the following command:</span></span>

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   <span data-ttu-id="793c4-125">La commande crée un dossier nommé *botsay-\<nom >* dans le dossier du *référentiel* .</span><span class="sxs-lookup"><span data-stu-id="793c4-125">The command creates a new folder named *botsay-\<name>* under the *repository* folder.</span></span>

1. <span data-ttu-id="793c4-126">Accédez au dossier *botsay-\<name >* .</span><span class="sxs-lookup"><span data-stu-id="793c4-126">Navigate to the *botsay-\<name>* folder.</span></span>

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a><span data-ttu-id="793c4-127">Ajouter le code</span><span class="sxs-lookup"><span data-stu-id="793c4-127">Add the code</span></span>

1. <span data-ttu-id="793c4-128">Ouvrez le fichier `Program.cs` à l’aide de votre éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="793c4-128">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="793c4-129">Ajoutez la directive `using` suivante en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="793c4-129">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="793c4-130">Remplacez la méthode `Main` par le code suivant pour traiter les arguments de ligne de commande de l’application.</span><span class="sxs-lookup"><span data-stu-id="793c4-130">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="793c4-131">Si aucun argument n’est passé, un bref message d’aide s’affiche.</span><span class="sxs-lookup"><span data-stu-id="793c4-131">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="793c4-132">Sinon, tous les arguments sont concaténés dans une chaîne unique et imprimés en appelant la méthode `ShowBot` que vous créez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="793c4-132">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="793c4-133">Ajoutez une nouvelle méthode nommée `ShowBot` qui accepte un paramètre de chaîne.</span><span class="sxs-lookup"><span data-stu-id="793c4-133">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="793c4-134">La méthode imprime le message et une image d’un robot à l’aide de lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="793c4-134">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="793c4-135">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="793c4-135">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="793c4-136">Test de l’application</span><span class="sxs-lookup"><span data-stu-id="793c4-136">Test the application</span></span>

<span data-ttu-id="793c4-137">Exécutez le projet et observez le résultat.</span><span class="sxs-lookup"><span data-stu-id="793c4-137">Run the project and see the output.</span></span> <span data-ttu-id="793c4-138">Essayez ces variations sur la ligne de commande pour afficher des résultats différents :</span><span class="sxs-lookup"><span data-stu-id="793c4-138">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="793c4-139">Tous les arguments après le délimiteur `--` sont passés à votre application.</span><span class="sxs-lookup"><span data-stu-id="793c4-139">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="793c4-140">Empaqueter l’outil</span><span class="sxs-lookup"><span data-stu-id="793c4-140">Package the tool</span></span>

<span data-ttu-id="793c4-141">Avant de pouvoir empaqueter et distribuer l’application en tant qu’outil, vous devez modifier le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="793c4-141">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span> 

1. <span data-ttu-id="793c4-142">Ouvrez le fichier *botsay-\<nom >. csproj* et ajoutez trois nouveaux nœuds XML à la fin du nœud `<PropertyGroup>` :</span><span class="sxs-lookup"><span data-stu-id="793c4-142">Open the *botsay-\<name>.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="793c4-143">`<ToolCommandName>` est un élément facultatif qui spécifie la commande qui appellera l’outil après son installation.</span><span class="sxs-lookup"><span data-stu-id="793c4-143">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="793c4-144">Si cet élément n’est pas fourni, le nom de commande de l’outil est le nom du fichier projet sans l’extension *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="793c4-144">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="793c4-145">`<PackageOutputPath>` est un élément facultatif qui détermine où le package NuGet sera produit.</span><span class="sxs-lookup"><span data-stu-id="793c4-145">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="793c4-146">Le package NuGet est ce que le CLI .NET Core utilise pour installer votre outil.</span><span class="sxs-lookup"><span data-stu-id="793c4-146">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="793c4-147">Le fichier projet se présente maintenant comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="793c4-147">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="793c4-148">Créez un package NuGet en exécutant la commande [dotnet Pack](dotnet-pack.md) :</span><span class="sxs-lookup"><span data-stu-id="793c4-148">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="793c4-149">Le *nom botsay-\<>. 1.0.0. nupkg* est créé dans le dossier identifié par la valeur `<PackageOutputPath>` à partir du *nom de l'\<botsay >. csproj* , qui est dans cet exemple le dossier *./nupkg* .</span><span class="sxs-lookup"><span data-stu-id="793c4-149">The *botsay-\<name>.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *botsay-\<name>.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="793c4-150">Lorsque vous souhaitez libérer un outil publiquement, vous pouvez le télécharger sur `https://www.nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="793c4-150">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="793c4-151">Une fois que l’outil est disponible sur NuGet, les développeurs peuvent installer l’outil à l’aide de la commande d’installation de l' [outil dotnet](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="793c4-151">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="793c4-152">Pour ce didacticiel, vous installez le package directement à partir du dossier local *nupkg* . il n’est donc pas nécessaire de charger le package dans NuGet.</span><span class="sxs-lookup"><span data-stu-id="793c4-152">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="793c4-153">Dépanner</span><span class="sxs-lookup"><span data-stu-id="793c4-153">Troubleshoot</span></span>

<span data-ttu-id="793c4-154">Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="793c4-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="793c4-155">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="793c4-155">Next steps</span></span>

<span data-ttu-id="793c4-156">Dans ce didacticiel, vous avez créé une application console et l’avez empaquetée en tant qu’outil.</span><span class="sxs-lookup"><span data-stu-id="793c4-156">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="793c4-157">Pour savoir comment utiliser l’outil comme un outil Global, passez au didacticiel suivant.</span><span class="sxs-lookup"><span data-stu-id="793c4-157">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="793c4-158">Installer et utiliser un outil Global</span><span class="sxs-lookup"><span data-stu-id="793c4-158">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="793c4-159">Si vous préférez, vous pouvez ignorer le didacticiel sur les outils globaux et accéder directement au didacticiel sur les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="793c4-159">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="793c4-160">Installer et utiliser un outil local</span><span class="sxs-lookup"><span data-stu-id="793c4-160">Install and use a local tool</span></span>](local-tools-how-to-use.md)
