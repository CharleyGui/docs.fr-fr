---
description: -nostdlib (Options du compilateur C#)
title: -nostdlib (Options du compilateur C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125096"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="e5130-103">-nostdlib (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e5130-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="e5130-104">**-nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.</span><span class="sxs-lookup"><span data-stu-id="e5130-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5130-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5130-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="e5130-106">Notes</span><span class="sxs-lookup"><span data-stu-id="e5130-106">Remarks</span></span>

<span data-ttu-id="e5130-107">Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.</span><span class="sxs-lookup"><span data-stu-id="e5130-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="e5130-108">Si vous ne spécifiez pas **-nostdlib**, mscorlib.dll est importé dans votre programme (ce qui équivaut à spécifier **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="e5130-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="e5130-109">Les options **-nostdlib** et **-nostdlib+** sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="e5130-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="e5130-110">Pour définir cette option de compilateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5130-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="e5130-111">Les instructions suivantes s’appliquent uniquement à Visual Studio 2015 (et versions antérieures).</span><span class="sxs-lookup"><span data-stu-id="e5130-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="e5130-112">La propriété **ne pas référencer mscorlib.dll** Build n’existe pas dans les versions plus récentes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5130-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="e5130-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="e5130-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="e5130-114">Cliquez sur la page de propriétés **Générer** .</span><span class="sxs-lookup"><span data-stu-id="e5130-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="e5130-115">Cliquez sur le bouton **Avancé** .</span><span class="sxs-lookup"><span data-stu-id="e5130-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="e5130-116">Modifiez la propriété **Ne pas référencer mscorlib.dll** .</span><span class="sxs-lookup"><span data-stu-id="e5130-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="e5130-117">Pour définir cette option du compilateur par programmation</span><span class="sxs-lookup"><span data-stu-id="e5130-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="e5130-118">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5130-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5130-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5130-119">See also</span></span>

- [<span data-ttu-id="e5130-120">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e5130-120">C# Compiler Options</span></span>](./index.md)
