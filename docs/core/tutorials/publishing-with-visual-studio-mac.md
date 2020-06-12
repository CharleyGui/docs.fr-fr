---
title: Publier une application console .NET Core à l’aide de Visual Studio pour Mac
description: La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application .NET Core.
ms.date: 06/08/2020
ms.openlocfilehash: 67762481d3a56b8473e643f71b8df909b6e54fc6
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713664"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="256d7-103">Didacticiel : publier une application console .NET Core à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="256d7-103">Tutorial: Publish a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="256d7-104">Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="256d7-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="256d7-105">La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="256d7-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="256d7-106">Pour déployer les fichiers, copiez-les sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="256d7-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="256d7-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="256d7-107">Prerequisites</span></span>

- <span data-ttu-id="256d7-108">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio pour Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="256d7-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="256d7-109">Publier l’application</span><span class="sxs-lookup"><span data-stu-id="256d7-109">Publish the app</span></span>

1. <span data-ttu-id="256d7-110">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="256d7-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="256d7-111">Ouvrez le projet HelloWorld que vous avez créé dans [créer une application console .net core dans Visual Studio pour Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="256d7-111">Open the HelloWorld project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="256d7-112">Vérifiez que Visual Studio génère la version release de votre application.</span><span class="sxs-lookup"><span data-stu-id="256d7-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="256d7-113">Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="256d7-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Barre d’outils Visual Studio avec version Release sélectionnée":::

1. <span data-ttu-id="256d7-115">Dans le menu principal, choisissez **générer**  >  **publier dans un dossier...**.</span><span class="sxs-lookup"><span data-stu-id="256d7-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Menu contextuel Publier de Visual Studio":::

1. <span data-ttu-id="256d7-117">Dans la boîte de dialogue **publier dans un dossier** , sélectionnez **publier**.</span><span class="sxs-lookup"><span data-stu-id="256d7-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Boîte de dialogue publier dans un dossier de Visual Studio":::

   <span data-ttu-id="256d7-119">Le dossier publier s’ouvre et affiche les fichiers qui ont été créés.</span><span class="sxs-lookup"><span data-stu-id="256d7-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="dossier de publication":::

1. <span data-ttu-id="256d7-121">Sélectionnez l’icône d’engrenage, puis sélectionnez **copier « publier » comme chemin d’accès** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="256d7-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Copier le chemin vers le dossier de publication":::

## <a name="inspect-the-files"></a><span data-ttu-id="256d7-123">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="256d7-123">Inspect the files</span></span>

<span data-ttu-id="256d7-124">Le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur un ordinateur sur lequel le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="256d7-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="256d7-125">Les utilisateurs peuvent exécuter l’application publiée en exécutant la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="256d7-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="256d7-126">Comme l’indique l’image précédente, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="256d7-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="256d7-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="256d7-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="256d7-128">Il s’agit du fichier de dépendances d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="256d7-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="256d7-129">Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="256d7-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="256d7-130">Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="256d7-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="256d7-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="256d7-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="256d7-132">Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application.</span><span class="sxs-lookup"><span data-stu-id="256d7-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="256d7-133">Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="256d7-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="256d7-134">Cette méthode d’exécution de l’application fonctionne sur toutes les plateformes sur lesquelles le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="256d7-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

* <span data-ttu-id="256d7-135">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="256d7-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="256d7-136">Il s’agit du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="256d7-136">This is the debug symbols file.</span></span> <span data-ttu-id="256d7-137">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="256d7-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="256d7-138">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="256d7-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="256d7-139">Il s’agit du fichier de configuration au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="256d7-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="256d7-140">Il identifie la version de .NET Core sur laquelle votre application doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="256d7-140">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="256d7-141">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="256d7-141">You can also add configuration options to it.</span></span> <span data-ttu-id="256d7-142">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="256d7-142">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="256d7-143">Exécuter l’application publiée</span><span class="sxs-lookup"><span data-stu-id="256d7-143">Run the published app</span></span>

1. <span data-ttu-id="256d7-144">Ouvrez un terminal et accédez au dossier *Publish* .</span><span class="sxs-lookup"><span data-stu-id="256d7-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="256d7-145">Pour ce faire, entrez, `cd` puis collez le chemin d’accès que vous avez copié précédemment.</span><span class="sxs-lookup"><span data-stu-id="256d7-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="256d7-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="256d7-146">For example:</span></span>

   ```
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. <span data-ttu-id="256d7-147">Exécutez l’application à l’aide de la `dotnet` commande :</span><span class="sxs-lookup"><span data-stu-id="256d7-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="256d7-148">Entrez `dotnet HelloWorld.dll` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="256d7-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="256d7-149">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="256d7-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="256d7-150">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="256d7-150">Additional resources</span></span>

- [<span data-ttu-id="256d7-151">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="256d7-151">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="256d7-152">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="256d7-152">Next steps</span></span>

<span data-ttu-id="256d7-153">Dans ce didacticiel, vous avez publié une application console.</span><span class="sxs-lookup"><span data-stu-id="256d7-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="256d7-154">Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="256d7-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="256d7-155">Créer une bibliothèque de .NET Standard dans Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="256d7-155">Create a .NET Standard library in Visual Studio for mac</span></span>](library-with-visual-studio-mac.md)
