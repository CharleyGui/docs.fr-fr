---
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351295"
---
# <a name="public-visual-basic"></a><span data-ttu-id="86d34-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86d34-102">Public (Visual Basic)</span></span>
<span data-ttu-id="86d34-103">Specifies that one or more declared programming elements have no access restrictions.</span><span class="sxs-lookup"><span data-stu-id="86d34-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d34-104">Notes</span><span class="sxs-lookup"><span data-stu-id="86d34-104">Remarks</span></span>  
 <span data-ttu-id="86d34-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span><span class="sxs-lookup"><span data-stu-id="86d34-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="86d34-106">To confer such unlimited access on an element, you can declare it with `Public`.</span><span class="sxs-lookup"><span data-stu-id="86d34-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="86d34-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span><span class="sxs-lookup"><span data-stu-id="86d34-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="86d34-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span><span class="sxs-lookup"><span data-stu-id="86d34-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="86d34-109">Règles</span><span class="sxs-lookup"><span data-stu-id="86d34-109">Rules</span></span>  
  
- <span data-ttu-id="86d34-110">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="86d34-110">**Declaration Context.**</span></span> <span data-ttu-id="86d34-111">You can use `Public` only at module, interface, or namespace level.</span><span class="sxs-lookup"><span data-stu-id="86d34-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="86d34-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span><span class="sxs-lookup"><span data-stu-id="86d34-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="86d34-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="86d34-113">Behavior</span></span>  
  
- <span data-ttu-id="86d34-114">**Access Level.**</span><span class="sxs-lookup"><span data-stu-id="86d34-114">**Access Level.**</span></span> <span data-ttu-id="86d34-115">All code that can access a module, class, or structure can access its `Public` elements.</span><span class="sxs-lookup"><span data-stu-id="86d34-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="86d34-116">**Default Access.**</span><span class="sxs-lookup"><span data-stu-id="86d34-116">**Default Access.**</span></span> <span data-ttu-id="86d34-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span><span class="sxs-lookup"><span data-stu-id="86d34-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="86d34-118">**Access Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="86d34-118">**Access Modifiers.**</span></span> <span data-ttu-id="86d34-119">The keywords that specify access level are called *access modifiers*.</span><span class="sxs-lookup"><span data-stu-id="86d34-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="86d34-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="86d34-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="86d34-121">Le modificateur `Public` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="86d34-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="86d34-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="86d34-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="86d34-124">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="86d34-125">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="86d34-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="86d34-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="86d34-128">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="86d34-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="86d34-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="86d34-131">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="86d34-132">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="86d34-133">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="86d34-134">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="86d34-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="86d34-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="86d34-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86d34-136">See also</span></span>

- [<span data-ttu-id="86d34-137">Protected</span><span class="sxs-lookup"><span data-stu-id="86d34-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="86d34-138">Friend</span><span class="sxs-lookup"><span data-stu-id="86d34-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="86d34-139">Private</span><span class="sxs-lookup"><span data-stu-id="86d34-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="86d34-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="86d34-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="86d34-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="86d34-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="86d34-142">Access levels in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86d34-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="86d34-143">Procédures</span><span class="sxs-lookup"><span data-stu-id="86d34-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="86d34-144">Structures</span><span class="sxs-lookup"><span data-stu-id="86d34-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="86d34-145">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="86d34-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
