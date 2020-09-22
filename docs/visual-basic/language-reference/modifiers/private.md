---
title: Privées
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 59f1c1666ce38923a2861244fb377007cd0fa992
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874975"
---
# <a name="private-visual-basic"></a><span data-ttu-id="a1880-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1880-102">Private (Visual Basic)</span></span>

<span data-ttu-id="a1880-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur contexte de déclaration, y compris à partir de tous les types contenus.</span><span class="sxs-lookup"><span data-stu-id="a1880-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1880-104">Notes</span><span class="sxs-lookup"><span data-stu-id="a1880-104">Remarks</span></span>  

 <span data-ttu-id="a1880-105">Si un élément de programmation représente une fonctionnalité propriétaire ou contient des données confidentielles, vous souhaitez généralement limiter l’accès à celui-ci aussi strictement que possible.</span><span class="sxs-lookup"><span data-stu-id="a1880-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="a1880-106">Vous atteignez la limite maximale en autorisant uniquement le module, la classe ou la structure qui le définit à y accéder.</span><span class="sxs-lookup"><span data-stu-id="a1880-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="a1880-107">Pour limiter l’accès à un élément de cette manière, vous pouvez le déclarer avec `Private` .</span><span class="sxs-lookup"><span data-stu-id="a1880-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="a1880-108">Vous pouvez également utiliser le modificateur d’accès [protected Private](private-protected.md) , qui rend un membre accessible à partir de cette classe et à partir de classes dérivées situées dans son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="a1880-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="a1880-109">Règles</span><span class="sxs-lookup"><span data-stu-id="a1880-109">Rules</span></span>  

- <span data-ttu-id="a1880-110">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="a1880-110">**Declaration Context.**</span></span> <span data-ttu-id="a1880-111">Vous pouvez utiliser `Private` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="a1880-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="a1880-112">Cela signifie que le contexte de déclaration pour un `Private` élément doit être un module, une classe ou une structure, et ne peut pas être un fichier source, un espace de noms, une interface ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="a1880-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a1880-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="a1880-113">Behavior</span></span>  
  
- <span data-ttu-id="a1880-114">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="a1880-114">**Access Level.**</span></span> <span data-ttu-id="a1880-115">Tout le code dans un contexte de déclaration peut accéder à ses `Private` éléments.</span><span class="sxs-lookup"><span data-stu-id="a1880-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="a1880-116">Cela comprend le code dans un type contenu, tel qu’une classe imbriquée ou une expression d’assignation dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="a1880-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="a1880-117">Aucun code en dehors du contexte de déclaration ne peut accéder à ses `Private` éléments.</span><span class="sxs-lookup"><span data-stu-id="a1880-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="a1880-118">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="a1880-118">**Access Modifiers.**</span></span> <span data-ttu-id="a1880-119">Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="a1880-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="a1880-120">Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a1880-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="a1880-121">Le modificateur `Private` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="a1880-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a1880-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="a1880-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="a1880-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="a1880-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="a1880-125">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="a1880-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="a1880-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="a1880-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="a1880-128">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="a1880-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="a1880-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="a1880-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="a1880-131">Property Statement</span><span class="sxs-lookup"><span data-stu-id="a1880-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="a1880-132">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="a1880-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="a1880-133">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1880-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a1880-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1880-134">See also</span></span>

- [<span data-ttu-id="a1880-135">Public</span><span class="sxs-lookup"><span data-stu-id="a1880-135">Public</span></span>](public.md)
- [<span data-ttu-id="a1880-136">Protect</span><span class="sxs-lookup"><span data-stu-id="a1880-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="a1880-137">Friend</span><span class="sxs-lookup"><span data-stu-id="a1880-137">Friend</span></span>](friend.md)
- [<span data-ttu-id="a1880-138">Protégé privé</span><span class="sxs-lookup"><span data-stu-id="a1880-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="a1880-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="a1880-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="a1880-140">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1880-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a1880-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="a1880-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="a1880-142">Structures</span><span class="sxs-lookup"><span data-stu-id="a1880-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a1880-143">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="a1880-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
