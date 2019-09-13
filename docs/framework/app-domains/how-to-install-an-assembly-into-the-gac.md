---
title: 'Procédure : installer un assembly dans le Global Assembly Cache'
ms.date: 02/05/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926514"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="1623b-102">Procédure : installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1623b-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="1623b-103">Le Global Assembly Cache (GAC) stocke des assemblys partagés par plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="1623b-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="1623b-104">Installez un assembly dans le [Global Assembly Cache](gac.md) avec l’un des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="1623b-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="1623b-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="1623b-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="1623b-106">Outil Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1623b-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="1623b-107">Vous ne pouvez installer dans le GAC que des assemblys à nom fort.</span><span class="sxs-lookup"><span data-stu-id="1623b-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="1623b-108">Pour savoir comment créer un assembly à nom fort, consultez [Guide pratique pour signer un assembly avec un nom fort](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="1623b-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="1623b-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="1623b-109">Windows Installer</span></span>

<span data-ttu-id="1623b-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), le moteur d’installation de Windows, est la méthode recommandée pour ajouter des assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1623b-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="1623b-111">Windows Installer fournit un décompte de références des assemblys dans le Global Assembly Cache, ainsi que d'autres avantages.</span><span class="sxs-lookup"><span data-stu-id="1623b-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="1623b-112">Pour créer un package de programme d’installation pour Windows Installer, utilisez l’[extension de l’ensemble d’outils WiX pour Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="1623b-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="1623b-113">Outil Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1623b-113">Global assembly cache tool</span></span>

<span data-ttu-id="1623b-114">Vous pouvez utiliser l’[outil Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter des assemblys au Global Assembly Cache et visualiser le contenu de ce cache.</span><span class="sxs-lookup"><span data-stu-id="1623b-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1623b-115">L’outil *gacutil.exe* est réservé au développement.</span><span class="sxs-lookup"><span data-stu-id="1623b-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="1623b-116">Ne vous en servez pas pour installer des assemblys de production dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1623b-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="1623b-117">Pour installer un assembly dans le GAC à l’aide de *gacutil.exe*, utilisez cette syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1623b-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="1623b-118">Dans cette commande, *\<assembly name>* est le nom de l’assembly à installer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1623b-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="1623b-119">Si *gacutil.exe* ne se trouve pas dans le chemin de votre système, utilisez l’[invite de commandes développeur pour VS *\<version>* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1623b-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="1623b-120">L’exemple suivant installe un assembly sous le nom de fichier *hello.dll* dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1623b-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="1623b-121">Dans les versions précédentes du .NET Framework, l’extension d’environnement Windows *Shfusion.dll* permet de faire glisser des assemblys dans l’Explorateur de fichiers pour les installer.</span><span class="sxs-lookup"><span data-stu-id="1623b-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="1623b-122">Depuis .NET Framework 4, *Shfusion.dll* est obsolète.</span><span class="sxs-lookup"><span data-stu-id="1623b-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="1623b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1623b-123">See also</span></span>

- [<span data-ttu-id="1623b-124">Utilisation d’assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1623b-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="1623b-125">Guide pratique : supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1623b-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="1623b-126">Gacutil.exe (Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="1623b-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="1623b-127">Guide pratique : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="1623b-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)
