---
title: -refout (Options du compilateur C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771756"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="3cd27-102">-refout (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="3cd27-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="3cd27-103">L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.</span><span class="sxs-lookup"><span data-stu-id="3cd27-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="3cd27-104">Cela se traduit par `metadataPeStream` dans l’API Emit.</span><span class="sxs-lookup"><span data-stu-id="3cd27-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="3cd27-105">Cette option correspond à la propriété de projet [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3cd27-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="3cd27-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cd27-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="3cd27-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="3cd27-107">Arguments</span></span>

 <span data-ttu-id="3cd27-108">`filepath` Chemin de l’assembly de référence.</span><span class="sxs-lookup"><span data-stu-id="3cd27-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="3cd27-109">Il doit généralement correspondre à celui de l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="3cd27-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="3cd27-110">La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="3cd27-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cd27-111">Notes </span><span class="sxs-lookup"><span data-stu-id="3cd27-111">Remarks</span></span>

<span data-ttu-id="3cd27-112">Les assemblages de référence sont un type spécial d’assemblage qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface publique de l’API de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="3cd27-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="3cd27-113">Elles comprennent des déclarations pour tous les membres qui sont importantes lorsqu’ils font référence à une assemblée dans des outils de construction, mais excluent toutes les mises en œuvre et déclarations des membres du groupe privé qui n’ont aucune incidence observable sur leur contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="3cd27-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="3cd27-114">Pour plus d’informations, voir [les assemblages de référence](../../../standard/assembly/reference-assemblies.md) dans .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="3cd27-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="3cd27-115">Les `-refout` [`-refonly`](refonly-compiler-option.md) options et les options s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="3cd27-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cd27-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cd27-116">See also</span></span>

- [<span data-ttu-id="3cd27-117">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="3cd27-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3cd27-118">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="3cd27-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
