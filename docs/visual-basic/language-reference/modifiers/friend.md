---
title: Friend (Visual Basic)
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
ms.openlocfilehash: 3e30267c8aa11ce97b3b3064ff0954378dab57af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959798"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="3c5bc-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="3c5bc-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de l’assembly qui contient leur déclaration.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c5bc-104">Notes</span><span class="sxs-lookup"><span data-stu-id="3c5bc-104">Remarks</span></span>  
 <span data-ttu-id="3c5bc-105">Dans de nombreux cas, vous souhaitez que les éléments de programmation tels que les classes et les structures soient utilisés par l’assembly entier, non seulement par le composant qui les déclare.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="3c5bc-106">Toutefois, vous ne voudrez peut-être pas qu’elles soient accessibles par du code en dehors de l’assembly (par exemple, si l’application est propriétaire).</span><span class="sxs-lookup"><span data-stu-id="3c5bc-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="3c5bc-107">Si vous souhaitez limiter l’accès à un élément de cette manière, vous pouvez le déclarer à l’aide `Friend` du modificateur.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="3c5bc-108">Le code d’autres classes, structures et modules compilés dans le même assembly peut accéder à tous `Friend` les éléments de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="3c5bc-109">`Friend`l’accès est souvent le niveau préféré pour les éléments de programmation d’une `Friend` application, et est le niveau d’accès par défaut d’une interface, d’un module, d’une classe ou d’une structure.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="3c5bc-110">Vous pouvez utiliser `Friend` uniquement au niveau du module, de l’interface ou de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="3c5bc-111">Par conséquent, le contexte de Déclaration `Friend` pour un élément doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure; il ne peut pas s’agir d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="3c5bc-112">Vous pouvez également utiliser le modificateur d’accès [Protected Friend](protected-friend.md) , qui rend un membre de classe accessible à partir de cette classe, des classes dérivées et du même assembly dans lequel la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="3c5bc-113">Pour restreindre l’accès à un membre à partir de sa classe et à partir de classes dérivées dans le même assembly, vous utilisez le modificateur d’accès [protected Private](private-protected.md) .</span><span class="sxs-lookup"><span data-stu-id="3c5bc-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="3c5bc-114">Pour une comparaison de `Friend` et des autres modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3c5bc-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c5bc-115">Vous pouvez spécifier qu’un autre assembly est un assembly friend, ce qui lui permet d’accéder à tous les types `Friend`et membres marqués comme.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="3c5bc-116">Pour plus d’informations, consultez [Assemblys friend](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3c5bc-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c5bc-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c5bc-117">Example</span></span>  
 <span data-ttu-id="3c5bc-118">La classe suivante utilise le `Friend` modificateur pour permettre à d’autres éléments de programmation dans le même assembly d’accéder à certains membres.</span><span class="sxs-lookup"><span data-stu-id="3c5bc-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="3c5bc-119">Usage</span><span class="sxs-lookup"><span data-stu-id="3c5bc-119">Usage</span></span>  
 <span data-ttu-id="3c5bc-120">Vous pouvez utiliser le `Friend` modificateur dans ces contextes:</span><span class="sxs-lookup"><span data-stu-id="3c5bc-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="3c5bc-121">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="3c5bc-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="3c5bc-123">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="3c5bc-124">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="3c5bc-125">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="3c5bc-126">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="3c5bc-127">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="3c5bc-128">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="3c5bc-129">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="3c5bc-130">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="3c5bc-131">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="3c5bc-132">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="3c5bc-133">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c5bc-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c5bc-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c5bc-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="3c5bc-135">Public</span><span class="sxs-lookup"><span data-stu-id="3c5bc-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="3c5bc-136">Protected</span><span class="sxs-lookup"><span data-stu-id="3c5bc-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="3c5bc-137">Private</span><span class="sxs-lookup"><span data-stu-id="3c5bc-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="3c5bc-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="3c5bc-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="3c5bc-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="3c5bc-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="3c5bc-140">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c5bc-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="3c5bc-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="3c5bc-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="3c5bc-142">Structures</span><span class="sxs-lookup"><span data-stu-id="3c5bc-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="3c5bc-143">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="3c5bc-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
