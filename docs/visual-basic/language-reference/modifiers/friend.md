---
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 98f8ed947c9f4376c5778011a3a91ca8b094f9ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351560"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="4794d-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4794d-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="4794d-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de l’assembly qui contient leur déclaration.</span><span class="sxs-lookup"><span data-stu-id="4794d-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4794d-104">Notes</span><span class="sxs-lookup"><span data-stu-id="4794d-104">Remarks</span></span>  
 <span data-ttu-id="4794d-105">Dans de nombreux cas, vous souhaitez que les éléments de programmation tels que les classes et les structures soient utilisés par l’assembly entier, non seulement par le composant qui les déclare.</span><span class="sxs-lookup"><span data-stu-id="4794d-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="4794d-106">Toutefois, vous ne voudrez peut-être pas qu’elles soient accessibles par du code en dehors de l’assembly (par exemple, si l’application est propriétaire).</span><span class="sxs-lookup"><span data-stu-id="4794d-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="4794d-107">Si vous souhaitez limiter l’accès à un élément de cette manière, vous pouvez le déclarer à l’aide du modificateur `Friend`.</span><span class="sxs-lookup"><span data-stu-id="4794d-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="4794d-108">Du code dans d’autres classes, structures et modules compilés dans le même assembly peut accéder à tous les éléments `Friend` de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="4794d-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="4794d-109">`Friend` accès est souvent le niveau préféré pour les éléments de programmation d’une application, et `Friend` est le niveau d’accès par défaut d’une interface, d’un module, d’une classe ou d’une structure.</span><span class="sxs-lookup"><span data-stu-id="4794d-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="4794d-110">Vous pouvez utiliser `Friend` uniquement au niveau du module, de l’interface ou de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4794d-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="4794d-111">Par conséquent, le contexte de déclaration pour un élément `Friend` doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure ; il ne peut pas s’agir d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="4794d-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="4794d-112">Vous pouvez également utiliser le modificateur d’accès [Protected Friend](protected-friend.md) , qui rend un membre de classe accessible à partir de cette classe, des classes dérivées et du même assembly dans lequel la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="4794d-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="4794d-113">Pour restreindre l’accès à un membre à partir de sa classe et à partir de classes dérivées dans le même assembly, vous utilisez le modificateur d’accès [protected Private](private-protected.md) .</span><span class="sxs-lookup"><span data-stu-id="4794d-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="4794d-114">Pour une comparaison des `Friend` et des autres modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4794d-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4794d-115">Vous pouvez spécifier qu’un autre assembly est un assembly friend, ce qui lui permet d’accéder à tous les types et membres marqués comme `Friend`.</span><span class="sxs-lookup"><span data-stu-id="4794d-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="4794d-116">Pour plus d’informations, consultez [Assemblys friend](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="4794d-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="4794d-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="4794d-117">Example</span></span>  
 <span data-ttu-id="4794d-118">La classe suivante utilise le modificateur `Friend` pour permettre à d’autres éléments de programmation dans le même assembly d’accéder à certains membres.</span><span class="sxs-lookup"><span data-stu-id="4794d-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="4794d-119">Utilisation</span><span class="sxs-lookup"><span data-stu-id="4794d-119">Usage</span></span>  
 <span data-ttu-id="4794d-120">Vous pouvez utiliser le modificateur `Friend` dans ces contextes :</span><span class="sxs-lookup"><span data-stu-id="4794d-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="4794d-121">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="4794d-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="4794d-123">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="4794d-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="4794d-124">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="4794d-125">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="4794d-126">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="4794d-127">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="4794d-128">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="4794d-129">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="4794d-130">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="4794d-131">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="4794d-132">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="4794d-133">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="4794d-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4794d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4794d-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="4794d-135">Public</span><span class="sxs-lookup"><span data-stu-id="4794d-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="4794d-136">Protected</span><span class="sxs-lookup"><span data-stu-id="4794d-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="4794d-137">Private</span><span class="sxs-lookup"><span data-stu-id="4794d-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="4794d-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="4794d-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="4794d-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="4794d-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="4794d-140">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4794d-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="4794d-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="4794d-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="4794d-142">Structures</span><span class="sxs-lookup"><span data-stu-id="4794d-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="4794d-143">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="4794d-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
