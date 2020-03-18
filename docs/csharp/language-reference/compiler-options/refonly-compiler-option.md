---
title: -refonly (Options du compilateur C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773852"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="75357-102">-refonly (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="75357-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="75357-103">L’option **-refonly** indique qu’un assembly de référence doit être généré à la place d’un assembly d’implémentation, en tant que sortie principale.</span><span class="sxs-lookup"><span data-stu-id="75357-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="75357-104">Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés.</span><span class="sxs-lookup"><span data-stu-id="75357-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="75357-105">Cette option correspond à la propriété de projet [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="75357-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="75357-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75357-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="75357-107">Notes </span><span class="sxs-lookup"><span data-stu-id="75357-107">Remarks</span></span>

<span data-ttu-id="75357-108">Les assemblages de référence sont un type spécial d’assemblage qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface publique de l’API de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="75357-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="75357-109">Elles comprennent des déclarations pour tous les membres qui sont importantes lorsqu’ils font référence à une assemblée dans des outils de construction, mais excluent toutes les mises en œuvre et déclarations des membres du groupe privé qui n’ont aucune incidence observable sur leur contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="75357-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="75357-110">Pour plus d’informations, voir [les assemblages de référence](../../../standard/assembly/reference-assemblies.md) dans .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="75357-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="75357-111">Les `-refonly` [`-refout`](refout-compiler-option.md) options et les options s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="75357-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="75357-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75357-112">See also</span></span>

- [<span data-ttu-id="75357-113">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="75357-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="75357-114">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="75357-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
