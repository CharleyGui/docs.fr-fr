---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351483"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="e50cb-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e50cb-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="e50cb-103">Spécifie qu’une propriété ou procédure n’est pas implémentée dans cette classe et qu’elle doit être substituée dans une classe dérivée avant de pouvoir être utilisée.</span><span class="sxs-lookup"><span data-stu-id="e50cb-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e50cb-104">Notes</span><span class="sxs-lookup"><span data-stu-id="e50cb-104">Remarks</span></span>  
 <span data-ttu-id="e50cb-105">Vous pouvez utiliser `MustOverride` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="e50cb-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="e50cb-106">La propriété ou la procédure qui spécifie `MustOverride` doit être membre d’une classe, et la classe doit être marquée [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="e50cb-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e50cb-107">Règles</span><span class="sxs-lookup"><span data-stu-id="e50cb-107">Rules</span></span>  
  
- <span data-ttu-id="e50cb-108">**Déclaration incomplète.**</span><span class="sxs-lookup"><span data-stu-id="e50cb-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="e50cb-109">Lorsque vous spécifiez `MustOverride`, vous ne fournissez pas de lignes de code supplémentaires pour la propriété ou la procédure, pas même pour l’instruction `End Function`, `End Property`ou `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="e50cb-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="e50cb-110">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="e50cb-110">**Combined Modifiers.**</span></span> <span data-ttu-id="e50cb-111">Vous ne pouvez pas spécifier `MustOverride` avec `NotOverridable`, `Overridable`ou `Shared` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="e50cb-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="e50cb-112">**Occultation et substitution.**</span><span class="sxs-lookup"><span data-stu-id="e50cb-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="e50cb-113">L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="e50cb-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e50cb-114">Pour plus d’informations, consultez [occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="e50cb-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="e50cb-115">**Autres termes.**</span><span class="sxs-lookup"><span data-stu-id="e50cb-115">**Alternate Terms.**</span></span> <span data-ttu-id="e50cb-116">Un élément qui ne peut pas être utilisé sauf dans une substitution est parfois appelé élément *virtuel pur* .</span><span class="sxs-lookup"><span data-stu-id="e50cb-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="e50cb-117">Le modificateur `MustOverride` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="e50cb-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e50cb-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="e50cb-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e50cb-119">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="e50cb-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e50cb-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="e50cb-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e50cb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e50cb-121">See also</span></span>

- [<span data-ttu-id="e50cb-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e50cb-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="e50cb-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="e50cb-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="e50cb-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="e50cb-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="e50cb-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="e50cb-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="e50cb-126">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e50cb-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="e50cb-127">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e50cb-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
