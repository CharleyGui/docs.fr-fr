---
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 8506aba7e64f2dbd975cc275cefb7b5bb1aefda5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875006"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="402d9-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="402d9-102">Overridable (Visual Basic)</span></span>

<span data-ttu-id="402d9-103">Spécifie qu’une propriété ou procédure peut être substituée par une propriété ou procédure portant le même nom dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="402d9-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="402d9-104">Notes</span><span class="sxs-lookup"><span data-stu-id="402d9-104">Remarks</span></span>  

 <span data-ttu-id="402d9-105">Le `Overridable` modificateur permet à une propriété ou une méthode d’une classe d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="402d9-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="402d9-106">Le modificateur [NotOverridable](notoverridable.md) empêche une propriété ou une méthode d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="402d9-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="402d9-107">Pour plus d’informations, consultez [Concepts de base de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="402d9-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="402d9-108">Si le `Overridable` `NotOverridable` modificateur ou n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou la méthode substitue une propriété ou une méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="402d9-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="402d9-109">Si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, la valeur par défaut est `Overridable` ; sinon, elle a la valeur `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="402d9-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="402d9-110">Vous pouvez masquer ou substituer pour redéfinir un élément hérité, mais il existe des différences significatives entre les deux approches.</span><span class="sxs-lookup"><span data-stu-id="402d9-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="402d9-111">Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="402d9-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="402d9-112">Un élément qui peut être substitué est parfois appelé élément *virtuel* .</span><span class="sxs-lookup"><span data-stu-id="402d9-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="402d9-113">S’il peut être substitué, mais n’est pas nécessaire, il est parfois également appelé élément *concret* .</span><span class="sxs-lookup"><span data-stu-id="402d9-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="402d9-114">Vous pouvez utiliser `Overridable` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="402d9-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="402d9-115">Modificateurs combinés</span><span class="sxs-lookup"><span data-stu-id="402d9-115">Combined Modifiers</span></span>  

 <span data-ttu-id="402d9-116">Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une `Private` méthode.</span><span class="sxs-lookup"><span data-stu-id="402d9-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="402d9-117">Vous ne pouvez pas spécifier `Overridable` avec `MustOverride` , `NotOverridable` ou `Shared` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="402d9-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="402d9-118">Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="402d9-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="402d9-119">Usage</span><span class="sxs-lookup"><span data-stu-id="402d9-119">Usage</span></span>  

 <span data-ttu-id="402d9-120">Le modificateur `Overridable` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="402d9-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="402d9-121">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="402d9-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="402d9-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="402d9-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="402d9-123">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="402d9-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="402d9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="402d9-124">See also</span></span>

- [<span data-ttu-id="402d9-125">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="402d9-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="402d9-126">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="402d9-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="402d9-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="402d9-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="402d9-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="402d9-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="402d9-129">Remplacements</span><span class="sxs-lookup"><span data-stu-id="402d9-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="402d9-130">Mots clés</span><span class="sxs-lookup"><span data-stu-id="402d9-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="402d9-131">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="402d9-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
