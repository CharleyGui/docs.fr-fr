---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373158"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="9aaa1-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aaa1-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="9aaa1-103">Spécifie qu’un attribut au début d’un fichier source s’applique à l’assembly entier.</span><span class="sxs-lookup"><span data-stu-id="9aaa1-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aaa1-104">Notes</span><span class="sxs-lookup"><span data-stu-id="9aaa1-104">Remarks</span></span>  
 <span data-ttu-id="9aaa1-105">De nombreux attributs se rapportent à un élément de programmation individuel, tel qu’une classe ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="9aaa1-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="9aaa1-106">Vous appliquez ce type d’attribut en attachant le bloc d’attributs, entre crochets pointus ( `< >` ), directement à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="9aaa1-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="9aaa1-107">Si un attribut se rapporte non seulement à l’élément suivant mais à l’assembly entier, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut à l’aide du `Assembly` mot clé.</span><span class="sxs-lookup"><span data-stu-id="9aaa1-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="9aaa1-108">S’il s’applique au module d’assembly actuel, vous utilisez le mot clé [module](module-keyword.md) .</span><span class="sxs-lookup"><span data-stu-id="9aaa1-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="9aaa1-109">Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo. vb. dans ce cas, il n’est pas nécessaire d’utiliser un bloc d’attributs dans votre fichier de code source principal.</span><span class="sxs-lookup"><span data-stu-id="9aaa1-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aaa1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aaa1-110">See also</span></span>

- [<span data-ttu-id="9aaa1-111">Modules\<keyword></span><span class="sxs-lookup"><span data-stu-id="9aaa1-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="9aaa1-112">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="9aaa1-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
