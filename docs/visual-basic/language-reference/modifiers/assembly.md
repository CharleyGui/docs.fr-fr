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
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351646"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="2cb43-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb43-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="2cb43-103">Spécifie qu’un attribut au début d’un fichier source s’applique à l’assembly entier.</span><span class="sxs-lookup"><span data-stu-id="2cb43-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb43-104">Notes</span><span class="sxs-lookup"><span data-stu-id="2cb43-104">Remarks</span></span>  
 <span data-ttu-id="2cb43-105">De nombreux attributs se rapportent à un élément de programmation individuel, tel qu’une classe ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="2cb43-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="2cb43-106">Vous appliquez ce type d’attribut en attachant le bloc d’attributs, entre crochets pointus (`< >`), directement à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="2cb43-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="2cb43-107">Si un attribut se rapporte non seulement à l’élément suivant mais à l’assembly entier, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut à l’aide du mot clé `Assembly`.</span><span class="sxs-lookup"><span data-stu-id="2cb43-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="2cb43-108">S’il s’applique au module d’assembly actuel, vous utilisez le mot clé [module](../../../visual-basic/language-reference/modifiers/module-keyword.md) .</span><span class="sxs-lookup"><span data-stu-id="2cb43-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="2cb43-109">Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo. vb. dans ce cas, il n’est pas nécessaire d’utiliser un bloc d’attributs dans votre fichier de code source principal.</span><span class="sxs-lookup"><span data-stu-id="2cb43-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb43-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cb43-110">See also</span></span>

- [<span data-ttu-id="2cb43-111">\<mot clé> du module</span><span class="sxs-lookup"><span data-stu-id="2cb43-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="2cb43-112">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="2cb43-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
