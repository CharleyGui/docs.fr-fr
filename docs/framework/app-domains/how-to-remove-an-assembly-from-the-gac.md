---
title: 'Procédure : supprimer un assembly du Global Assembly Cache'
description: Découvrez comment supprimer un assembly du Global Assembly Cache dans .NET, à l’aide de l’outil Global Assembly Cache (Gacutil.exe) ou Windows Installer.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
ms.openlocfilehash: e3a596ea6029ded190c33032e96b601de9d4012d
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104762"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="a7f77-103">Procédure : supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="a7f77-103">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="a7f77-104">Il existe deux façons de supprimer un assembly du Global Assembly Cache (GAC) :</span><span class="sxs-lookup"><span data-stu-id="a7f77-104">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="a7f77-105">Utilisation de l’[outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a7f77-105">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="a7f77-106">Vous pouvez utiliser cette option pour désinstaller des assemblys que vous avez placés dans le GAC lors du développement et des tests.</span><span class="sxs-lookup"><span data-stu-id="a7f77-106">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="a7f77-107">Utilisation de [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="a7f77-107">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="a7f77-108">Utilisez cette option pour désinstaller des assemblys quand vous testez des packages d'installation et pour les systèmes de production.</span><span class="sxs-lookup"><span data-stu-id="a7f77-108">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="a7f77-109">Suppression d'un assembly avec Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="a7f77-109">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="a7f77-110">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="a7f77-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="a7f77-111">**gacutil – u**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="a7f77-111">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="a7f77-112">Dans cette commande, *nom_assembly* est le nom de l’assembly à supprimer du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="a7f77-112">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="a7f77-113">Vous ne devez pas utiliser Gacutil.exe pour supprimer des assemblys sur des systèmes de production, en raison de la possibilité que l'assembly soit encore requis par certaines applications.</span><span class="sxs-lookup"><span data-stu-id="a7f77-113">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="a7f77-114">Au lieu de cela, vous devez utiliser Windows Installer, qui conserve un comptage des références pour chaque assembly qu'il installe dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="a7f77-114">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="a7f77-115">L’exemple suivant supprime un assembly nommé `hello.dll` de l’global assembly cache :</span><span class="sxs-lookup"><span data-stu-id="a7f77-115">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="a7f77-116">Suppression d'un assembly avec Windows Installer</span><span class="sxs-lookup"><span data-stu-id="a7f77-116">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="a7f77-117">Dans l’application **Programmes et fonctionnalités** du **Panneau de configuration**, sélectionnez l’application que vous voulez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="a7f77-117">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="a7f77-118">Si le package d'installation a placé les assemblys dans le GAC, Windows Installer les supprime s'ils ne sont pas utilisés par une autre application.</span><span class="sxs-lookup"><span data-stu-id="a7f77-118">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="a7f77-119">Windows Installer conserve un comptage des références pour les assemblys installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="a7f77-119">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="a7f77-120">Un assembly est supprimé du GAC seulement quand son comptage des références atteint zéro, ce qui indique qu'il n'est utilisé par aucune application installée par un package Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="a7f77-120">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7f77-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f77-121">See also</span></span>

- [<span data-ttu-id="a7f77-122">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="a7f77-122">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="a7f77-123">Comment : installer un assembly dans le global assembly cache</span><span class="sxs-lookup"><span data-stu-id="a7f77-123">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="a7f77-124">Gacutil.exe (Outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="a7f77-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
