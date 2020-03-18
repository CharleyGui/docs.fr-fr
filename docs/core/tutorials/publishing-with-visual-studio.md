---
title: Publiez votre application .NET Core Hello World avec Visual Studio
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156632"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="313c4-103">Publiez votre application .NET Core Hello World avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="313c4-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="313c4-104">Dans [Créer une application Hello World avec .NET Core dans Visual Studio](with-visual-studio.md), vous avez construit une application de console Hello World.</span><span class="sxs-lookup"><span data-stu-id="313c4-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="313c4-105">Dans [Debug votre application Hello World avec Visual Studio](debugging-with-visual-studio.md), vous l’avez testée à l’aide du debugger Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="313c4-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="313c4-106">Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="313c4-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="313c4-107">La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="313c4-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="313c4-108">Pour déployer les fichiers, copiez-les sur la machine cible.</span><span class="sxs-lookup"><span data-stu-id="313c4-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="313c4-109">Publier l’application</span><span class="sxs-lookup"><span data-stu-id="313c4-109">Publish the app</span></span>

1. <span data-ttu-id="313c4-110">Vérifiez que Visual Studio génère la version release de votre application.</span><span class="sxs-lookup"><span data-stu-id="313c4-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="313c4-111">Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="313c4-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="313c4-113">Cliquez à droite sur le projet **HelloWorld** (pas la solution HelloWorld) et **sélectionnez Publier** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="313c4-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="313c4-114">(Vous pouvez également sélectionner **Publish HelloWorld** à partir du menu **Main Build.)**</span><span class="sxs-lookup"><span data-stu-id="313c4-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="313c4-116">Sur la **page Cible Pick,** sélectionnez **Folder,** puis sélectionnez **Create Profile**.</span><span class="sxs-lookup"><span data-stu-id="313c4-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Choisissez une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="313c4-118">Dans la page de **publication**, sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="313c4-118">On the **Publish** page, select **Publish**.</span></span>

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="313c4-120">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="313c4-120">Inspect the files</span></span>

<span data-ttu-id="313c4-121">Le processus de publication crée un déploiement dépendant du cadre, qui est un type de déploiement où l’application publiée s’exécute sur n’importe quelle plate-forme prise en charge par .NET Core avec .NET Core installé sur le système.</span><span class="sxs-lookup"><span data-stu-id="313c4-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="313c4-122">Les utilisateurs peuvent exécuter l’application publiée en cliquant à deux clics sur l’exécutable ou en émettant la `dotnet HelloWorld.dll` commande à partir d’une invite de commande.</span><span class="sxs-lookup"><span data-stu-id="313c4-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="313c4-123">Dans les étapes suivantes, vous examinerez les fichiers créés par le processus de publication.</span><span class="sxs-lookup"><span data-stu-id="313c4-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="313c4-124">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="313c4-124">Open a command prompt.</span></span>

   <span data-ttu-id="313c4-125">Une façon d’ouvrir une invite de commande est d’entrer **Command Prompt** (ou **cmd** pour faire court) dans la boîte de recherche sur la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="313c4-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="313c4-126">Sélectionnez l’application de bureau **Command Prompt,** ou appuyez **sur Enter** si elle est déjà sélectionnée dans les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="313c4-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="313c4-127">Naviguez vers l’application publiée dans la *sous-direction* de l’annuaire du projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="313c4-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Fenêtre de console affichant les fichiers publiés](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="313c4-129">Comme le montre l’image, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="313c4-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="313c4-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="313c4-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="313c4-131">Il s’agit du fichier de dépendances en temps d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="313c4-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="313c4-132">Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de lien dynamique qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="313c4-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="313c4-133">Pour plus d’informations, voir [fichiers de configuration Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="313c4-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="313c4-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="313c4-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="313c4-135">Il s’agit de la version de [déploiement dépendante](../deploying/deploy-with-cli.md#framework-dependent-deployment) du cadre de l’application.</span><span class="sxs-lookup"><span data-stu-id="313c4-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="313c4-136">Pour exécuter cette bibliothèque `dotnet HelloWorld.dll` de lien dynamique, entrez à une invite de commande.</span><span class="sxs-lookup"><span data-stu-id="313c4-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="313c4-137">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="313c4-137">*HelloWorld.exe*</span></span>

         <span data-ttu-id="313c4-138">Il s’agit de la version [exécutable dépendante](../deploying/deploy-with-cli.md#framework-dependent-executable) du cadre de l’application.</span><span class="sxs-lookup"><span data-stu-id="313c4-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="313c4-139">Pour l’exécuter, entrez `HelloWorld.exe` à une invite de commande.</span><span class="sxs-lookup"><span data-stu-id="313c4-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="313c4-140">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="313c4-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="313c4-141">C’est le fichier des symboles de débogé.</span><span class="sxs-lookup"><span data-stu-id="313c4-141">This is the debug symbols file.</span></span> <span data-ttu-id="313c4-142">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="313c4-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="313c4-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="313c4-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="313c4-144">Il s’agit du fichier de configuration du temps d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="313c4-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="313c4-145">Il identifie la version de .NET Core sur laquelle votre application doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="313c4-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="313c4-146">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="313c4-146">You can also add configuration options to it.</span></span> <span data-ttu-id="313c4-147">Pour plus d’informations, voir [paramètres de configuration .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="313c4-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="313c4-148">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="313c4-148">Additional resources</span></span>

- [<span data-ttu-id="313c4-149">.NET Déploiement d’applications de base</span><span class="sxs-lookup"><span data-stu-id="313c4-149">.NET Core application deployment</span></span>](../deploying/index.md)
