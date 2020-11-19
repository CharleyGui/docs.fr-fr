---
title: Publier une application console .NET à l’aide de Visual Studio Code
description: Découvrez comment utiliser Visual Studio Code et l’interface CLI .NET pour créer l’ensemble des fichiers nécessaires à l’exécution d’une application .NET.
ms.date: 11/17/2020
ms.openlocfilehash: 9cfe490203d2d3254103ad2f0a4c4ff74972ec64
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915884"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="3c593-103">Didacticiel : publier une application console .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3c593-103">Tutorial: Publish a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="3c593-104">Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="3c593-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="3c593-105">La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="3c593-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="3c593-106">Pour déployer les fichiers, copiez-les sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="3c593-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="3c593-107">L’interface CLI .NET est utilisée pour publier l’application. vous pouvez donc suivre ce didacticiel avec un éditeur de code autre que Visual Studio Code si vous préférez.</span><span class="sxs-lookup"><span data-stu-id="3c593-107">The .NET CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3c593-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3c593-108">Prerequisites</span></span>

- <span data-ttu-id="3c593-109">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net à l’aide de Visual Studio code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="3c593-109">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="3c593-110">Publier l’application</span><span class="sxs-lookup"><span data-stu-id="3c593-110">Publish the app</span></span>

1. <span data-ttu-id="3c593-111">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3c593-111">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="3c593-112">Ouvrez le dossier du projet *HelloWorld* que vous avez créé dans [créer une application console .net à l’aide de Visual Studio code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="3c593-112">Open the *HelloWorld* project folder that you created in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="3c593-113">Choisissez **Afficher**  >  **Terminal** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="3c593-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="3c593-114">Le terminal s’ouvre dans le dossier *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="3c593-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="3c593-115">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3c593-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="3c593-116">La configuration de build par défaut est *Debug*. cette commande spécifie donc la configuration *Release* Build.</span><span class="sxs-lookup"><span data-stu-id="3c593-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="3c593-117">La sortie de la configuration de build de mise en production possède des informations de débogage symboliques minimales et est entièrement optimisée.</span><span class="sxs-lookup"><span data-stu-id="3c593-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="3c593-118">La sortie de commande ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3c593-118">The command output is similar to the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="3c593-119">Inspecter les fichiers</span><span class="sxs-lookup"><span data-stu-id="3c593-119">Inspect the files</span></span>

<span data-ttu-id="3c593-120">Par défaut, le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur un ordinateur sur lequel le Runtime .NET est installé.</span><span class="sxs-lookup"><span data-stu-id="3c593-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET runtime installed.</span></span> <span data-ttu-id="3c593-121">Pour exécuter l’application publiée, vous pouvez utiliser le fichier exécutable ou exécuter la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3c593-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="3c593-122">Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.</span><span class="sxs-lookup"><span data-stu-id="3c593-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="3c593-123">Sélectionnez l' **Explorateur** dans la barre de navigation de gauche.</span><span class="sxs-lookup"><span data-stu-id="3c593-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="3c593-124">Développez *bin/Release/net 5.0/Publish*.</span><span class="sxs-lookup"><span data-stu-id="3c593-124">Expand *bin/Release/net5.0/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Explorateur présentant les fichiers publiés":::

   <span data-ttu-id="3c593-126">Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="3c593-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="3c593-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="3c593-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="3c593-128">Il s’agit du fichier de dépendances d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c593-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="3c593-129">Il définit les composants .NET et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="3c593-129">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="3c593-130">Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3c593-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="3c593-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="3c593-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="3c593-132">Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c593-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="3c593-133">Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3c593-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="3c593-134">Cette méthode d’exécution de l’application fonctionne sur toutes les plateformes sur lesquelles le Runtime .NET est installé.</span><span class="sxs-lookup"><span data-stu-id="3c593-134">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

   * <span data-ttu-id="3c593-135">*HelloWorld.exe* (*HelloWorld* sur Linux, non créé sur MacOS.)</span><span class="sxs-lookup"><span data-stu-id="3c593-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="3c593-136">Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c593-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="3c593-137">Le fichier est spécifique au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3c593-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="3c593-138">*HelloWorld.pdb* (facultatif pour le déploiement)</span><span class="sxs-lookup"><span data-stu-id="3c593-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="3c593-139">Il s’agit du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="3c593-139">This is the debug symbols file.</span></span> <span data-ttu-id="3c593-140">Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.</span><span class="sxs-lookup"><span data-stu-id="3c593-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="3c593-141">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="3c593-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="3c593-142">Il s’agit du fichier de configuration au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c593-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="3c593-143">Il identifie la version de .NET sur laquelle votre application a été conçue pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="3c593-143">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="3c593-144">Vous pouvez également y ajouter des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="3c593-144">You can also add configuration options to it.</span></span> <span data-ttu-id="3c593-145">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="3c593-145">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="3c593-146">Exécuter l’application publiée</span><span class="sxs-lookup"><span data-stu-id="3c593-146">Run the published app</span></span>

1. <span data-ttu-id="3c593-147">Dans l' **Explorateur**, cliquez avec le bouton droit sur le dossier de *publication* (<kbd>CTRL</kbd>+ clic sur MacOS), puis sélectionnez **ouvrir dans Terminal**.</span><span class="sxs-lookup"><span data-stu-id="3c593-147">In **Explorer**, right-click the *publish* folder (<kbd>Ctrl</kbd>-click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Menu contextuel avec ouverture dans le terminal":::

1. <span data-ttu-id="3c593-149">Sur Windows ou Linux, exécutez l’application à l’aide de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="3c593-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="3c593-150">Sur Windows, entrez `.\HelloWorld.exe` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="3c593-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="3c593-151">Sur Linux, entrez `./HelloWorld` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="3c593-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="3c593-152">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="3c593-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="3c593-153">Sur n’importe quelle plateforme, exécutez l’application à l’aide de la  [`dotnet`](../tools/dotnet.md) commande :</span><span class="sxs-lookup"><span data-stu-id="3c593-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="3c593-154">Entrez `dotnet HelloWorld.dll`, puis appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="3c593-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="3c593-155">Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.</span><span class="sxs-lookup"><span data-stu-id="3c593-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3c593-156">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3c593-156">Additional resources</span></span>

- [<span data-ttu-id="3c593-157">déploiement d'applications .NET</span><span class="sxs-lookup"><span data-stu-id="3c593-157">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="3c593-158">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3c593-158">Next steps</span></span>

<span data-ttu-id="3c593-159">Dans ce didacticiel, vous avez publié une application console.</span><span class="sxs-lookup"><span data-stu-id="3c593-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="3c593-160">Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="3c593-160">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3c593-161">Créer une bibliothèque de classes .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3c593-161">Create a .NET class library using Visual Studio Code</span></span>](library-with-visual-studio-code.md)
