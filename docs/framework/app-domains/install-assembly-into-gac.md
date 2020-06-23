---
title: 'Procédure : installer un assembly dans le Global Assembly Cache'
description: Installez un assembly dans le Global Assembly Cache (GAC) dans .NET afin qu’il puisse être partagé par de nombreuses applications. Utilisez Windows Installer ou l’utilitaire GAC.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104663"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="c30a4-104">Procédure : installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c30a4-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="c30a4-105">Le Global Assembly Cache (GAC) stocke des assemblys partagés par plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="c30a4-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="c30a4-106">Installez un assembly dans le [Global Assembly Cache](gac.md) avec l’un des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="c30a4-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="c30a4-107">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="c30a4-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="c30a4-108">Outil global assembly cache</span><span class="sxs-lookup"><span data-stu-id="c30a4-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="c30a4-109">Vous pouvez installer uniquement des assemblys avec nom fort dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c30a4-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="c30a4-110">Pour plus d’informations sur la création d’un assembly avec nom fort, consultez [Comment : signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="c30a4-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="c30a4-111">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="c30a4-111">Windows Installer</span></span>

<span data-ttu-id="c30a4-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), le moteur d’installation de Windows, est la méthode recommandée pour ajouter des assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c30a4-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="c30a4-113">Windows Installer fournit un décompte de références des assemblys dans le Global Assembly Cache, ainsi que d'autres avantages.</span><span class="sxs-lookup"><span data-stu-id="c30a4-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="c30a4-114">Pour créer un package de programme d’installation pour Windows Installer, utilisez l’[extension de l’ensemble d’outils WiX pour Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="c30a4-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="c30a4-115">Global Assembly Cache (outil)</span><span class="sxs-lookup"><span data-stu-id="c30a4-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="c30a4-116">Vous pouvez utiliser l' [utilitaire .net global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter des assemblys au global assembly cache et afficher le contenu de l’global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="c30a4-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c30a4-117">L’outil *gacutil.exe* est réservé au développement.</span><span class="sxs-lookup"><span data-stu-id="c30a4-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="c30a4-118">Ne vous en servez pas pour installer des assemblys de production dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c30a4-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="c30a4-119">Pour installer un assembly dans le GAC à l’aide de *gacutil.exe*, utilisez cette syntaxe :</span><span class="sxs-lookup"><span data-stu-id="c30a4-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="c30a4-120">Dans cette commande, *\<assembly name>* est le nom de l’assembly à installer dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="c30a4-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="c30a4-121">Si *gacutil.exe* ne se trouve pas dans votre chemin d’accès système, utilisez l' [invite de commandes développeur pour Visual Studio *\<version>* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c30a4-121">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="c30a4-122">L’exemple suivant installe un assembly sous le nom de fichier *hello.dll* dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c30a4-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="c30a4-123">Dans les versions précédentes du .NET Framework, l’extension d’environnement Windows *Shfusion.dll* permet de faire glisser des assemblys dans l’Explorateur de fichiers pour les installer.</span><span class="sxs-lookup"><span data-stu-id="c30a4-123">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="c30a4-124">Depuis .NET Framework 4, *Shfusion.dll* est obsolète.</span><span class="sxs-lookup"><span data-stu-id="c30a4-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="c30a4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c30a4-125">See also</span></span>

- [<span data-ttu-id="c30a4-126">Utiliser des assemblys et le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c30a4-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="c30a4-127">Comment : supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c30a4-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="c30a4-128">Gacutil.exe (outil global assembly cache)</span><span class="sxs-lookup"><span data-stu-id="c30a4-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="c30a4-129">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="c30a4-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
