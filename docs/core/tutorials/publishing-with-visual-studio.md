---
title: Publier une application console .NET Core à l’aide de Visual Studio
description: La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application .NET Core.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 44646a307d230db395b55b9dec5acfd168605940
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701282"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="d5b81-103">Didacticiel : publier une application console .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5b81-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="d5b81-104">Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d5b81-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="d5b81-105">La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="d5b81-106">Pour déployer les fichiers, copiez-les sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="d5b81-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d5b81-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d5b81-107">Prerequisites</span></span>

- <span data-ttu-id="d5b81-108">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d5b81-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="d5b81-109">Publier l’application</span><span class="sxs-lookup"><span data-stu-id="d5b81-109">Publish the app</span></span>

1. <span data-ttu-id="d5b81-110">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5b81-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="d5b81-111">Ouvrez le projet *HelloWorld* que vous avez créé dans [créer une application console .net core dans Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d5b81-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="d5b81-112">Assurez-vous que Visual Studio utilise la configuration de la version Release.</span><span class="sxs-lookup"><span data-stu-id="d5b81-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="d5b81-113">Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="d5b81-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="d5b81-115">Cliquez avec le bouton droit sur le projet **HelloWorld** (et non sur la solution HelloWorld) et sélectionnez **publier** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="d5b81-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="d5b81-117">Dans l’onglet **cible** de la page **publier** , sélectionnez **dossier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="d5b81-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Choisir une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="d5b81-119">Dans l’onglet **emplacement** de la page **publier** , sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="d5b81-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Onglet emplacement de la page de publication de Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="d5b81-121">Sous l’onglet **publier** de la fenêtre **publier** , sélectionnez **publier**.</span><span class="sxs-lookup"><span data-stu-id="d5b81-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="d5b81-123">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="d5b81-123">Inspect the files</span></span>

<span data-ttu-id="d5b81-124">Par défaut, le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur l’ordinateur sur lequel le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="d5b81-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="d5b81-125">Les utilisateurs peuvent exécuter l’application publiée en double-cliquant sur l’exécutable ou en exécutant la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d5b81-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="d5b81-126">Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.</span><span class="sxs-lookup"><span data-stu-id="d5b81-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="d5b81-127">Dans **Explorateur de solutions**, sélectionnez **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="d5b81-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="d5b81-128">Dans le dossier du projet, développez *bin/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="d5b81-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Explorateur de solutions l’indication des fichiers publiés":::

   <span data-ttu-id="d5b81-130">Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="d5b81-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="d5b81-131">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="d5b81-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="d5b81-132">Il s’agit du fichier de dépendances d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="d5b81-133">Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="d5b81-134">Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d5b81-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="d5b81-135">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="d5b81-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="d5b81-136">Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="d5b81-137">Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d5b81-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="d5b81-138">Cette méthode d’exécution de l’application fonctionne sur toutes les plateformes sur lesquelles le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="d5b81-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="d5b81-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="d5b81-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="d5b81-140">Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="d5b81-141">Pour l’exécuter, entrez `HelloWorld.exe` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d5b81-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="d5b81-142">Le fichier est spécifique au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d5b81-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="d5b81-143">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="d5b81-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="d5b81-144">Il s’agit du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="d5b81-144">This is the debug symbols file.</span></span> <span data-ttu-id="d5b81-145">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="d5b81-146">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="d5b81-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="d5b81-147">Il s’agit du fichier de configuration au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="d5b81-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="d5b81-148">Il identifie la version de .NET Core sur laquelle votre application doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="d5b81-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="d5b81-149">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="d5b81-149">You can also add configuration options to it.</span></span> <span data-ttu-id="d5b81-150">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d5b81-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="d5b81-151">Exécuter l’application publiée</span><span class="sxs-lookup"><span data-stu-id="d5b81-151">Run the published app</span></span>

1. <span data-ttu-id="d5b81-152">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier de *publication* , puis sélectionnez **copier le chemin d’accès complet**.</span><span class="sxs-lookup"><span data-stu-id="d5b81-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="d5b81-153">Ouvrez une invite de commandes et accédez au dossier de *publication* .</span><span class="sxs-lookup"><span data-stu-id="d5b81-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="d5b81-154">Pour ce faire, entrez, `cd` puis collez le chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="d5b81-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="d5b81-155">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d5b81-155">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="d5b81-156">Exécutez l’application à l’aide de l’exécutable :</span><span class="sxs-lookup"><span data-stu-id="d5b81-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="d5b81-157">Entrez `HelloWorld.exe`, puis appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d5b81-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d5b81-158">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="d5b81-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="d5b81-159">Exécutez l’application à l’aide de la `dotnet` commande :</span><span class="sxs-lookup"><span data-stu-id="d5b81-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="d5b81-160">Entrez `dotnet HelloWorld.dll`, puis appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d5b81-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d5b81-161">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="d5b81-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d5b81-162">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d5b81-162">Additional resources</span></span>

- [<span data-ttu-id="d5b81-163">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="d5b81-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="d5b81-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d5b81-164">Next steps</span></span>

<span data-ttu-id="d5b81-165">Dans ce didacticiel, vous avez publié une application console.</span><span class="sxs-lookup"><span data-stu-id="d5b81-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="d5b81-166">Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="d5b81-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d5b81-167">Créer une bibliothèque .NET Standard dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5b81-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
