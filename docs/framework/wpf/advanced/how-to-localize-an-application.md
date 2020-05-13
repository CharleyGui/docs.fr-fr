---
title: Localiser une application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209680"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="e3875-102">Comment : localiser une application</span><span class="sxs-lookup"><span data-stu-id="e3875-102">How to: Localize an application</span></span>

<span data-ttu-id="e3875-103">Ce didacticiel explique comment créer une application localisée à l'aide de l'outil LocBaml.</span><span class="sxs-lookup"><span data-stu-id="e3875-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3875-104">L'outil LocBaml n'est pas une application prête pour la production.</span><span class="sxs-lookup"><span data-stu-id="e3875-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="e3875-105">Il est présenté comme un exemple qui fait appel à un certain nombre d'API de localisation et montre comment vous pouvez écrire un outil de localisation.</span><span class="sxs-lookup"><span data-stu-id="e3875-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e3875-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="e3875-106">Overview</span></span>

<span data-ttu-id="e3875-107">Cet article vous donne une approche pas à pas de la localisation d’une application.</span><span class="sxs-lookup"><span data-stu-id="e3875-107">This article gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="e3875-108">Tout d’abord, vous préparez votre application afin que le texte qui sera traduit puisse être extrait.</span><span class="sxs-lookup"><span data-stu-id="e3875-108">First, you prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="e3875-109">Une fois le texte traduit, vous fusionnez le texte traduit en une nouvelle copie de l’application d’origine.</span><span class="sxs-lookup"><span data-stu-id="e3875-109">After the text is translated, you merge the translated text into a new copy of the original application.</span></span>
  
## <a name="create-a-sample-application"></a><span data-ttu-id="e3875-110">Créer un exemple d’application</span><span class="sxs-lookup"><span data-stu-id="e3875-110">Create a sample application</span></span>

