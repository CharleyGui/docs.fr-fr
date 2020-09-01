---
description: -refonly (Options du compilateur C#)
title: -refonly (Options du compilateur C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124745"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="073d0-103">-refonly (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="073d0-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="073d0-104">L’option **-refonly** indique qu’un assembly de référence doit être généré à la place d’un assembly d’implémentation, en tant que sortie principale.</span><span class="sxs-lookup"><span data-stu-id="073d0-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="073d0-105">Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés.</span><span class="sxs-lookup"><span data-stu-id="073d0-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="073d0-106">Cette option correspond à la propriété de projet [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="073d0-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="073d0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="073d0-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="073d0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="073d0-108">Remarks</span></span>

<span data-ttu-id="073d0-109">Les assemblys de référence sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="073d0-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="073d0-110">Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="073d0-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="073d0-111">Pour plus d’informations, consultez [références des assemblys](../../../standard/assembly/reference-assemblies.md) dans le guide .net.</span><span class="sxs-lookup"><span data-stu-id="073d0-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="073d0-112">Les `-refonly` options et s’excluent [`-refout`](refout-compiler-option.md) mutuellement.</span><span class="sxs-lookup"><span data-stu-id="073d0-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="073d0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="073d0-113">See also</span></span>

- [<span data-ttu-id="073d0-114">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="073d0-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="073d0-115">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="073d0-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
