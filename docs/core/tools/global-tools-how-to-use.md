---
title: 'Didacticiel : installer et utiliser un outil Global .NET Core'
description: Découvrez comment installer et utiliser un outil .NET comme un outil Global.
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543872"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="6de94-103">Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="6de94-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="6de94-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6de94-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="6de94-105">Ce didacticiel vous apprend à installer et à utiliser un outil Global.</span><span class="sxs-lookup"><span data-stu-id="6de94-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="6de94-106">Vous utilisez un outil que vous créez dans le [premier didacticiel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="6de94-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6de94-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="6de94-107">Prerequisites</span></span>

* <span data-ttu-id="6de94-108">Effectuez le [premier didacticiel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="6de94-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="6de94-109">Utiliser l’outil comme outil Global</span><span class="sxs-lookup"><span data-stu-id="6de94-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="6de94-110">Installez l’outil à partir du package en exécutant la commande [dotnet Tool install](dotnet-tool-install.md) dans le *nom botsay-\<>* dossier du projet :</span><span class="sxs-lookup"><span data-stu-id="6de94-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *botsay-\<name>* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="6de94-111">Le paramètre `--global` indique à l’CLI .NET Core d’installer les fichiers binaires de l’outil dans un emplacement par défaut qui est automatiquement ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="6de94-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="6de94-112">Le paramètre `--add-source` indique à l’CLI .NET Core d’utiliser temporairement le répertoire *./nupkg* comme flux source supplémentaire pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="6de94-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="6de94-113">Vous avez donné un nom unique à votre package pour vous assurer qu’il se trouve uniquement dans le répertoire *./nupkg* , pas sur le site NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="6de94-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span> 

   <span data-ttu-id="6de94-114">La sortie affiche la commande utilisée pour appeler l’outil et la version installée :</span><span class="sxs-lookup"><span data-stu-id="6de94-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="6de94-115">Appelez l’outil :</span><span class="sxs-lookup"><span data-stu-id="6de94-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="6de94-116">Si cette commande échoue, vous devrez peut-être ouvrir un nouveau terminal pour actualiser le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="6de94-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="6de94-117">Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="6de94-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="6de94-118">Utiliser l’outil comme outil Global installé dans un emplacement personnalisé</span><span class="sxs-lookup"><span data-stu-id="6de94-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="6de94-119">Installez l’outil à partir du package.</span><span class="sxs-lookup"><span data-stu-id="6de94-119">Install the tool from the package.</span></span>

   <span data-ttu-id="6de94-120">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="6de94-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="6de94-121">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="6de94-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="6de94-122">Le paramètre `--tool-path` indique à l’CLI .NET Core d’installer les fichiers binaires de l’outil à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="6de94-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="6de94-123">Si le répertoire n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="6de94-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="6de94-124">Ce répertoire n’est pas automatiquement ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="6de94-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="6de94-125">La sortie affiche la commande utilisée pour appeler l’outil et la version installée :</span><span class="sxs-lookup"><span data-stu-id="6de94-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="6de94-126">Appelez l’outil :</span><span class="sxs-lookup"><span data-stu-id="6de94-126">Invoke the tool:</span></span>

   <span data-ttu-id="6de94-127">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="6de94-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="6de94-128">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="6de94-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="6de94-129">Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="6de94-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="6de94-130">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="6de94-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="6de94-131">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="6de94-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a><span data-ttu-id="6de94-132">Dépanner</span><span class="sxs-lookup"><span data-stu-id="6de94-132">Troubleshoot</span></span>

<span data-ttu-id="6de94-133">Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="6de94-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6de94-134">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6de94-134">Next steps</span></span>

<span data-ttu-id="6de94-135">Dans ce didacticiel, vous avez installé et utilisé un outil comme un outil Global.</span><span class="sxs-lookup"><span data-stu-id="6de94-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="6de94-136">Pour installer et utiliser le même outil qu’un outil local, passez au didacticiel suivant.</span><span class="sxs-lookup"><span data-stu-id="6de94-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6de94-137">Installer et utiliser les outils locaux</span><span class="sxs-lookup"><span data-stu-id="6de94-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
