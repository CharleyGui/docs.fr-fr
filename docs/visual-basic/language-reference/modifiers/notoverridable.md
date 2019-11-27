---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351445"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="ba5c0-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba5c0-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="ba5c0-103">Spécifie qu’une propriété ou procédure ne peut pas être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba5c0-104">Notes</span><span class="sxs-lookup"><span data-stu-id="ba5c0-104">Remarks</span></span>  
 <span data-ttu-id="ba5c0-105">Le modificateur `NotOverridable` empêche une propriété ou une méthode d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="ba5c0-106">Le modificateur [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) permet à une propriété ou à une méthode d’une classe d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="ba5c0-107">Pour plus d’informations, consultez [Concepts de base de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ba5c0-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="ba5c0-108">Si le modificateur `Overridable` ou `NotOverridable` n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou la méthode substitue une propriété ou une méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="ba5c0-109">Si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, la valeur par défaut est `Overridable`; dans le cas contraire, il est `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="ba5c0-110">Un élément qui ne peut pas être substitué est parfois appelé élément *sealed* .</span><span class="sxs-lookup"><span data-stu-id="ba5c0-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="ba5c0-111">Vous pouvez utiliser `NotOverridable` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="ba5c0-112">Vous pouvez spécifier `NotOverridable` uniquement sur une propriété ou une procédure qui remplace une autre propriété ou procédure, autrement dit, uniquement en association avec `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="ba5c0-113">Modificateurs combinés</span><span class="sxs-lookup"><span data-stu-id="ba5c0-113">Combined Modifiers</span></span>  
 <span data-ttu-id="ba5c0-114">Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une méthode `Private`.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="ba5c0-115">Vous ne pouvez pas spécifier `NotOverridable` avec `MustOverride`, `Overridable`ou `Shared` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ba5c0-116">Utilisation</span><span class="sxs-lookup"><span data-stu-id="ba5c0-116">Usage</span></span>  
 <span data-ttu-id="ba5c0-117">Le modificateur `NotOverridable` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="ba5c0-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ba5c0-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="ba5c0-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ba5c0-119">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="ba5c0-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ba5c0-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="ba5c0-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba5c0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba5c0-121">See also</span></span>

- [<span data-ttu-id="ba5c0-122">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="ba5c0-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="ba5c0-123">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="ba5c0-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="ba5c0-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ba5c0-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="ba5c0-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="ba5c0-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="ba5c0-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="ba5c0-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="ba5c0-127">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ba5c0-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="ba5c0-128">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba5c0-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
