---
title: 'Procédure : Localiser une application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 8f1251195fdb21ac57030056abc7b5657edb49fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614619"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="880de-102">Procédure : Localiser une application</span><span class="sxs-lookup"><span data-stu-id="880de-102">How to: Localize an Application</span></span>
<span data-ttu-id="880de-103">Ce didacticiel explique comment créer une application localisée à l'aide de l'outil LocBaml.</span><span class="sxs-lookup"><span data-stu-id="880de-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="880de-104">L'outil LocBaml n'est pas une application prête pour la production.</span><span class="sxs-lookup"><span data-stu-id="880de-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="880de-105">Il est présenté comme un exemple qui fait appel à un certain nombre d'API de localisation et montre comment vous pouvez écrire un outil de localisation.</span><span class="sxs-lookup"><span data-stu-id="880de-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="880de-106">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="880de-106">Overview</span></span>  
 <span data-ttu-id="880de-107">Ce document vous propose une approche pas à pas pour localiser une application.</span><span class="sxs-lookup"><span data-stu-id="880de-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="880de-108">Tout d'abord, vous allez préparer votre application de façon à pouvoir extraire le texte qui sera traduit.</span><span class="sxs-lookup"><span data-stu-id="880de-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="880de-109">Une fois le texte traduit, vous le fusionnerez dans une nouvelle copie de l'application d'origine.</span><span class="sxs-lookup"><span data-stu-id="880de-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="880de-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="880de-110">Requirements</span></span>  
 <span data-ttu-id="880de-111">Dans le cadre de cette procédure, vous allez utiliser [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], qui est un compilateur qui s'exécute à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="880de-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="880de-112">De même, vous serez invité à utiliser un fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="880de-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="880de-113">Pour obtenir des instructions sur l’utilisation [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] et fichiers projet, consultez [générer et déployer](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="880de-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="880de-114">Tous les exemples fournis dans ce document sont de culture en-US (anglais américain).</span><span class="sxs-lookup"><span data-stu-id="880de-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="880de-115">Vous pouvez ainsi parcourir les différentes étapes des exemples sans avoir à installer une autre langue.</span><span class="sxs-lookup"><span data-stu-id="880de-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="880de-116">Créer un exemple d'application</span><span class="sxs-lookup"><span data-stu-id="880de-116">Create a Sample Application</span></span>  
 <span data-ttu-id="880de-117">Dans cette étape, vous allez préparer votre application en vue de sa localisation.</span><span class="sxs-lookup"><span data-stu-id="880de-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="880de-118">L'exemple HelloApp, qui est fourni dans les exemples [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], sera utilisé dans les exemples de code fournis dans ce document.</span><span class="sxs-lookup"><span data-stu-id="880de-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="880de-119">Si vous souhaitez utiliser cet exemple, téléchargez le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichiers à partir de la [exemple d’outil LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="880de-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1. <span data-ttu-id="880de-120">Développez votre application jusqu'au point où vous voulez démarrer la localisation.</span><span class="sxs-lookup"><span data-stu-id="880de-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="880de-121">Spécifiez le langage de développement dans le fichier de projet de sorte que [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] génère un assembly principal et un assembly satellite (fichier doté de l'extension .resources.dll) pour contenir les ressources de langage neutre.</span><span class="sxs-lookup"><span data-stu-id="880de-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="880de-122">Le fichier de projet de l'exemple HelloApp s'intitule HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="880de-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="880de-123">Dans ce fichier, vous trouverez le langage de développement identifié comme suit :</span><span class="sxs-lookup"><span data-stu-id="880de-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="880de-124">Ajoutez des UID à vos fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="880de-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="880de-125">Les UID permettent de suivre les modifications apportées aux fichiers et d'identifier les éléments qui doivent être traduits.</span><span class="sxs-lookup"><span data-stu-id="880de-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="880de-126">Pour ajouter des UID à vos fichiers, exécutez **updateuid** sur votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="880de-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="880de-127">**msbuild -t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="880de-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="880de-128">Pour vérifier que vous n’est manquant ou en double UID, exécutez **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="880de-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="880de-129">**msbuild -t:checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="880de-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="880de-130">Après l’exécution **updateuid**, vos fichiers doivent contenir des UID.</span><span class="sxs-lookup"><span data-stu-id="880de-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="880de-131">Par exemple, dans le fichier Pane1.xaml de HelloApp, vous devez trouver les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="880de-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="880de-132">Créer l'assembly satellite de ressources de langage neutre</span><span class="sxs-lookup"><span data-stu-id="880de-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="880de-133">Après avoir configuré l'application pour générer un assembly satellite de ressources de langage neutre, vous devez générer l'application.</span><span class="sxs-lookup"><span data-stu-id="880de-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="880de-134">Cela a pour effet de générer l'assembly d'application principal, ainsi que l'assembly satellite de ressources de langage neutre dont a besoin LocBaml pour la localisation.</span><span class="sxs-lookup"><span data-stu-id="880de-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="880de-135">Pour générer l'application :</span><span class="sxs-lookup"><span data-stu-id="880de-135">To build the application:</span></span>  
  
1. <span data-ttu-id="880de-136">Compilez HelloApp pour créer une [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="880de-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="880de-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="880de-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="880de-138">L'assembly d'application principal nouvellement créé, HelloApp.exe, se trouve dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="880de-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="880de-139">L'assembly satellite de ressources de langage neutre nouvellement créé, HelloApp.resources.dll, est créé dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="880de-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="880de-140">Générer l'outil LocBaml</span><span class="sxs-lookup"><span data-stu-id="880de-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="880de-141">Tous les fichiers nécessaires à la génération de LocBaml se trouvent dans les exemples [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="880de-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="880de-142">Télécharger les fichiers c# à partir de la [exemple d’outil LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="880de-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="880de-143">Dans la ligne de commande, exécutez le fichier de projet (locbaml.csproj) pour générer l'outil :</span><span class="sxs-lookup"><span data-stu-id="880de-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="880de-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="880de-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="880de-145">Accédez au répertoire Bin\Release pour trouver le fichier exécutable nouvellement créé (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="880de-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="880de-146">Exemple : C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="880de-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="880de-147">Les options que vous pouvez spécifier pendant l'exécution de LocBaml sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="880de-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="880de-148">**analyser** ou **-p:** Analyse Baml, les ressources ou [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] fichiers pour générer un fichier .csv ou .txt.</span><span class="sxs-lookup"><span data-stu-id="880de-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="880de-149">**Générer** ou **-g :** Génère un fichier binaire localisé à l’aide d’un fichier traduit.</span><span class="sxs-lookup"><span data-stu-id="880de-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="880de-150">**out** ou **-o** {*répertoirefichiers*] **:** Nom de fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="880de-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="880de-151">**culture** ou **- cul** {*culture*] **:** Paramètres régionaux des assemblys de sortie.</span><span class="sxs-lookup"><span data-stu-id="880de-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="880de-152">**traduction** ou **- trans** {*translation.csv*] **:** Fichier traduit ou localisé.</span><span class="sxs-lookup"><span data-stu-id="880de-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="880de-153">**asmpath** ou **- asmpath :** {*répertoirefichiers*] **:** Si votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contient des contrôles personnalisés, vous devez fournir le **asmpath** à l’assembly de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="880de-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="880de-154">**nologo :** N’affiche aucune information de droits d’auteur ou d’un logo.</span><span class="sxs-lookup"><span data-stu-id="880de-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="880de-155">**verbose :** Affiche des informations en mode détaillé.</span><span class="sxs-lookup"><span data-stu-id="880de-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="880de-156">Si vous avez besoin d’une liste des options lorsque vous exécutez l’outil, tapez **LocBaml.exe** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="880de-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="880de-157">Utiliser LocBaml pour analyser un fichier</span><span class="sxs-lookup"><span data-stu-id="880de-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="880de-158">Maintenant que vous avez créé l'outil LocBaml, vous êtes prêt à l'utiliser pour analyser HelloApp.resources.dll et ainsi extraire le texte qui sera localisé.</span><span class="sxs-lookup"><span data-stu-id="880de-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="880de-159">Copiez LocBaml.exe dans le dossier bin\debug de votre application, là où l'assembly d'application principal a été créé.</span><span class="sxs-lookup"><span data-stu-id="880de-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="880de-160">Pour analyser le fichier d'assembly satellite et stocker la sortie sous forme de fichier .csv, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="880de-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="880de-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="880de-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="880de-162">Si le fichier d'entrée, HelloApp.resources.dll, n'est pas dans le même répertoire que LocBaml.exe, déplacez l'un des deux fichiers de telle sorte qu'ils se trouvent dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="880de-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="880de-163">Quand vous exécutez LocBaml pour analyser les fichiers, la sortie se compose de sept champs délimités par des virgules (fichiers .csv) ou des tabulations (fichiers .txt).</span><span class="sxs-lookup"><span data-stu-id="880de-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="880de-164">Voici le fichier .csv analysé pour HelloApp.resources.dll :</span><span class="sxs-lookup"><span data-stu-id="880de-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="880de-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="880de-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="880de-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="880de-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="880de-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="880de-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="880de-168">Les sept champs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="880de-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="880de-169">**BAML Name**.</span><span class="sxs-lookup"><span data-stu-id="880de-169">**BAML Name**.</span></span> <span data-ttu-id="880de-170">Nom de la ressource BAML par rapport à l'assembly satellite de langage source.</span><span class="sxs-lookup"><span data-stu-id="880de-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="880de-171">**Resource Key**.</span><span class="sxs-lookup"><span data-stu-id="880de-171">**Resource Key**.</span></span> <span data-ttu-id="880de-172">Identificateur de la ressource localisée.</span><span class="sxs-lookup"><span data-stu-id="880de-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="880de-173">**Category**.</span><span class="sxs-lookup"><span data-stu-id="880de-173">**Category**.</span></span> <span data-ttu-id="880de-174">Type de valeur.</span><span class="sxs-lookup"><span data-stu-id="880de-174">The value type.</span></span> <span data-ttu-id="880de-175">Consultez [attributs de localisation et les commentaires](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="880de-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="880de-176">**Readability**.</span><span class="sxs-lookup"><span data-stu-id="880de-176">**Readability**.</span></span> <span data-ttu-id="880de-177">Indique si la valeur peut être lue par un localisateur.</span><span class="sxs-lookup"><span data-stu-id="880de-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="880de-178">Consultez [attributs de localisation et les commentaires](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="880de-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="880de-179">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="880de-179">**Modifiability**.</span></span> <span data-ttu-id="880de-180">Indique si la valeur peut être modifiée par un localisateur.</span><span class="sxs-lookup"><span data-stu-id="880de-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="880de-181">Consultez [attributs de localisation et les commentaires](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="880de-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="880de-182">**Comments**.</span><span class="sxs-lookup"><span data-stu-id="880de-182">**Comments**.</span></span> <span data-ttu-id="880de-183">Description supplémentaire de la valeur pour aider à déterminer comment une valeur est localisée.</span><span class="sxs-lookup"><span data-stu-id="880de-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="880de-184">Consultez [attributs de localisation et les commentaires](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="880de-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="880de-185">**Value**.</span><span class="sxs-lookup"><span data-stu-id="880de-185">**Value**.</span></span> <span data-ttu-id="880de-186">valeur de texte à traduire dans la culture souhaitée.</span><span class="sxs-lookup"><span data-stu-id="880de-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="880de-187">Le tableau suivant montre comment ces champs sont mappés par rapport aux valeurs délimitées du fichier .csv :</span><span class="sxs-lookup"><span data-stu-id="880de-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="880de-188">BAML name</span><span class="sxs-lookup"><span data-stu-id="880de-188">BAML name</span></span>|<span data-ttu-id="880de-189">Resource key</span><span class="sxs-lookup"><span data-stu-id="880de-189">Resource key</span></span>|<span data-ttu-id="880de-190">Category</span><span class="sxs-lookup"><span data-stu-id="880de-190">Category</span></span>|<span data-ttu-id="880de-191">Readability</span><span class="sxs-lookup"><span data-stu-id="880de-191">Readability</span></span>|<span data-ttu-id="880de-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="880de-192">Modifiability</span></span>|<span data-ttu-id="880de-193">Comments</span><span class="sxs-lookup"><span data-stu-id="880de-193">Comments</span></span>|<span data-ttu-id="880de-194">Value</span><span class="sxs-lookup"><span data-stu-id="880de-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="880de-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="880de-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="880de-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="880de-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="880de-197">Ignore</span><span class="sxs-lookup"><span data-stu-id="880de-197">Ignore</span></span>|<span data-ttu-id="880de-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="880de-198">FALSE</span></span>|<span data-ttu-id="880de-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="880de-199">FALSE</span></span>||<span data-ttu-id="880de-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="880de-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="880de-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="880de-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="880de-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="880de-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="880de-203">None</span><span class="sxs-lookup"><span data-stu-id="880de-203">None</span></span>|<span data-ttu-id="880de-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="880de-204">TRUE</span></span>|<span data-ttu-id="880de-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="880de-205">TRUE</span></span>||<span data-ttu-id="880de-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="880de-206">Hello World</span></span>|
   |<span data-ttu-id="880de-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="880de-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="880de-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="880de-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="880de-209">Aucun</span><span class="sxs-lookup"><span data-stu-id="880de-209">None</span></span>|<span data-ttu-id="880de-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="880de-210">TRUE</span></span>|<span data-ttu-id="880de-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="880de-211">TRUE</span></span>||<span data-ttu-id="880de-212">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="880de-212">Goodbye World</span></span>|
  
   <span data-ttu-id="880de-213">Notez que toutes les valeurs pour le **commentaires** champ ne contient aucune valeur ; si un champ n’a pas une valeur, il est vide.</span><span class="sxs-lookup"><span data-stu-id="880de-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="880de-214">Notez également que l’élément dans la première ligne est ni lisible ni modifiable et « Ignore » en tant que son **catégorie** valeur, ce qui indique que la valeur n’est pas localisable.</span><span class="sxs-lookup"><span data-stu-id="880de-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="880de-215">Pour faciliter la découverte des éléments localisables dans les fichiers analysés, en particulier dans des fichiers volumineux, vous pouvez trier ou filtrer les éléments en **catégorie**, **la lisibilité**, et **modifiabilité**.</span><span class="sxs-lookup"><span data-stu-id="880de-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="880de-216">Par exemple, vous pouvez filtrer les valeurs illisibles et non modifiables.</span><span class="sxs-lookup"><span data-stu-id="880de-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="880de-217">Traduire le contenu localisable</span><span class="sxs-lookup"><span data-stu-id="880de-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="880de-218">Utilisez n'importe quel outil à votre disposition pour traduire le contenu extrait.</span><span class="sxs-lookup"><span data-stu-id="880de-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="880de-219">Une bonne façon de procéder est d'écrire les ressources dans un fichier .csv et de les afficher dans [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], en apportant les modifications de traduction dans la dernière colonne (value).</span><span class="sxs-lookup"><span data-stu-id="880de-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="880de-220">Utiliser LocBaml pour générer un nouveau fichier .resources.dll</span><span class="sxs-lookup"><span data-stu-id="880de-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="880de-221">Le contenu qui a été identifié en analysant HelloApp.resources.dll avec LocBaml a été traduit et doit être fusionné dans l'application d'origine.</span><span class="sxs-lookup"><span data-stu-id="880de-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="880de-222">Utilisez le **générer** ou **-g** option pour générer un nouveau. resources.dll fichier.</span><span class="sxs-lookup"><span data-stu-id="880de-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="880de-223">Utilisez la syntaxe suivante pour générer un nouveau fichier HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="880de-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="880de-224">Indiquez la culture en-US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="880de-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="880de-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="880de-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="880de-226">Si le fichier d'entrée, Hello.csv, n'est pas dans le même répertoire que l'exécutable, LocBaml.exe, déplacez l'un des deux fichiers de telle sorte qu'ils se trouvent dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="880de-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="880de-227">Remplacez l'ancien fichier HelloApp.resources.dll dans le répertoire C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll par le fichier HelloApp.resources.dll que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="880de-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="880de-228">« Hello World » et « Goodbye World » doivent maintenant être traduits dans votre application.</span><span class="sxs-lookup"><span data-stu-id="880de-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="880de-229">Pour traduire dans une autre culture, utilisez celle qui correspond à la langue d'arrivée de la traduction.</span><span class="sxs-lookup"><span data-stu-id="880de-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="880de-230">L'exemple suivant montre comment traduire en français du Canada :</span><span class="sxs-lookup"><span data-stu-id="880de-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="880de-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="880de-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="880de-232">Dans le même assembly que l'assembly d'application principal, créez un dossier propre à la culture pour héberger le nouvel assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="880de-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="880de-233">Pour le français du Canada, le dossier s'intitulerait fr-CA.</span><span class="sxs-lookup"><span data-stu-id="880de-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="880de-234">Copiez l'assembly satellite généré dans le nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="880de-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="880de-235">Pour tester le nouvel assembly satellite, vous devez modifier la culture sous laquelle votre application s'exécutera.</span><span class="sxs-lookup"><span data-stu-id="880de-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="880de-236">Vous pouvez le faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="880de-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="880de-237">Modifiez les paramètres régionaux de votre système d’exploitation (**Démarrer** &#124; **le panneau de configuration** &#124; **Options régionales et linguistiques**).</span><span class="sxs-lookup"><span data-stu-id="880de-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="880de-238">Dans votre application, ajoutez le code suivant à App.xaml.cs :</span><span class="sxs-lookup"><span data-stu-id="880de-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="880de-239">Quelques conseils pour utiliser LocBaml</span><span class="sxs-lookup"><span data-stu-id="880de-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="880de-240">Tous les assemblys dépendants qui définissent des contrôles personnalisés doivent être copiés dans le répertoire local de LocBaml ou installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="880de-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="880de-241">Cela est nécessaire, car l'API de localisation doit avoir accès aux assemblys dépendants au moment de lire le [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="880de-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span></span>  
  
- <span data-ttu-id="880de-242">Si l'assembly principal est signé, la DLL de ressources générée doit l'être également pour pouvoir être chargée.</span><span class="sxs-lookup"><span data-stu-id="880de-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="880de-243">La version de la DLL de ressources localisées doit être synchronisée avec l'assembly principal.</span><span class="sxs-lookup"><span data-stu-id="880de-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="880de-244">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="880de-244">What's Next</span></span>  
 <span data-ttu-id="880de-245">Vous connaissez à présent les rudiments de l'outil LocBaml.</span><span class="sxs-lookup"><span data-stu-id="880de-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="880de-246">Vous êtes normalement en mesure de créer un fichier contenant des UID.</span><span class="sxs-lookup"><span data-stu-id="880de-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="880de-247">À l'aide de l'outil LocBaml, vous devez être en mesure d'analyser un fichier pour extraire le contenu localisable, et une fois le contenu traduit, vous devez pouvoir générer un fichier .resources.dll qui fusionne le contenu traduit.</span><span class="sxs-lookup"><span data-stu-id="880de-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="880de-248">Bien que non exhaustive, cette rubrique vous donne les moyens de localiser vos applications à l'aide LocBaml.</span><span class="sxs-lookup"><span data-stu-id="880de-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880de-249">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="880de-249">See also</span></span>

- [<span data-ttu-id="880de-250">Globalisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="880de-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="880de-251">Vue d’ensemble de l’utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="880de-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
