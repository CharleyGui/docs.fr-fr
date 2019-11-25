---
title: Private
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351332"
---
# <a name="private-visual-basic"></a><span data-ttu-id="c6485-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6485-102">Private (Visual Basic)</span></span>
<span data-ttu-id="c6485-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span><span class="sxs-lookup"><span data-stu-id="c6485-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6485-104">Notes</span><span class="sxs-lookup"><span data-stu-id="c6485-104">Remarks</span></span>  
 <span data-ttu-id="c6485-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span><span class="sxs-lookup"><span data-stu-id="c6485-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="c6485-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span><span class="sxs-lookup"><span data-stu-id="c6485-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="c6485-107">To limit access to an element in this way, you can declare it with `Private`.</span><span class="sxs-lookup"><span data-stu-id="c6485-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="c6485-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span><span class="sxs-lookup"><span data-stu-id="c6485-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="c6485-109">Règles</span><span class="sxs-lookup"><span data-stu-id="c6485-109">Rules</span></span>  

- <span data-ttu-id="c6485-110">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="c6485-110">**Declaration Context.**</span></span> <span data-ttu-id="c6485-111">Vous pouvez utiliser `Private` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="c6485-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="c6485-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span><span class="sxs-lookup"><span data-stu-id="c6485-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c6485-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="c6485-113">Behavior</span></span>  
  
- <span data-ttu-id="c6485-114">**Access Level.**</span><span class="sxs-lookup"><span data-stu-id="c6485-114">**Access Level.**</span></span> <span data-ttu-id="c6485-115">All code within a declaration context can access its `Private` elements.</span><span class="sxs-lookup"><span data-stu-id="c6485-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="c6485-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span><span class="sxs-lookup"><span data-stu-id="c6485-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="c6485-117">No code outside of the declaration context can access its `Private` elements.</span><span class="sxs-lookup"><span data-stu-id="c6485-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="c6485-118">**Access Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="c6485-118">**Access Modifiers.**</span></span> <span data-ttu-id="c6485-119">The keywords that specify access level are called *access modifiers*.</span><span class="sxs-lookup"><span data-stu-id="c6485-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="c6485-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c6485-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="c6485-121">Le modificateur `Private` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="c6485-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c6485-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="c6485-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="c6485-124">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="c6485-125">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="c6485-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="c6485-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="c6485-128">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="c6485-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c6485-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="c6485-131">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c6485-132">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="c6485-133">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6485-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6485-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6485-134">See also</span></span>

- [<span data-ttu-id="c6485-135">Public</span><span class="sxs-lookup"><span data-stu-id="c6485-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="c6485-136">Protected</span><span class="sxs-lookup"><span data-stu-id="c6485-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="c6485-137">Friend</span><span class="sxs-lookup"><span data-stu-id="c6485-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="c6485-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c6485-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="c6485-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="c6485-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="c6485-140">Procédures</span><span class="sxs-lookup"><span data-stu-id="c6485-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c6485-141">Structures</span><span class="sxs-lookup"><span data-stu-id="c6485-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c6485-142">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="c6485-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
