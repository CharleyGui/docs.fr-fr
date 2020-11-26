---
description: 'Comment : définir des variables d’environnement pour la ligne de commande Visual Studio'
title: 'Comment : définir des variables d’environnement pour la ligne de commande Visual Studio'
ms.date: 12/20/2019
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: b985c85e2fddce459ed68b3d07ba7d54a8b2d0a7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125603"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="ecf86-103">Comment : définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ecf86-103">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="ecf86-104">Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ecf86-104">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="ecf86-105">Visual Studio 2015 et versions antérieures utilisaient VSVARS32.bat, pas VsDevCmd.bat dans le même but.</span><span class="sxs-lookup"><span data-stu-id="ecf86-105">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="ecf86-106">Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="ecf86-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="ecf86-107">Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ecf86-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="ecf86-108">Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ecf86-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="ecf86-109">Pour exécuter VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="ecf86-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="ecf86-110">Dans le menu **Démarrer** , ouvrez le **Invite de commandes développeur pour vs 2019**.</span><span class="sxs-lookup"><span data-stu-id="ecf86-110">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="ecf86-111">Il se trouve dans le dossier **Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="ecf86-111">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="ecf86-112">Accédez au sous-répertoire \Program Files\Microsoft Visual Studio \\ *version* \\ *offer*\Common7\Tools ou \Program Files (x86) \Microsoft Visual Studio \\ *version* \\ *offer*\Common7\Tools de votre installation.</span><span class="sxs-lookup"><span data-stu-id="ecf86-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="ecf86-113">(La *version* est *2019* pour la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="ecf86-113">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="ecf86-114">*Offre* correspond à *Enterprise*, *Professional* ou *Community*.)</span><span class="sxs-lookup"><span data-stu-id="ecf86-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="ecf86-115">Exécutez VsDevCmd.bat en tapant **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="ecf86-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="ecf86-116">VsDevCmd.bat peut varier d’un ordinateur à l’autre.</span><span class="sxs-lookup"><span data-stu-id="ecf86-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="ecf86-117">Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé par un fichier VsDevCmd.bat d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ecf86-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="ecf86-118">À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.</span><span class="sxs-lookup"><span data-stu-id="ecf86-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="ecf86-119">Options disponibles pour VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="ecf86-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="ecf86-120">Pour afficher les options disponibles pour VsDevCmd.BAT, exécutez la commande avec l’option `-help` :</span><span class="sxs-lookup"><span data-stu-id="ecf86-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="ecf86-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecf86-121">See also</span></span>

- [<span data-ttu-id="ecf86-122">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="ecf86-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
