---
title: Protected
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398218"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="1d680-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d680-102">Protected (Visual Basic)</span></span>

<span data-ttu-id="1d680-103">Modificateur d’accès au membre qui spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur propre classe ou d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="1d680-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d680-104">Notes</span><span class="sxs-lookup"><span data-stu-id="1d680-104">Remarks</span></span>

<span data-ttu-id="1d680-105">Parfois, un élément de programmation déclaré dans une classe contient des données sensibles ou du Code restreint, et vous souhaitez limiter l’accès à l’élément.</span><span class="sxs-lookup"><span data-stu-id="1d680-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="1d680-106">Toutefois, si la classe peut être héritée et que vous vous attendez à une hiérarchie de classes dérivées, il peut être nécessaire que ces classes dérivées accèdent aux données ou au code.</span><span class="sxs-lookup"><span data-stu-id="1d680-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="1d680-107">Dans ce cas, vous souhaitez que l’élément soit accessible à la fois à partir de la classe de base et à partir de toutes les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1d680-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="1d680-108">Pour limiter l’accès à un élément de cette manière, vous pouvez le déclarer avec `Protected` .</span><span class="sxs-lookup"><span data-stu-id="1d680-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="1d680-109">Le `Protected` modificateur d’accès peut être combiné avec deux autres modificateurs :</span><span class="sxs-lookup"><span data-stu-id="1d680-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="1d680-110">Le modificateur [Friend protégé](protected-friend.md) rend un membre de classe accessible à partir de cette classe, des classes dérivées et du même assembly dans lequel la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="1d680-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="1d680-111">Le modificateur [protected Private](private-protected.md) rend un membre de classe accessible par les types dérivés, mais uniquement au sein de son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="1d680-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="1d680-112">Règles</span><span class="sxs-lookup"><span data-stu-id="1d680-112">Rules</span></span>

<span data-ttu-id="1d680-113">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="1d680-113">**Declaration Context.**</span></span> <span data-ttu-id="1d680-114">Vous pouvez utiliser `Protected` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="1d680-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="1d680-115">Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="1d680-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="1d680-116">Comportement</span><span class="sxs-lookup"><span data-stu-id="1d680-116">Behavior</span></span>

- <span data-ttu-id="1d680-117">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="1d680-117">**Access Level.**</span></span> <span data-ttu-id="1d680-118">Tout le code d’une classe peut accéder à ses éléments.</span><span class="sxs-lookup"><span data-stu-id="1d680-118">All code in a class can access its elements.</span></span> <span data-ttu-id="1d680-119">Le code d’une classe qui dérive d’une classe de base peut accéder à tous les `Protected` éléments de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="1d680-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="1d680-120">Cela est vrai pour toutes les générations de dérivation.</span><span class="sxs-lookup"><span data-stu-id="1d680-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="1d680-121">Cela signifie qu’une classe peut accéder aux `Protected` éléments de la classe de base de la classe de base, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1d680-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="1d680-122">L’accès protégé n’est pas un sur-ensemble ou un sous-ensemble d’accès Friend.</span><span class="sxs-lookup"><span data-stu-id="1d680-122">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="1d680-123">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="1d680-123">**Access Modifiers.**</span></span> <span data-ttu-id="1d680-124">Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="1d680-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="1d680-125">Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1d680-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="1d680-126">Le modificateur `Protected` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="1d680-126">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="1d680-127">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-127">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="1d680-128">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-128">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="1d680-129">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="1d680-129">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="1d680-130">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="1d680-130">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="1d680-131">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-131">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="1d680-132">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-132">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="1d680-133">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="1d680-133">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="1d680-134">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-134">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="1d680-135">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-135">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="1d680-136">Property Statement</span><span class="sxs-lookup"><span data-stu-id="1d680-136">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="1d680-137">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="1d680-137">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="1d680-138">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d680-138">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="1d680-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d680-139">See also</span></span>

- [<span data-ttu-id="1d680-140">Public</span><span class="sxs-lookup"><span data-stu-id="1d680-140">Public</span></span>](public.md)
- [<span data-ttu-id="1d680-141">Contact</span><span class="sxs-lookup"><span data-stu-id="1d680-141">Friend</span></span>](friend.md)
- [<span data-ttu-id="1d680-142">Privé</span><span class="sxs-lookup"><span data-stu-id="1d680-142">Private</span></span>](private.md)
- [<span data-ttu-id="1d680-143">Protégé privé</span><span class="sxs-lookup"><span data-stu-id="1d680-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="1d680-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="1d680-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="1d680-145">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d680-145">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="1d680-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="1d680-146">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="1d680-147">Structures</span><span class="sxs-lookup"><span data-stu-id="1d680-147">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="1d680-148">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="1d680-148">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
