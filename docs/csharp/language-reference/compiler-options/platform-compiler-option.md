---
description: -platform (Options du compilateur C#)
title: -platform (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 3fdb030dfc141b011f5faa827a4e4bb45ae38d19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89466012"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="51401-103">-platform (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="51401-103">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="51401-104">Spécifie la version du CLR (Common Language Runtime) qui peut exécuter l’assembly.</span><span class="sxs-lookup"><span data-stu-id="51401-104">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="51401-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51401-105">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="51401-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51401-106">Parameters</span></span>

`string` \
<span data-ttu-id="51401-107">anycpu (valeur par défaut), anycpu32bitpreferred, ARM, x64, x86 ou Itanium.</span><span class="sxs-lookup"><span data-stu-id="51401-107">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="51401-108">Notes</span><span class="sxs-lookup"><span data-stu-id="51401-108">Remarks</span></span>

- <span data-ttu-id="51401-109">**anycpu** (valeur par défaut) compile votre assembly pour qu’il s’exécute sur n’importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="51401-109">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="51401-110">Votre application s’exécute en tant que processus 64 bits dans la mesure du possible et repasse en 32 bits quand seul ce mode est disponible.</span><span class="sxs-lookup"><span data-stu-id="51401-110">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="51401-111">**anycpu32bitpreferred** compile votre assembly pour qu’il s’exécute sur n’importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="51401-111">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="51401-112">Votre application s’exécute en mode 32 bits sur les systèmes qui prennent en charge les applications 64 bits et 32 bits.</span><span class="sxs-lookup"><span data-stu-id="51401-112">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="51401-113">Vous pouvez spécifier cette option uniquement pour les projets qui ciblent .NET Framework 4,5 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="51401-113">You can specify this option only for projects that target .NET Framework 4.5 or later.</span></span>

- <span data-ttu-id="51401-114">**ARM** compile votre assembly pour qu’il s’exécute sur un ordinateur doté d’un processeur ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="51401-114">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="51401-115">**ARM64** compile votre assembly pour s’exécuter par le CLR 64 bits sur un ordinateur qui dispose d’un processeur Advanced RISC Machine (ARM) qui prend en charge le jeu d’instructions A64.</span><span class="sxs-lookup"><span data-stu-id="51401-115">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="51401-116">**x64** compile votre assembly pour qu’il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d’instructions AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="51401-116">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="51401-117">**x86** compile votre assembly pour qu’il soit exécuté par le CLR 32 bits x86.</span><span class="sxs-lookup"><span data-stu-id="51401-117">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="51401-118">**Itanium** compile votre assembly pour qu’il soit exécuté par le CLR 64 bits sur un ordinateur doté d’un processeur Itanium.</span><span class="sxs-lookup"><span data-stu-id="51401-118">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="51401-119">Sur un système d'exploitation Windows 64 bits :</span><span class="sxs-lookup"><span data-stu-id="51401-119">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="51401-120">Les assemblys compilés avec **-platform:x86** s’exécutent sur le CLR 32 bits fonctionnant sous WOW64.</span><span class="sxs-lookup"><span data-stu-id="51401-120">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="51401-121">Une DLL compilée avec **-platform:anycpu** s’exécute sur le même CLR que le processus dans lequel elle est chargée.</span><span class="sxs-lookup"><span data-stu-id="51401-121">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="51401-122">Les fichiers exécutables compilés avec **-platform:anycpu** s’exécutent sur le CLR 64 bits.</span><span class="sxs-lookup"><span data-stu-id="51401-122">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="51401-123">Les fichiers exécutables compilés avec **-platform:anycpu32bitpreferred** s’exécutent sur le CLR 32 bits.</span><span class="sxs-lookup"><span data-stu-id="51401-123">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="51401-124">Le paramètre **anycpu32bitpreferred** est valide uniquement pour l’exécutable (. EXE) et nécessite .NET Framework 4,5 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="51401-124">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires .NET Framework 4.5 or later.</span></span>

<span data-ttu-id="51401-125">Pour plus d’informations sur le développement d’une application s’exécutant sur un système d’exploitation Windows 64 bits, consultez [Applications 64 bits](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="51401-125">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="51401-126">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51401-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="51401-127">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="51401-127">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="51401-128">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="51401-128">Click the **Build** property page.</span></span>

3. <span data-ttu-id="51401-129">Modifiez la propriété **plateforme cible** et, pour les projets qui ciblent .NET Framework 4,5 ou une version ultérieure, activez ou désactivez la case à cocher **préférer 32 bits** .</span><span class="sxs-lookup"><span data-stu-id="51401-129">Modify the **Platform target** property and, for projects that target .NET Framework 4.5 or later, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="51401-130">`-platform` n’est pas disponible dans l’environnement de développement de Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="51401-130">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="51401-131">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="51401-131">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="51401-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="51401-132">Example</span></span>

<span data-ttu-id="51401-133">L’exemple suivant montre comment utiliser l’option **-platform** pour préciser que l’application doit être exécutée par le CLR 64 bits sur un système d’exploitation Windows 64 bits.</span><span class="sxs-lookup"><span data-stu-id="51401-133">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="51401-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51401-134">See also</span></span>

- [<span data-ttu-id="51401-135">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="51401-135">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="51401-136">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="51401-136">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
