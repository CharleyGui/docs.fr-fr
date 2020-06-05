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
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392156"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="da113-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da113-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="da113-103">Spécifie qu’une propriété ou procédure ne peut pas être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="da113-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da113-104">Notes</span><span class="sxs-lookup"><span data-stu-id="da113-104">Remarks</span></span>  
 <span data-ttu-id="da113-105">Le `NotOverridable` modificateur empêche une propriété ou une méthode d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="da113-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="da113-106">Le modificateur [Overridable](overridable.md) permet à une propriété ou à une méthode d’une classe d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="da113-106">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="da113-107">Pour plus d’informations, consultez [Concepts de base de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="da113-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="da113-108">Si le `Overridable` `NotOverridable` modificateur ou n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou la méthode substitue une propriété ou une méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="da113-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="da113-109">Si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, la valeur par défaut est `Overridable` ; sinon, elle a la valeur `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="da113-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="da113-110">Un élément qui ne peut pas être substitué est parfois appelé élément *sealed* .</span><span class="sxs-lookup"><span data-stu-id="da113-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="da113-111">Vous pouvez utiliser `NotOverridable` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="da113-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="da113-112">Vous pouvez spécifier `NotOverridable` uniquement sur une propriété ou une procédure qui remplace une autre propriété ou procédure, autrement dit, uniquement en association avec `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="da113-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="da113-113">Modificateurs combinés</span><span class="sxs-lookup"><span data-stu-id="da113-113">Combined Modifiers</span></span>  
 <span data-ttu-id="da113-114">Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une `Private` méthode.</span><span class="sxs-lookup"><span data-stu-id="da113-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="da113-115">Vous ne pouvez pas spécifier `NotOverridable` avec `MustOverride` , `Overridable` ou `Shared` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="da113-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="da113-116">Utilisation</span><span class="sxs-lookup"><span data-stu-id="da113-116">Usage</span></span>  
 <span data-ttu-id="da113-117">Le modificateur `NotOverridable` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="da113-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="da113-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="da113-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="da113-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="da113-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="da113-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="da113-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="da113-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da113-121">See also</span></span>

- [<span data-ttu-id="da113-122">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="da113-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="da113-123">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="da113-123">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="da113-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="da113-124">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="da113-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="da113-125">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="da113-126">Remplacements</span><span class="sxs-lookup"><span data-stu-id="da113-126">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="da113-127">Mots clés</span><span class="sxs-lookup"><span data-stu-id="da113-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="da113-128">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da113-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
