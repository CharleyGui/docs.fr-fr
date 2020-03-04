---
title: 'Didacticiel : installer et utiliser un outil Global .NET Core'
description: Découvrez comment installer et utiliser un outil .NET comme un outil Global.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156736"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="671e5-103">Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="671e5-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="671e5-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="671e5-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="671e5-105">Ce didacticiel vous apprend à installer et à utiliser un outil Global.</span><span class="sxs-lookup"><span data-stu-id="671e5-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="671e5-106">Vous utilisez un outil que vous créez dans le [premier didacticiel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="671e5-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="671e5-107">Composants requis</span><span class="sxs-lookup"><span data-stu-id="671e5-107">Prerequisites</span></span>

* <span data-ttu-id="671e5-108">Effectuez le [premier didacticiel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="671e5-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="671e5-109">Utiliser l’outil comme outil Global</span><span class="sxs-lookup"><span data-stu-id="671e5-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="671e5-110">Installez l’outil à partir du package en exécutant la commande [dotnet Tool install](dotnet-tool-install.md) dans le dossier du projet *Microsoft. botsay* :</span><span class="sxs-lookup"><span data-stu-id="671e5-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="671e5-111">Le paramètre `--global` indique à l’CLI .NET Core d’installer les fichiers binaires de l’outil dans un emplacement par défaut qui est automatiquement ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="671e5-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="671e5-112">Le paramètre `--add-source` indique à l’CLI .NET Core d’utiliser temporairement le répertoire *./nupkg* comme flux source supplémentaire pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="671e5-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="671e5-113">Vous avez donné un nom unique à votre package pour vous assurer qu’il se trouve uniquement dans le répertoire *./nupkg* , pas sur le site NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="671e5-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="671e5-114">La sortie affiche la commande utilisée pour appeler l’outil et la version installée :</span><span class="sxs-lookup"><span data-stu-id="671e5-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="671e5-115">Appelez l’outil :</span><span class="sxs-lookup"><span data-stu-id="671e5-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="671e5-116">Si cette commande échoue, vous devrez peut-être ouvrir un nouveau terminal pour actualiser le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="671e5-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="671e5-117">Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="671e5-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="671e5-118">Utiliser l’outil comme outil Global installé dans un emplacement personnalisé</span><span class="sxs-lookup"><span data-stu-id="671e5-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="671e5-119">Installez l’outil à partir du package.</span><span class="sxs-lookup"><span data-stu-id="671e5-119">Install the tool from the package.</span></span>

   <span data-ttu-id="671e5-120">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="671e5-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="671e5-121">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="671e5-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="671e5-122">Le paramètre `--tool-path` indique à l’CLI .NET Core d’installer les fichiers binaires de l’outil à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="671e5-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="671e5-123">Si le répertoire n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="671e5-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="671e5-124">Ce répertoire n’est pas automatiquement ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="671e5-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="671e5-125">La sortie affiche la commande utilisée pour appeler l’outil et la version installée :</span><span class="sxs-lookup"><span data-stu-id="671e5-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="671e5-126">Appelez l’outil :</span><span class="sxs-lookup"><span data-stu-id="671e5-126">Invoke the tool:</span></span>

   <span data-ttu-id="671e5-127">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="671e5-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="671e5-128">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="671e5-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="671e5-129">Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="671e5-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="671e5-130">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="671e5-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="671e5-131">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="671e5-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="671e5-132">Dépannage</span><span class="sxs-lookup"><span data-stu-id="671e5-132">Troubleshoot</span></span>

<span data-ttu-id="671e5-133">Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="671e5-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="671e5-134">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="671e5-134">Next steps</span></span>

<span data-ttu-id="671e5-135">Dans ce didacticiel, vous avez installé et utilisé un outil comme un outil Global.</span><span class="sxs-lookup"><span data-stu-id="671e5-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="671e5-136">Pour installer et utiliser le même outil qu’un outil local, passez au didacticiel suivant.</span><span class="sxs-lookup"><span data-stu-id="671e5-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="671e5-137">Installer et utiliser les outils locaux</span><span class="sxs-lookup"><span data-stu-id="671e5-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
