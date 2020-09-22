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
ms.openlocfilehash: cf73f07b6e13d524281129e3c5d8dceceb90764c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867950"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="3a9c0-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a9c0-102">MustOverride (Visual Basic)</span></span>

<span data-ttu-id="3a9c0-103">Spécifie qu’une propriété ou procédure n’est pas implémentée dans cette classe et qu’elle doit être substituée dans une classe dérivée avant de pouvoir être utilisée.</span><span class="sxs-lookup"><span data-stu-id="3a9c0-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a9c0-104">Notes</span><span class="sxs-lookup"><span data-stu-id="3a9c0-104">Remarks</span></span>  

 <span data-ttu-id="3a9c0-105">Vous pouvez utiliser `MustOverride` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="3a9c0-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="3a9c0-106">La propriété ou la procédure qui spécifie `MustOverride` doit être membre d’une classe, et la classe doit être marquée [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="3a9c0-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3a9c0-107">Règles</span><span class="sxs-lookup"><span data-stu-id="3a9c0-107">Rules</span></span>  
  
- <span data-ttu-id="3a9c0-108">**Déclaration incomplète.**</span><span class="sxs-lookup"><span data-stu-id="3a9c0-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="3a9c0-109">Lorsque vous spécifiez `MustOverride` , vous ne fournissez pas de lignes de code supplémentaires pour la propriété ou la procédure, pas même l' `End Function` `End Property` instruction, ou `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="3a9c0-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="3a9c0-110">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="3a9c0-110">**Combined Modifiers.**</span></span> <span data-ttu-id="3a9c0-111">Vous ne pouvez pas spécifier `MustOverride` avec `NotOverridable` , `Overridable` ou `Shared` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="3a9c0-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="3a9c0-112">**Occultation et substitution.**</span><span class="sxs-lookup"><span data-stu-id="3a9c0-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="3a9c0-113">L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="3a9c0-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="3a9c0-114">Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="3a9c0-114">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="3a9c0-115">**Autres termes.**</span><span class="sxs-lookup"><span data-stu-id="3a9c0-115">**Alternate Terms.**</span></span> <span data-ttu-id="3a9c0-116">Un élément qui ne peut pas être utilisé sauf dans une substitution est parfois appelé élément *virtuel pur* .</span><span class="sxs-lookup"><span data-stu-id="3a9c0-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="3a9c0-117">Le modificateur `MustOverride` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="3a9c0-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3a9c0-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="3a9c0-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="3a9c0-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="3a9c0-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="3a9c0-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="3a9c0-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3a9c0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a9c0-121">See also</span></span>

- [<span data-ttu-id="3a9c0-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3a9c0-122">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="3a9c0-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="3a9c0-123">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="3a9c0-124">Remplacements</span><span class="sxs-lookup"><span data-stu-id="3a9c0-124">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="3a9c0-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3a9c0-125">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="3a9c0-126">Mots clés</span><span class="sxs-lookup"><span data-stu-id="3a9c0-126">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="3a9c0-127">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a9c0-127">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
