---
description: -refout (Options du compilateur C#)
title: -refout (Options du compilateur C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128712"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="94e08-103">-refout (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="94e08-103">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="94e08-104">L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.</span><span class="sxs-lookup"><span data-stu-id="94e08-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="94e08-105">Cela se traduit par `metadataPeStream` dans l’API Emit.</span><span class="sxs-lookup"><span data-stu-id="94e08-105">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="94e08-106">Cette option correspond à la propriété de projet [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="94e08-106">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="94e08-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94e08-107">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="94e08-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="94e08-108">Arguments</span></span>

 <span data-ttu-id="94e08-109">`filepath` Chemin de l’assembly de référence.</span><span class="sxs-lookup"><span data-stu-id="94e08-109">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="94e08-110">Il doit généralement correspondre à celui de l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="94e08-110">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="94e08-111">La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="94e08-111">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="94e08-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="94e08-112">Remarks</span></span>

<span data-ttu-id="94e08-113">Les assemblys de référence sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="94e08-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="94e08-114">Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="94e08-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="94e08-115">Pour plus d’informations, consultez [références des assemblys](../../../standard/assembly/reference-assemblies.md) dans le guide .net.</span><span class="sxs-lookup"><span data-stu-id="94e08-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="94e08-116">Les `-refout` options et s’excluent [`-refonly`](refonly-compiler-option.md) mutuellement.</span><span class="sxs-lookup"><span data-stu-id="94e08-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="94e08-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94e08-117">See also</span></span>

- [<span data-ttu-id="94e08-118">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="94e08-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="94e08-119">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="94e08-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
