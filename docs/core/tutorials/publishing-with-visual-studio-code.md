---
title: Publier une application Hello World .NET Core avec Visual Studio Code
description: La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application .NET Core.
ms.date: 05/28/2020
ms.openlocfilehash: b49b12bf41e3ea7be8dbc459eb7d9b1fbef25790
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84246681"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio-code"></a><span data-ttu-id="11778-103">Didacticiel : publier une application console .NET Core avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="11778-103">Tutorial: Publish a .NET Core console application with Visual Studio Code</span></span>

<span data-ttu-id="11778-104">Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="11778-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="11778-105">La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="11778-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="11778-106">Pour déployer les fichiers, copiez-les sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="11778-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="11778-107">Le CLI .NET Core est utilisé pour publier l’application. vous pouvez donc suivre ce didacticiel avec un éditeur de code autre que Visual Studio Code si vous préférez.</span><span class="sxs-lookup"><span data-stu-id="11778-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11778-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="11778-108">Prerequisites</span></span>

- <span data-ttu-id="11778-109">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="11778-109">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="11778-110">Publier l’application</span><span class="sxs-lookup"><span data-stu-id="11778-110">Publish the app</span></span>

1. <span data-ttu-id="11778-111">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="11778-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="11778-112">Ouvrez le dossier du projet *HelloWorld* que vous avez créé dans [créer une application console .net core dans Visual Studio code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="11778-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="11778-113">Choisissez **Afficher**  >  **Terminal** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="11778-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="11778-114">Le terminal s’ouvre dans le dossier *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="11778-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="11778-115">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="11778-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="11778-116">La configuration de build par défaut est *Debug*. cette commande spécifie donc la configuration *Release* Build.</span><span class="sxs-lookup"><span data-stu-id="11778-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="11778-117">La sortie de la configuration de build de mise en production possède des informations de débogage symboliques minimales et est entièrement optimisée.</span><span class="sxs-lookup"><span data-stu-id="11778-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="11778-118">La sortie de commande ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="11778-118">The command output is similar to the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="11778-119">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="11778-119">Inspect the files</span></span>

<span data-ttu-id="11778-120">Par défaut, le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur un ordinateur sur lequel le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="11778-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="11778-121">Pour exécuter l’application publiée, vous pouvez utiliser le fichier exécutable ou exécuter la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="11778-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="11778-122">Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.</span><span class="sxs-lookup"><span data-stu-id="11778-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="11778-123">Sélectionnez l' **Explorateur** dans la barre de navigation de gauche.</span><span class="sxs-lookup"><span data-stu-id="11778-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="11778-124">Développez *bin/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="11778-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Explorateur présentant les fichiers publiés":::

   <span data-ttu-id="11778-126">Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="11778-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="11778-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="11778-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="11778-128">Il s’agit du fichier de dépendances d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="11778-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="11778-129">Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="11778-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="11778-130">Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="11778-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="11778-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="11778-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="11778-132">Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application.</span><span class="sxs-lookup"><span data-stu-id="11778-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="11778-133">Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="11778-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="11778-134">Cette méthode d’exécution de l’application fonctionne sur toutes les plateformes sur lesquelles le Runtime .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="11778-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="11778-135">*HelloWorld. exe* (*HelloWorld* sur Linux, non créé sur MacOS.)</span><span class="sxs-lookup"><span data-stu-id="11778-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="11778-136">Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application.</span><span class="sxs-lookup"><span data-stu-id="11778-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="11778-137">Le fichier est spécifique au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="11778-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="11778-138">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="11778-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="11778-139">Il s’agit du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="11778-139">This is the debug symbols file.</span></span> <span data-ttu-id="11778-140">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="11778-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="11778-141">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="11778-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="11778-142">Il s’agit du fichier de configuration au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="11778-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="11778-143">Il identifie la version de .NET Core sur laquelle votre application doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="11778-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="11778-144">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="11778-144">You can also add configuration options to it.</span></span> <span data-ttu-id="11778-145">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="11778-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="11778-146">Exécuter l’application publiée</span><span class="sxs-lookup"><span data-stu-id="11778-146">Run the published app</span></span>

1. <span data-ttu-id="11778-147">Dans l' **Explorateur**, cliquez avec le bouton droit sur le dossier de *publication* (ou <kbd>Appuyez sur CTRL</kbd>+ clic sur MacOS), puis sélectionnez **ouvrir dans Terminal**.</span><span class="sxs-lookup"><span data-stu-id="11778-147">In **Explorer**, right-click the *publish* folder (or <kbd>Ctrl</kbd>+click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Menu contextuel avec ouverture dans le terminal":::

1. <span data-ttu-id="11778-149">Sur Windows ou Linux, exécutez l’application à l’aide de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="11778-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="11778-150">Sur Windows, entrez `.\HelloWorld.exe` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="11778-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="11778-151">Sur Linux, entrez `./HelloWorld` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="11778-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="11778-152">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="11778-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="11778-153">Sur n’importe quelle plateforme, exécutez l’application à l’aide de la [`dotnet`](../tools/dotnet.md) commande :</span><span class="sxs-lookup"><span data-stu-id="11778-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="11778-154">Entrez `dotnet HelloWorld.dll`, puis appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="11778-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="11778-155">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="11778-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="11778-156">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="11778-156">Additional resources</span></span>

- [<span data-ttu-id="11778-157">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="11778-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="11778-158">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="11778-158">Next steps</span></span>

<span data-ttu-id="11778-159">Dans ce didacticiel, vous avez publié une application console.</span><span class="sxs-lookup"><span data-stu-id="11778-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="11778-160">Pour savoir comment créer des bibliothèques, consultez [développer des bibliothèques avec le CLI .net Core](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="11778-160">To learn how to build libraries, see [Develop libraries with the .NET Core CLI](libraries.md).</span></span>

<!--In the next tutorial, you create a class library.

> [!div class="nextstepaction"]
> [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md)
-->
