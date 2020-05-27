---
title: Publier votre application de Hello World .NET Core avec Visual Studio
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e4ef8c12f3e52faa7cf09058a98abae65b0dcfce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005091"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a><span data-ttu-id="eec4e-103">Didacticiel : publier une application console .NET Core avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eec4e-103">Tutorial: Publish a .NET Core console application with Visual Studio</span></span>

<span data-ttu-id="eec4e-104">Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="eec4e-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="eec4e-105">La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="eec4e-106">Pour déployer les fichiers, copiez-les sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="eec4e-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eec4e-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="eec4e-107">Prerequisites</span></span>

- <span data-ttu-id="eec4e-108">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="eec4e-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="eec4e-109">Publier l’application</span><span class="sxs-lookup"><span data-stu-id="eec4e-109">Publish the app</span></span>

1. <span data-ttu-id="eec4e-110">Vérifiez que Visual Studio génère la version release de votre application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="eec4e-111">Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="eec4e-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="eec4e-113">Cliquez avec le bouton droit sur le projet **HelloWorld** (et non sur la solution HelloWorld) et sélectionnez **publier** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="eec4e-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="eec4e-115">Dans l’onglet **cible** de la page **publier** , sélectionnez **dossier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="eec4e-115">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Choisir une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="eec4e-117">Dans l’onglet **emplacement** de la page **publier** , sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="eec4e-117">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Onglet emplacement de la page de publication de Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="eec4e-119">Sous l’onglet **publier** de la fenêtre **publier** , sélectionnez **publier**.</span><span class="sxs-lookup"><span data-stu-id="eec4e-119">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="eec4e-121">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="eec4e-121">Inspect the files</span></span>

<span data-ttu-id="eec4e-122">Le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur l’ordinateur sur lequel le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="eec4e-122">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="eec4e-123">Les utilisateurs peuvent exécuter l’application publiée en double-cliquant sur l’exécutable ou en exécutant la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="eec4e-123">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="eec4e-124">Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.</span><span class="sxs-lookup"><span data-stu-id="eec4e-124">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="eec4e-125">Dans **Explorateur de solutions**, sélectionnez **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="eec4e-125">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="eec4e-126">Dans le dossier du projet, développez *bin/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="eec4e-126">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Explorateur de solutions l’indication des fichiers publiés":::

   <span data-ttu-id="eec4e-128">Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="eec4e-128">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="eec4e-129">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="eec4e-129">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="eec4e-130">Il s’agit du fichier de dépendances d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-130">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="eec4e-131">Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-131">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="eec4e-132">Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="eec4e-132">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="eec4e-133">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="eec4e-133">*HelloWorld.dll*</span></span>

         <span data-ttu-id="eec4e-134">Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-134">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="eec4e-135">Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="eec4e-135">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="eec4e-136">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="eec4e-136">*HelloWorld.exe*</span></span>

         <span data-ttu-id="eec4e-137">Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-137">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="eec4e-138">Pour l’exécuter, entrez `HelloWorld.exe` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="eec4e-138">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="eec4e-139">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="eec4e-139">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="eec4e-140">Il s’agit du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="eec4e-140">This is the debug symbols file.</span></span> <span data-ttu-id="eec4e-141">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-141">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="eec4e-142">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="eec4e-142">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="eec4e-143">Il s’agit du fichier de configuration au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="eec4e-143">This is the application's run-time configuration file.</span></span> <span data-ttu-id="eec4e-144">Il identifie la version de .NET Core sur laquelle votre application doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="eec4e-144">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="eec4e-145">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="eec4e-145">You can also add configuration options to it.</span></span> <span data-ttu-id="eec4e-146">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="eec4e-146">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="eec4e-147">Exécuter l’application publiée</span><span class="sxs-lookup"><span data-stu-id="eec4e-147">Run the published app</span></span>

1. <span data-ttu-id="eec4e-148">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier de *publication* , puis sélectionnez **copier le chemin d’accès complet**.</span><span class="sxs-lookup"><span data-stu-id="eec4e-148">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="eec4e-149">Ouvrez une invite de commandes et accédez au dossier de *publication* .</span><span class="sxs-lookup"><span data-stu-id="eec4e-149">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="eec4e-150">Entrez `cd` , puis collez le chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="eec4e-150">Enter `cd` and then paste the full path.</span></span> <span data-ttu-id="eec4e-151">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eec4e-151">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="eec4e-152">Exécutez l’application à l’aide de l’exécutable :</span><span class="sxs-lookup"><span data-stu-id="eec4e-152">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="eec4e-153">Entrez `HelloWorld.exe` et appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="eec4e-153">Enter `HelloWorld.exe` and press Enter.</span></span>

   1. <span data-ttu-id="eec4e-154">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="eec4e-154">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="eec4e-155">Exécutez l’application à l’aide de la `dotnet` commande :</span><span class="sxs-lookup"><span data-stu-id="eec4e-155">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="eec4e-156">Entrez `dotnet HelloWorld.dll` et appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="eec4e-156">Enter `dotnet HelloWorld.dll` and press Enter.</span></span>

   1. <span data-ttu-id="eec4e-157">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="eec4e-157">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eec4e-158">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="eec4e-158">Additional resources</span></span>

- [<span data-ttu-id="eec4e-159">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="eec4e-159">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="eec4e-160">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="eec4e-160">Next steps</span></span>

<span data-ttu-id="eec4e-161">Dans ce didacticiel, vous avez publié une application console.</span><span class="sxs-lookup"><span data-stu-id="eec4e-161">In this tutorial, you published a console app.</span></span> <span data-ttu-id="eec4e-162">Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="eec4e-162">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eec4e-163">Créer une bibliothèque .NET Standard dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eec4e-163">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