<span data-ttu-id="e3875-111">Dans cette étape, vous préparez votre application pour la localisation.</span><span class="sxs-lookup"><span data-stu-id="e3875-111">In this step, you prepare your app for localization.</span></span> <span data-ttu-id="e3875-112">Dans les exemples Windows Presentation Foundation (WPF), un exemple HelloApp est fourni qui sera utilisé pour les exemples de code de cette discussion.</span><span class="sxs-lookup"><span data-stu-id="e3875-112">In the Windows Presentation Foundation (WPF) samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="e3875-113">Si vous souhaitez utiliser cet exemple, téléchargez les fichiers Extensible Application Markup Language (XAML) à partir de l' [exemple d’outil LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="e3875-113">If you would like to use this sample, download the Extensible Application Markup Language (XAML) files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="e3875-114">Développez votre application jusqu'au point où vous voulez démarrer la localisation.</span><span class="sxs-lookup"><span data-stu-id="e3875-114">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="e3875-115">Spécifiez le langage de développement dans le fichier projet de sorte que MSBuild génère un assembly principal et un assembly satellite (un fichier avec l’extension. resources. dll) pour contenir les ressources de langage neutre.</span><span class="sxs-lookup"><span data-stu-id="e3875-115">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="e3875-116">Le fichier de projet de l'exemple HelloApp s'intitule HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="e3875-116">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="e3875-117">Dans ce fichier, vous trouverez le langage de développement identifié comme suit :</span><span class="sxs-lookup"><span data-stu-id="e3875-117">In that file, you will find the development language identified as follows:</span></span>  
  
   `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="e3875-118">Ajoutez des UID à vos fichiers XAML.</span><span class="sxs-lookup"><span data-stu-id="e3875-118">Add Uids to your XAML files.</span></span> <span data-ttu-id="e3875-119">Les UID permettent de suivre les modifications apportées aux fichiers et d'identifier les éléments qui doivent être traduits.</span><span class="sxs-lookup"><span data-stu-id="e3875-119">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="e3875-120">Pour ajouter des UID à vos fichiers, exécutez `updateuid` sur votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="e3875-120">To add Uids to your files, run `updateuid` on your project file:</span></span>  

   `msbuild -t:updateuid helloapp.csproj`

   <span data-ttu-id="e3875-121">Pour vérifier que vous n’avez pas d’UID ou d’UID en double, exécutez `checkuid` :</span><span class="sxs-lookup"><span data-stu-id="e3875-121">To verify that you have no missing or duplicate Uids, run `checkuid`:</span></span>  

   `msbuild -t:checkuid helloapp.csproj`

   <span data-ttu-id="e3875-122">Après `updateuid` l’exécution de, vos fichiers doivent contenir des UID.</span><span class="sxs-lookup"><span data-stu-id="e3875-122">After running `updateuid`, your files should contain Uids.</span></span> <span data-ttu-id="e3875-123">Par exemple, dans le fichier *fichier Pane1. Xaml* de HelloApp, vous devez trouver ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e3875-123">For example, in the *Pane1.xaml* file of HelloApp, you should find the following:</span></span>  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="e3875-124">Créer l’assembly satellite des ressources de langue neutre</span><span class="sxs-lookup"><span data-stu-id="e3875-124">Create the neutral-language resources satellite assembly</span></span>

<span data-ttu-id="e3875-125">Une fois que l’application est configurée pour générer un assembly satellite de ressources de langue neutre, vous générez l’application.</span><span class="sxs-lookup"><span data-stu-id="e3875-125">After the application is configured to generate a neutral-language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="e3875-126">Cela génère l’assembly d’application principal, ainsi que l’assembly satellite de ressources de langue neutre requis par LocBaml pour la localisation.</span><span class="sxs-lookup"><span data-stu-id="e3875-126">This generates the main application assembly as well as the neutral-language resources satellite assembly that's required by LocBaml for localization.</span></span>

<span data-ttu-id="e3875-127">Pour générer l’application :</span><span class="sxs-lookup"><span data-stu-id="e3875-127">To build the application:</span></span>  
  
1. <span data-ttu-id="e3875-128">Compilez HelloApp pour créer une bibliothèque de liens dynamiques (DLL) :</span><span class="sxs-lookup"><span data-stu-id="e3875-128">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
   `msbuild helloapp.csproj`
  
2. <span data-ttu-id="e3875-129">L’assembly d’application principal nouvellement créé, HelloApp. exe, est créé dans le dossier suivant : *C:\HelloApp\Bin\Debug*</span><span class="sxs-lookup"><span data-stu-id="e3875-129">The newly created main application assembly, HelloApp.exe, is created in the following folder: *C:\HelloApp\Bin\Debug*</span></span>
  
3. <span data-ttu-id="e3875-130">L’assembly satellite des ressources de langage neutre nouvellement créé, HelloApp. resources. dll, est créé dans le dossier suivant : *C:\HelloApp\Bin\Debug\en-US*</span><span class="sxs-lookup"><span data-stu-id="e3875-130">The newly created neutral-language resources satellite assembly, HelloApp.resources.dll, is created in the following folder: *C:\HelloApp\Bin\Debug\en-US*</span></span>
  
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="e3875-131">Générer l’outil LocBaml</span><span class="sxs-lookup"><span data-stu-id="e3875-131">Build the LocBaml tool</span></span>  
  
1. <span data-ttu-id="e3875-132">Tous les fichiers nécessaires à la génération de LocBaml se trouvent dans les exemples WPF.</span><span class="sxs-lookup"><span data-stu-id="e3875-132">All the files necessary to build LocBaml are located in the WPF samples.</span></span> <span data-ttu-id="e3875-133">Téléchargez les fichiers C# à partir de l' [exemple d’outil LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="e3875-133">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="e3875-134">Dans la ligne de commande, exécutez le fichier de projet (locbaml.csproj) pour générer l'outil :</span><span class="sxs-lookup"><span data-stu-id="e3875-134">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  

   `msbuild locbaml.csproj`
  
3. <span data-ttu-id="e3875-135">Accédez au répertoire *bin\Release* pour trouver le fichier exécutable nouvellement créé (LocBaml. exe).</span><span class="sxs-lookup"><span data-stu-id="e3875-135">Go to the *Bin\Release* directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="e3875-136">Exemple : *C:\LocBaml\Bin\Release\locbaml.exe*</span><span class="sxs-lookup"><span data-stu-id="e3875-136">Example: *C:\LocBaml\Bin\Release\locbaml.exe*</span></span>
  
4. <span data-ttu-id="e3875-137">Les options que vous pouvez spécifier lors de l’exécution de LocBaml sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="e3875-137">The options that you can specify when you run LocBaml are as follows.</span></span>

   | <span data-ttu-id="e3875-138">Option</span><span class="sxs-lookup"><span data-stu-id="e3875-138">Option</span></span> | <span data-ttu-id="e3875-139">Description</span><span class="sxs-lookup"><span data-stu-id="e3875-139">Description</span></span>|
   | - | - |
   | <span data-ttu-id="e3875-140">`parse` ou `-p`</span><span class="sxs-lookup"><span data-stu-id="e3875-140">`parse` or `-p`</span></span> | <span data-ttu-id="e3875-141">Analyse les fichiers BAML, les ressources ou les DLL pour générer un fichier. csv ou. txt.</span><span class="sxs-lookup"><span data-stu-id="e3875-141">Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span> |
   | <span data-ttu-id="e3875-142">`generate` ou `-g`</span><span class="sxs-lookup"><span data-stu-id="e3875-142">`generate` or `-g`</span></span> | <span data-ttu-id="e3875-143">Génère un fichier binaire localisé à l’aide d’un fichier traduit.</span><span class="sxs-lookup"><span data-stu-id="e3875-143">Generates a localized binary file by using a translated file.</span></span> |
   | <span data-ttu-id="e3875-144">`out`ou `-o` {*répertoirefichiers*]</span><span class="sxs-lookup"><span data-stu-id="e3875-144">`out` or `-o` {*filedirectory*]</span></span> | <span data-ttu-id="e3875-145">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="e3875-145">Output file name.</span></span> |
   | <span data-ttu-id="e3875-146">`culture`ou `-cul` {*culture*]</span><span class="sxs-lookup"><span data-stu-id="e3875-146">`culture` or `-cul` {*culture*]</span></span> | <span data-ttu-id="e3875-147">Paramètres régionaux des assemblys de sortie.</span><span class="sxs-lookup"><span data-stu-id="e3875-147">Locale of output assemblies.</span></span> |
   | <span data-ttu-id="e3875-148">`translation`ou `-trans` {*translation. csv*]</span><span class="sxs-lookup"><span data-stu-id="e3875-148">`translation` or `-trans` {*translation.csv*]</span></span> | <span data-ttu-id="e3875-149">Fichier traduit ou localisé.</span><span class="sxs-lookup"><span data-stu-id="e3875-149">Translated or localized file.</span></span> |
   | <span data-ttu-id="e3875-150">`asmpath`ou `-asmpath` {*répertoirefichiers*]</span><span class="sxs-lookup"><span data-stu-id="e3875-150">`asmpath` or `-asmpath` {*filedirectory*]</span></span> | <span data-ttu-id="e3875-151">Si votre code XAML contient des contrôles personnalisés, vous devez fournir le `asmpath` à l’assembly de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e3875-151">If your XAML code contains custom controls, you must supply the `asmpath` to the custom control assembly.</span></span> |
   | `nologo` | <span data-ttu-id="e3875-152"> : n'affiche aucun logo ni information de droits d'auteur.</span><span class="sxs-lookup"><span data-stu-id="e3875-152">Displays no logo or copyright information.</span></span> |
   | `verbose` | <span data-ttu-id="e3875-153"> : affiche des informations en mode détaillé.</span><span class="sxs-lookup"><span data-stu-id="e3875-153">Displays verbose mode information.</span></span> |
  
   > [!NOTE]
   > <span data-ttu-id="e3875-154">Si vous avez besoin d’une liste des options lors de l’exécution de l’outil, entrez, `LocBaml.exe` puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e3875-154">If you need a list of the options when you are running the tool, enter `LocBaml.exe` and then press **Enter**.</span></span>
  
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="e3875-155">Utiliser LocBaml pour analyser un fichier</span><span class="sxs-lookup"><span data-stu-id="e3875-155">Use LocBaml to parse a file</span></span>

<span data-ttu-id="e3875-156">Maintenant que vous avez créé l'outil LocBaml, vous êtes prêt à l'utiliser pour analyser HelloApp.resources.dll et ainsi extraire le texte qui sera localisé.</span><span class="sxs-lookup"><span data-stu-id="e3875-156">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="e3875-157">Copiez LocBaml.exe dans le dossier bin\debug de votre application, là où l'assembly d'application principal a été créé.</span><span class="sxs-lookup"><span data-stu-id="e3875-157">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="e3875-158">Pour analyser le fichier d'assembly satellite et stocker la sortie sous forme de fichier .csv, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e3875-158">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > <span data-ttu-id="e3875-159">Si le fichier d'entrée, HelloApp.resources.dll, n'est pas dans le même répertoire que LocBaml.exe, déplacez l'un des deux fichiers de telle sorte qu'ils se trouvent dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="e3875-159">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="e3875-160">Quand vous exécutez LocBaml pour analyser les fichiers, la sortie se compose de sept champs délimités par des virgules (fichiers .csv) ou des tabulations (fichiers .txt).</span><span class="sxs-lookup"><span data-stu-id="e3875-160">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="e3875-161">Voici le fichier .csv analysé pour HelloApp.resources.dll :</span><span class="sxs-lookup"><span data-stu-id="e3875-161">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="e3875-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="e3875-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="e3875-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="e3875-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="e3875-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="e3875-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="e3875-165">Les sept champs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="e3875-165">The seven fields are:</span></span>  
  
   - <span data-ttu-id="e3875-166">**Nom BAML**.</span><span class="sxs-lookup"><span data-stu-id="e3875-166">**BAML Name**.</span></span> <span data-ttu-id="e3875-167">Nom de la ressource BAML par rapport à l'assembly satellite de langage source.</span><span class="sxs-lookup"><span data-stu-id="e3875-167">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   - <span data-ttu-id="e3875-168">**Clé de ressource**.</span><span class="sxs-lookup"><span data-stu-id="e3875-168">**Resource Key**.</span></span> <span data-ttu-id="e3875-169">Identificateur de la ressource localisée.</span><span class="sxs-lookup"><span data-stu-id="e3875-169">The localized resource identifier.</span></span>  
  
   - <span data-ttu-id="e3875-170">**Catégorie**.</span><span class="sxs-lookup"><span data-stu-id="e3875-170">**Category**.</span></span> <span data-ttu-id="e3875-171">Type de valeur.</span><span class="sxs-lookup"><span data-stu-id="e3875-171">The value type.</span></span> <span data-ttu-id="e3875-172">Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="e3875-172">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="e3875-173">**Lisibilité**.</span><span class="sxs-lookup"><span data-stu-id="e3875-173">**Readability**.</span></span> <span data-ttu-id="e3875-174">Indique si la valeur peut être lue par un localisateur.</span><span class="sxs-lookup"><span data-stu-id="e3875-174">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="e3875-175">Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="e3875-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="e3875-176">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="e3875-176">**Modifiability**.</span></span> <span data-ttu-id="e3875-177">Indique si la valeur peut être modifiée par un localisateur.</span><span class="sxs-lookup"><span data-stu-id="e3875-177">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="e3875-178">Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="e3875-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="e3875-179">**Commentaires**.</span><span class="sxs-lookup"><span data-stu-id="e3875-179">**Comments**.</span></span> <span data-ttu-id="e3875-180">Description supplémentaire de la valeur pour aider à déterminer comment une valeur est localisée.</span><span class="sxs-lookup"><span data-stu-id="e3875-180">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="e3875-181">Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="e3875-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="e3875-182">**Valeur**.</span><span class="sxs-lookup"><span data-stu-id="e3875-182">**Value**.</span></span> <span data-ttu-id="e3875-183">valeur de texte à traduire dans la culture souhaitée.</span><span class="sxs-lookup"><span data-stu-id="e3875-183">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="e3875-184">Le tableau suivant montre comment ces champs sont mappés par rapport aux valeurs délimitées du fichier .csv :</span><span class="sxs-lookup"><span data-stu-id="e3875-184">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="e3875-185">BAML name</span><span class="sxs-lookup"><span data-stu-id="e3875-185">BAML name</span></span>|<span data-ttu-id="e3875-186">Resource key</span><span class="sxs-lookup"><span data-stu-id="e3875-186">Resource key</span></span>|<span data-ttu-id="e3875-187">Category</span><span class="sxs-lookup"><span data-stu-id="e3875-187">Category</span></span>|<span data-ttu-id="e3875-188">Readability</span><span class="sxs-lookup"><span data-stu-id="e3875-188">Readability</span></span>|<span data-ttu-id="e3875-189">Modifiability</span><span class="sxs-lookup"><span data-stu-id="e3875-189">Modifiability</span></span>|<span data-ttu-id="e3875-190">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e3875-190">Comments</span></span>|<span data-ttu-id="e3875-191">Value</span><span class="sxs-lookup"><span data-stu-id="e3875-191">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="e3875-192">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="e3875-192">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="e3875-193">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="e3875-193">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="e3875-194">Ignorer</span><span class="sxs-lookup"><span data-stu-id="e3875-194">Ignore</span></span>|<span data-ttu-id="e3875-195">FALSE</span><span class="sxs-lookup"><span data-stu-id="e3875-195">FALSE</span></span>|<span data-ttu-id="e3875-196">FALSE</span><span class="sxs-lookup"><span data-stu-id="e3875-196">FALSE</span></span>||<span data-ttu-id="e3875-197">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="e3875-197">#Text1;#Text2</span></span>|
   |<span data-ttu-id="e3875-198">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="e3875-198">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="e3875-199">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="e3875-199">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="e3875-200">Aucune</span><span class="sxs-lookup"><span data-stu-id="e3875-200">None</span></span>|<span data-ttu-id="e3875-201">TRUE</span><span class="sxs-lookup"><span data-stu-id="e3875-201">TRUE</span></span>|<span data-ttu-id="e3875-202">TRUE</span><span class="sxs-lookup"><span data-stu-id="e3875-202">TRUE</span></span>||<span data-ttu-id="e3875-203">Hello World</span><span class="sxs-lookup"><span data-stu-id="e3875-203">Hello World</span></span>|
   |<span data-ttu-id="e3875-204">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="e3875-204">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="e3875-205">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="e3875-205">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="e3875-206">Aucune</span><span class="sxs-lookup"><span data-stu-id="e3875-206">None</span></span>|<span data-ttu-id="e3875-207">TRUE</span><span class="sxs-lookup"><span data-stu-id="e3875-207">TRUE</span></span>|<span data-ttu-id="e3875-208">TRUE</span><span class="sxs-lookup"><span data-stu-id="e3875-208">TRUE</span></span>||<span data-ttu-id="e3875-209">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="e3875-209">Goodbye World</span></span>|
  
   <span data-ttu-id="e3875-210">Notez que toutes les valeurs du champ de **Commentaires** ne contiennent aucune valeur ; Si un champ n’a pas de valeur, il est vide.</span><span class="sxs-lookup"><span data-stu-id="e3875-210">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="e3875-211">Notez également que l’élément de la première ligne n’est ni lisible ni modifiable et qu’il a « ignore » comme valeur de **catégorie** , ce qui indique que la valeur n’est pas localisable.</span><span class="sxs-lookup"><span data-stu-id="e3875-211">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="e3875-212">Pour faciliter la découverte des éléments localisables dans les fichiers analysés, en particulier dans les fichiers volumineux, vous pouvez trier ou filtrer les éléments par **catégorie**, **lisibilité**et **modifiabilité**.</span><span class="sxs-lookup"><span data-stu-id="e3875-212">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="e3875-213">Par exemple, vous pouvez filtrer les valeurs illisibles et non modifiables.</span><span class="sxs-lookup"><span data-stu-id="e3875-213">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
## <a name="translate-the-localizable-content"></a><span data-ttu-id="e3875-214">Traduire le contenu localisable</span><span class="sxs-lookup"><span data-stu-id="e3875-214">Translate the localizable content</span></span>

<span data-ttu-id="e3875-215">Utilisez n'importe quel outil à votre disposition pour traduire le contenu extrait.</span><span class="sxs-lookup"><span data-stu-id="e3875-215">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="e3875-216">Une bonne façon de procéder consiste à écrire les ressources dans un fichier. csv et à les afficher dans Microsoft Excel, en apportant des modifications de traduction à la dernière colonne (valeur).</span><span class="sxs-lookup"><span data-stu-id="e3875-216">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="e3875-217">Utiliser LocBaml pour générer un nouveau fichier. resources. dll</span><span class="sxs-lookup"><span data-stu-id="e3875-217">Use LocBaml to generate a new .resources.dll file</span></span>

<span data-ttu-id="e3875-218">Le contenu qui a été identifié en analysant HelloApp.resources.dll avec LocBaml a été traduit et doit être fusionné dans l'application d'origine.</span><span class="sxs-lookup"><span data-stu-id="e3875-218">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="e3875-219">Utilisez l' `generate` `-g` option ou pour générer un nouveau fichier. resources. dll.</span><span class="sxs-lookup"><span data-stu-id="e3875-219">Use the `generate` or `-g` option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="e3875-220">Utilisez la syntaxe suivante pour générer un nouveau fichier HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="e3875-220">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="e3875-221">Indiquez la culture en-US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="e3875-221">Mark the culture as en-US (/cul:en-US).</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > <span data-ttu-id="e3875-222">Si le fichier d'entrée, Hello.csv, n'est pas dans le même répertoire que l'exécutable, LocBaml.exe, déplacez l'un des deux fichiers de telle sorte qu'ils se trouvent dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="e3875-222">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="e3875-223">Remplacez l’ancien fichier *HelloApp. resources. dll* dans le répertoire *c:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll par* par le fichier *HelloApp. resources. dll* que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="e3875-223">Replace the old *HelloApp.resources.dll* file in the *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* directory with your newly created *HelloApp.resources.dll* file.</span></span>  
  
3. <span data-ttu-id="e3875-224">« Hello World » et « Goodbye World » doivent maintenant être traduits dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e3875-224">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="e3875-225">Pour traduire dans une autre culture, utilisez celle qui correspond à la langue d'arrivée de la traduction.</span><span class="sxs-lookup"><span data-stu-id="e3875-225">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="e3875-226">L'exemple suivant montre comment traduire en français du Canada :</span><span class="sxs-lookup"><span data-stu-id="e3875-226">The following example shows how to translate to French-Canadian:</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. <span data-ttu-id="e3875-227">Dans le même assembly que l'assembly d'application principal, créez un dossier propre à la culture pour héberger le nouvel assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="e3875-227">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="e3875-228">Pour le français du Canada, le dossier s'intitulerait fr-CA.</span><span class="sxs-lookup"><span data-stu-id="e3875-228">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="e3875-229">Copiez l'assembly satellite généré dans le nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="e3875-229">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="e3875-230">Pour tester le nouvel assembly satellite, vous devez modifier la culture sous laquelle votre application s'exécutera.</span><span class="sxs-lookup"><span data-stu-id="e3875-230">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="e3875-231">Vous pouvez le faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="e3875-231">You can do this in one of two ways:</span></span>  
  
   - <span data-ttu-id="e3875-232">Modifiez les paramètres régionaux de votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e3875-232">Change your operating system's regional settings.</span></span>
  
   - <span data-ttu-id="e3875-233">Dans votre application, ajoutez le code suivant à App.xaml.cs :</span><span class="sxs-lookup"><span data-stu-id="e3875-233">In your application, add the following code to App.xaml.cs:</span></span>  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a><span data-ttu-id="e3875-234">Conseils pour l’utilisation de LocBaml</span><span class="sxs-lookup"><span data-stu-id="e3875-234">Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="e3875-235">Tous les assemblys dépendants qui définissent des contrôles personnalisés doivent être copiés dans le répertoire local de LocBaml ou installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="e3875-235">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="e3875-236">Cela est nécessaire, car l’API de localisation doit avoir accès aux assemblys dépendants lorsqu’elle lit le XAML binaire (BAML).</span><span class="sxs-lookup"><span data-stu-id="e3875-236">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="e3875-237">Si l'assembly principal est signé, la DLL de ressources générée doit l'être également pour pouvoir être chargée.</span><span class="sxs-lookup"><span data-stu-id="e3875-237">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="e3875-238">La version de la DLL de ressources localisées doit être synchronisée avec l'assembly principal.</span><span class="sxs-lookup"><span data-stu-id="e3875-238">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e3875-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3875-239">See also</span></span>

- [<span data-ttu-id="e3875-240">Globalisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="e3875-240">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="e3875-241">Vue d'ensemble de l'utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="e3875-241">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
