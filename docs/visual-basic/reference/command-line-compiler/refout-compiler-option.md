---
title: -REFOUT (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775548"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="22278-102">-REFOUT (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22278-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="22278-103">L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.</span><span class="sxs-lookup"><span data-stu-id="22278-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="22278-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22278-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="22278-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="22278-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="22278-106">Chemin d’accès et nom de fichier de l’assembly de référence.</span><span class="sxs-lookup"><span data-stu-id="22278-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="22278-107">Il doit généralement se trouver dans un sous-dossier de l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="22278-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="22278-108">La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="22278-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="22278-109">Tous les dossiers de `filepath` doivent exister. le compilateur ne les crée pas.</span><span class="sxs-lookup"><span data-stu-id="22278-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="22278-110">Notes</span><span class="sxs-lookup"><span data-stu-id="22278-110">Remarks</span></span>

<span data-ttu-id="22278-111">Visual Basic prend en charge le commutateur `-refout` à partir de la version 15,3.</span><span class="sxs-lookup"><span data-stu-id="22278-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="22278-112">Les assemblys de référence sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="22278-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="22278-113">Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="22278-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="22278-114">Pour plus d’informations, consultez [références des assemblys](../../../standard/assembly/reference-assemblies.md) dans le guide .net.</span><span class="sxs-lookup"><span data-stu-id="22278-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="22278-115">Les options `-refout` et [`-refonly`](refonly-compiler-option.md) s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="22278-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="22278-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22278-116">See also</span></span>

- [<span data-ttu-id="22278-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="22278-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="22278-118">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22278-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="22278-119">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="22278-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
