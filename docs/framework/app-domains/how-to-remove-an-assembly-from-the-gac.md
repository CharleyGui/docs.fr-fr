---
title: Guide pratique pour supprimer un assembly du Global Assembly Cache
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
ms.openlocfilehash: c7d85222f35a61154e3eec70d8c9dad2ca6a32f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119852"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="97a88-102">Guide pratique pour supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="97a88-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="97a88-103">Il existe deux façons de supprimer un assembly du Global Assembly Cache (GAC) :</span><span class="sxs-lookup"><span data-stu-id="97a88-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="97a88-104">Utilisation de l’[outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="97a88-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="97a88-105">Vous pouvez utiliser cette option pour désinstaller des assemblys que vous avez placés dans le GAC lors du développement et des tests.</span><span class="sxs-lookup"><span data-stu-id="97a88-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="97a88-106">Utilisation de [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="97a88-106">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="97a88-107">Utilisez cette option pour désinstaller des assemblys quand vous testez des packages d'installation et pour les systèmes de production.</span><span class="sxs-lookup"><span data-stu-id="97a88-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="97a88-108">Suppression d'un assembly avec Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="97a88-108">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="97a88-109">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="97a88-109">At the command prompt, type the following command:</span></span>

<span data-ttu-id="97a88-110">**gacutil –u** \<*nom_assembly*></span><span class="sxs-lookup"><span data-stu-id="97a88-110">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="97a88-111">Dans cette commande, *nom_assembly* est le nom de l’assembly à supprimer du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="97a88-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="97a88-112">Vous ne devez pas utiliser Gacutil.exe pour supprimer des assemblys sur des systèmes de production, en raison de la possibilité que l'assembly soit encore requis par certaines applications.</span><span class="sxs-lookup"><span data-stu-id="97a88-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="97a88-113">Au lieu de cela, vous devez utiliser Windows Installer, qui conserve un comptage des références pour chaque assembly qu'il installe dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="97a88-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="97a88-114">L’exemple suivant supprime un assembly `hello.dll` nommé de l’global assembly cache :</span><span class="sxs-lookup"><span data-stu-id="97a88-114">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="97a88-115">Suppression d'un assembly avec Windows Installer</span><span class="sxs-lookup"><span data-stu-id="97a88-115">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="97a88-116">Dans l’application **Programmes et fonctionnalités** du **Panneau de configuration**, sélectionnez l’application que vous voulez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="97a88-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="97a88-117">Si le package d'installation a placé les assemblys dans le GAC, Windows Installer les supprime s'ils ne sont pas utilisés par une autre application.</span><span class="sxs-lookup"><span data-stu-id="97a88-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="97a88-118">Windows Installer conserve un comptage des références pour les assemblys installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="97a88-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="97a88-119">Un assembly est supprimé du GAC seulement quand son comptage des références atteint zéro, ce qui indique qu'il n'est utilisé par aucune application installée par un package Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="97a88-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="97a88-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97a88-120">See also</span></span>

- [<span data-ttu-id="97a88-121">Utilisation d’assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="97a88-121">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="97a88-122">Comment : installer un assembly dans le global assembly cache</span><span class="sxs-lookup"><span data-stu-id="97a88-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="97a88-123">Gacutil. exe (Outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="97a88-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
