---
title: Private
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 0c855c4e08b365b4cb75ab062d2ec304a79612ab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347914"
---
# <a name="private-visual-basic"></a><span data-ttu-id="07c71-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07c71-102">Private (Visual Basic)</span></span>
<span data-ttu-id="07c71-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur contexte de déclaration, y compris à partir de tous les types contenus.</span><span class="sxs-lookup"><span data-stu-id="07c71-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07c71-104">Notes</span><span class="sxs-lookup"><span data-stu-id="07c71-104">Remarks</span></span>  
 <span data-ttu-id="07c71-105">Si un élément de programmation représente une fonctionnalité propriétaire ou contient des données confidentielles, vous souhaitez généralement limiter l’accès à celui-ci aussi strictement que possible.</span><span class="sxs-lookup"><span data-stu-id="07c71-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="07c71-106">Vous atteignez la limite maximale en autorisant uniquement le module, la classe ou la structure qui le définit à y accéder.</span><span class="sxs-lookup"><span data-stu-id="07c71-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="07c71-107">Pour limiter l’accès à un élément de cette manière, vous pouvez le déclarer avec `Private`.</span><span class="sxs-lookup"><span data-stu-id="07c71-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="07c71-108">Vous pouvez également utiliser le modificateur d’accès [protected Private](private-protected.md) , qui rend un membre accessible à partir de cette classe et à partir de classes dérivées situées dans son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="07c71-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="07c71-109">règles</span><span class="sxs-lookup"><span data-stu-id="07c71-109">Rules</span></span>  

- <span data-ttu-id="07c71-110">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="07c71-110">**Declaration Context.**</span></span> <span data-ttu-id="07c71-111">Vous pouvez utiliser `Private` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="07c71-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="07c71-112">Cela signifie que le contexte de déclaration pour un élément `Private` doit être un module, une classe ou une structure, et ne peut pas être un fichier source, un espace de noms, une interface ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="07c71-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="07c71-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="07c71-113">Behavior</span></span>  
  
- <span data-ttu-id="07c71-114">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="07c71-114">**Access Level.**</span></span> <span data-ttu-id="07c71-115">Tout le code dans un contexte de déclaration peut accéder à ses éléments `Private`.</span><span class="sxs-lookup"><span data-stu-id="07c71-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="07c71-116">Cela comprend le code dans un type contenu, tel qu’une classe imbriquée ou une expression d’assignation dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="07c71-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="07c71-117">Aucun code en dehors du contexte de déclaration ne peut accéder à ses éléments `Private`.</span><span class="sxs-lookup"><span data-stu-id="07c71-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="07c71-118">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="07c71-118">**Access Modifiers.**</span></span> <span data-ttu-id="07c71-119">Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="07c71-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="07c71-120">Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="07c71-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="07c71-121">Le modificateur `Private` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="07c71-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="07c71-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="07c71-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="07c71-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="07c71-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="07c71-125">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="07c71-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="07c71-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="07c71-128">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="07c71-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="07c71-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="07c71-131">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="07c71-132">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="07c71-133">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="07c71-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="07c71-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07c71-134">See also</span></span>

- [<span data-ttu-id="07c71-135">Public</span><span class="sxs-lookup"><span data-stu-id="07c71-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="07c71-136">Protected</span><span class="sxs-lookup"><span data-stu-id="07c71-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="07c71-137">Friend</span><span class="sxs-lookup"><span data-stu-id="07c71-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="07c71-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="07c71-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="07c71-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="07c71-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="07c71-140">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07c71-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="07c71-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="07c71-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="07c71-142">Structures</span><span class="sxs-lookup"><span data-stu-id="07c71-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="07c71-143">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="07c71-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
