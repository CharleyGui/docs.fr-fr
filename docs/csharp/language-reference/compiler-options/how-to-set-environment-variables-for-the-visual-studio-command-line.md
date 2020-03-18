---
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
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342365"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="cca84-102">Comment : définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cca84-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="cca84-103">Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="cca84-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="cca84-104">Visual Studio 2015 et les versions précédentes ont utilisé VSVARS32.bat, pas VsDevCmd.bat dans le même but.</span><span class="sxs-lookup"><span data-stu-id="cca84-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="cca84-105">Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="cca84-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="cca84-106">Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="cca84-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="cca84-107">Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="cca84-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="cca84-108">Pour exécuter VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="cca84-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="cca84-109">À partir du menu **Démarrer,** ouvrez **l’invite de commande de développeur pour VS 2019.**</span><span class="sxs-lookup"><span data-stu-id="cca84-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="cca84-110">C’est dans le dossier **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="cca84-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="cca84-111">Modification de la\\*version*\\studio visuel «Program Files-Microsoft)*offre*de «Common7-Tools\\ou fichiers de programme (x86) Microsoft Visual Studio*Version*\\*offrant*la sous-direction de votre installation.</span><span class="sxs-lookup"><span data-stu-id="cca84-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="cca84-112">(*Version* *2019* pour la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="cca84-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="cca84-113">*Offre* correspond à *Enterprise*, *Professional* ou *Community*.)</span><span class="sxs-lookup"><span data-stu-id="cca84-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="cca84-114">Exécutez VsDevCmd.bat en tapant **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="cca84-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="cca84-115">VsDevCmd.bat peut varier d’un ordinateur à l’autre.</span><span class="sxs-lookup"><span data-stu-id="cca84-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="cca84-116">Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé par un fichier VsDevCmd.bat d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cca84-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="cca84-117">À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.</span><span class="sxs-lookup"><span data-stu-id="cca84-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="cca84-118">Options disponibles pour VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="cca84-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="cca84-119">Pour afficher les options disponibles pour VsDevCmd.BAT, exécutez la commande avec l’option `-help` :</span><span class="sxs-lookup"><span data-stu-id="cca84-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="cca84-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cca84-120">See also</span></span>

- [<span data-ttu-id="cca84-121">Génération en ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="cca84-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
