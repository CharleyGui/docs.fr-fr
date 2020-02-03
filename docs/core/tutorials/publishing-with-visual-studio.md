---
title: Publier votre application de Hello World .NET Core avec Visual Studio
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741567"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="dd30a-103">Publier votre application de Hello World .NET Core avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd30a-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="dd30a-104">Dans [créer une application Hello World avec .net core dans Visual Studio](with-visual-studio.md), vous avez créé une application console Hello World.</span><span class="sxs-lookup"><span data-stu-id="dd30a-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="dd30a-105">Dans [déboguer votre application Hello World avec Visual Studio](debugging-with-visual-studio.md), vous l’avez testée à l’aide du débogueur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dd30a-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="dd30a-106">Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="dd30a-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="dd30a-107">La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="dd30a-108">Pour déployer les fichiers, copiez-les sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="dd30a-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="dd30a-109">Publier l'application</span><span class="sxs-lookup"><span data-stu-id="dd30a-109">Publish the app</span></span>

1. <span data-ttu-id="dd30a-110">Vérifiez que Visual Studio génère la version release de votre application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="dd30a-111">Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="dd30a-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="dd30a-113">Cliquez avec le bouton droit sur le projet **HelloWorld** (et non pas sur la solution HelloWorld) et sélectionnez **Publier** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="dd30a-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="dd30a-114">(Vous pouvez également sélectionner **publier HelloWorld** dans le menu principal **générer** .)</span><span class="sxs-lookup"><span data-stu-id="dd30a-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. <span data-ttu-id="dd30a-116">Sur la page **choisir une cible de publication** , sélectionnez **dossier**, puis créer un **Profil**.</span><span class="sxs-lookup"><span data-stu-id="dd30a-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Choisir une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. <span data-ttu-id="dd30a-118">Dans la page de **publication**, sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="dd30a-118">On the **Publish** page, select **Publish**.</span></span>

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a><span data-ttu-id="dd30a-120">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="dd30a-120">Inspect the files</span></span>

<span data-ttu-id="dd30a-121">Le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur n’importe quelle plateforme prise en charge par .NET Core avec .NET Core installé sur le système.</span><span class="sxs-lookup"><span data-stu-id="dd30a-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="dd30a-122">Les utilisateurs peuvent exécuter l’application publiée en double-cliquant sur l’exécutable ou en lançant la commande `dotnet HelloWorld.dll` à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="dd30a-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="dd30a-123">Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.</span><span class="sxs-lookup"><span data-stu-id="dd30a-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="dd30a-124">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="dd30a-124">Open a command prompt.</span></span>

   <span data-ttu-id="dd30a-125">Pour ouvrir une invite de commandes, vous pouvez entrer une **invite de commandes** (ou **cmd** pour Short) dans la zone de recherche de la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="dd30a-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="dd30a-126">Sélectionnez l’application de bureau d' **invite de commandes** ou appuyez sur **entrée** si elle est déjà sélectionnée dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="dd30a-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="dd30a-127">Accédez à l’application publiée dans le sous-répertoire *bin\Release\netcoreapp3.1\publish* du répertoire du projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Fenêtre de console affichant les fichiers publiés](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="dd30a-129">Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="dd30a-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="dd30a-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="dd30a-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="dd30a-131">Il s’agit du fichier de dépendances d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="dd30a-132">Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="dd30a-133">Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd30a-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="dd30a-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="dd30a-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="dd30a-135">Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="dd30a-136">Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="dd30a-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="dd30a-137">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="dd30a-137">*HelloWorld.exe*</span></span>
      
         <span data-ttu-id="dd30a-138">Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="dd30a-139">Pour l’exécuter, entrez `HelloWorld.exe` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="dd30a-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="dd30a-140">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="dd30a-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="dd30a-141">Il s’agit du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="dd30a-141">This is the debug symbols file.</span></span> <span data-ttu-id="dd30a-142">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="dd30a-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="dd30a-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="dd30a-144">Il s’agit du fichier de configuration au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd30a-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="dd30a-145">Il identifie la version de .NET Core sur laquelle votre application doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="dd30a-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="dd30a-146">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="dd30a-146">You can also add configuration options to it.</span></span> <span data-ttu-id="dd30a-147">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="dd30a-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="dd30a-148">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="dd30a-148">Additional resources</span></span>

- [<span data-ttu-id="dd30a-149">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="dd30a-149">.NET Core application deployment</span></span>](../deploying/index.md)
