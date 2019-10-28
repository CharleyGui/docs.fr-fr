---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775567"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="06626-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06626-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="06626-103">L’option **-refonly** indique que la sortie principale de la compilation doit être un assembly de référence au lieu d’un assembly d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="06626-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="06626-104">Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés.</span><span class="sxs-lookup"><span data-stu-id="06626-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="06626-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06626-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="06626-106">Notes</span><span class="sxs-lookup"><span data-stu-id="06626-106">Remarks</span></span>

<span data-ttu-id="06626-107">Visual Basic prend en charge le commutateur `-refonly` à partir de la version 15,3.</span><span class="sxs-lookup"><span data-stu-id="06626-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="06626-108">Les assemblys de référence sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="06626-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="06626-109">Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="06626-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="06626-110">Pour plus d’informations, consultez [références des assemblys](../../../standard/assembly/reference-assemblies.md) dans le guide .net.</span><span class="sxs-lookup"><span data-stu-id="06626-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="06626-111">Les options `-refonly` et [`-refout`](refout-compiler-option.md) s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="06626-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="06626-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06626-112">See also</span></span>

- [<span data-ttu-id="06626-113">/refout</span><span class="sxs-lookup"><span data-stu-id="06626-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="06626-114">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06626-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="06626-115">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="06626-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
