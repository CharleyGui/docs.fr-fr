---
title: Modules <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 6c4f24ad161302835be683e9d324ce32b16c4087
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867989"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="1c73e-102">\<keyword> Module (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c73e-102">Module \<keyword> (Visual Basic)</span></span>

<span data-ttu-id="1c73e-103">Spécifie qu’un attribut au début d’un fichier source s’applique au module d’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="1c73e-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c73e-104">Notes</span><span class="sxs-lookup"><span data-stu-id="1c73e-104">Remarks</span></span>  

 <span data-ttu-id="1c73e-105">De nombreux attributs se rapportent à un élément de programmation individuel, tel qu’une classe ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="1c73e-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="1c73e-106">Vous appliquez ce type d’attribut en attachant le bloc d’attributs, entre crochets pointus ( `< >` ), directement à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="1c73e-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="1c73e-107">Si un attribut se rapporte non seulement à l’élément suivant mais au module d’assembly actuel, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut à l’aide du `Module` mot clé.</span><span class="sxs-lookup"><span data-stu-id="1c73e-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="1c73e-108">S’il s’applique à l’intégralité de l’assembly, vous utilisez le mot clé [assembly](assembly.md) .</span><span class="sxs-lookup"><span data-stu-id="1c73e-108">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="1c73e-109">Le `Module` modificateur n’est pas le même que l' [instruction module](../statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1c73e-109">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c73e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c73e-110">See also</span></span>

- [<span data-ttu-id="1c73e-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="1c73e-111">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="1c73e-112">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="1c73e-112">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="1c73e-113">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="1c73e-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
