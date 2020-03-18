---
title: 'Tutorial: Installer et utiliser un outil mondial .NET Core'
description: Apprenez à installer et à utiliser un outil .NET comme outil global.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156736"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="3925c-103">Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="3925c-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="3925c-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="3925c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="3925c-105">Ce tutoriel vous apprend à installer et à utiliser un outil global.</span><span class="sxs-lookup"><span data-stu-id="3925c-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="3925c-106">Vous utilisez un outil que vous créez dans le [premier tutoriel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="3925c-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3925c-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="3925c-107">Prerequisites</span></span>

* <span data-ttu-id="3925c-108">Compléter le [premier tutoriel de cette série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="3925c-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="3925c-109">Utilisez l’outil comme outil global</span><span class="sxs-lookup"><span data-stu-id="3925c-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="3925c-110">Installez l’outil à partir du paquet en exécutant la commande [d’installation d’outil dotnet](dotnet-tool-install.md) dans le dossier de projet *microsoft.botsay* :</span><span class="sxs-lookup"><span data-stu-id="3925c-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="3925c-111">Le `--global` paramètre indique au CLI core .NET d’installer les binaires d’outils dans un emplacement par défaut qui est automatiquement ajouté à la variable de l’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="3925c-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="3925c-112">Le `--add-source` paramètre indique à l’ECC Core .NET d’utiliser temporairement le répertoire *./nupkg* comme source supplémentaire pour les paquets NuGet.</span><span class="sxs-lookup"><span data-stu-id="3925c-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="3925c-113">Vous avez donné à votre paquet un nom unique pour s’assurer qu’il ne sera trouvé dans le répertoire *./nupkg,* pas sur le site Nuget.org.</span><span class="sxs-lookup"><span data-stu-id="3925c-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="3925c-114">La sortie montre la commande utilisée pour appeler l’outil et la version installée :</span><span class="sxs-lookup"><span data-stu-id="3925c-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="3925c-115">Invoquez l’outil :</span><span class="sxs-lookup"><span data-stu-id="3925c-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="3925c-116">Si cette commande échoue, vous devrez peut-être ouvrir un nouveau terminal pour rafraîchir le PATH.</span><span class="sxs-lookup"><span data-stu-id="3925c-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="3925c-117">Retirez l’outil en exécutant [l’outil dotnet désinstaller](dotnet-tool-uninstall.md) la commande :</span><span class="sxs-lookup"><span data-stu-id="3925c-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="3925c-118">Utilisez l’outil comme outil global installé dans un emplacement personnalisé</span><span class="sxs-lookup"><span data-stu-id="3925c-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="3925c-119">Installez l’outil à partir de l’emballage.</span><span class="sxs-lookup"><span data-stu-id="3925c-119">Install the tool from the package.</span></span>

   <span data-ttu-id="3925c-120">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="3925c-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="3925c-121">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="3925c-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="3925c-122">Le `--tool-path` paramètre indique à l’RTC de base .NET d’installer les binaires d’outils à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="3925c-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="3925c-123">Si le répertoire n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="3925c-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="3925c-124">Ce répertoire n’est pas automatiquement ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="3925c-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="3925c-125">La sortie montre la commande utilisée pour appeler l’outil et la version installée :</span><span class="sxs-lookup"><span data-stu-id="3925c-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="3925c-126">Invoquez l’outil :</span><span class="sxs-lookup"><span data-stu-id="3925c-126">Invoke the tool:</span></span>

   <span data-ttu-id="3925c-127">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="3925c-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="3925c-128">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="3925c-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="3925c-129">Retirez l’outil en exécutant [l’outil dotnet désinstaller](dotnet-tool-uninstall.md) la commande :</span><span class="sxs-lookup"><span data-stu-id="3925c-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="3925c-130">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="3925c-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="3925c-131">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="3925c-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="3925c-132">Dépanner</span><span class="sxs-lookup"><span data-stu-id="3925c-132">Troubleshoot</span></span>

<span data-ttu-id="3925c-133">Si vous obtenez un message d’erreur tout en suivant le tutoriel, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="3925c-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3925c-134">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3925c-134">Next steps</span></span>

<span data-ttu-id="3925c-135">Dans ce tutoriel, vous avez installé et utilisé un outil comme un outil global.</span><span class="sxs-lookup"><span data-stu-id="3925c-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="3925c-136">Pour installer et utiliser le même outil qu’un outil local, passez au tutoriel suivant.</span><span class="sxs-lookup"><span data-stu-id="3925c-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3925c-137">Installer et utiliser des outils locaux</span><span class="sxs-lookup"><span data-stu-id="3925c-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
