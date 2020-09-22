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
ms.openlocfilehash: f2b6a126435b111ef56ee2a9870ea6fbddf87901
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867688"
---
# <a name="public-visual-basic"></a><span data-ttu-id="79c67-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c67-102">Public (Visual Basic)</span></span>

<span data-ttu-id="79c67-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés n’ont pas de restrictions d’accès.</span><span class="sxs-lookup"><span data-stu-id="79c67-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79c67-104">Notes</span><span class="sxs-lookup"><span data-stu-id="79c67-104">Remarks</span></span>  

 <span data-ttu-id="79c67-105">Si vous publiez un composant ou un ensemble de composants, par exemple une bibliothèque de classes, vous souhaitez généralement que les éléments de programmation soient accessibles par tout code qui interagit avec votre assembly.</span><span class="sxs-lookup"><span data-stu-id="79c67-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="79c67-106">Pour conférer un accès illimité à un élément, vous pouvez le déclarer avec `Public` .</span><span class="sxs-lookup"><span data-stu-id="79c67-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="79c67-107">L’accès public est le niveau normal d’un élément de programmation lorsque vous n’avez pas besoin de limiter l’accès à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="79c67-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="79c67-108">Notez que le niveau d’accès d’un élément déclaré dans une interface, un module, une classe ou une structure est défini par défaut sur `Public` si vous ne le déclarez pas dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="79c67-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="79c67-109">Règles</span><span class="sxs-lookup"><span data-stu-id="79c67-109">Rules</span></span>  
  
- <span data-ttu-id="79c67-110">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="79c67-110">**Declaration Context.**</span></span> <span data-ttu-id="79c67-111">Vous pouvez utiliser `Public` uniquement au niveau du module, de l’interface ou de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="79c67-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="79c67-112">Cela signifie que le contexte de déclaration pour un `Public` élément doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure, et ne peut pas être une procédure.</span><span class="sxs-lookup"><span data-stu-id="79c67-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="79c67-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="79c67-113">Behavior</span></span>  
  
- <span data-ttu-id="79c67-114">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="79c67-114">**Access Level.**</span></span> <span data-ttu-id="79c67-115">Tout le code qui peut accéder à un module, une classe ou une structure peut accéder à ses `Public` éléments.</span><span class="sxs-lookup"><span data-stu-id="79c67-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="79c67-116">**Accès par défaut.**</span><span class="sxs-lookup"><span data-stu-id="79c67-116">**Default Access.**</span></span> <span data-ttu-id="79c67-117">Les variables locales à l’intérieur d’une procédure utilisent par défaut un accès public, et vous ne pouvez pas utiliser de modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="79c67-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="79c67-118">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="79c67-118">**Access Modifiers.**</span></span> <span data-ttu-id="79c67-119">Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="79c67-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="79c67-120">Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="79c67-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="79c67-121">Le modificateur `Public` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="79c67-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="79c67-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="79c67-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="79c67-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="79c67-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="79c67-125">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="79c67-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="79c67-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="79c67-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="79c67-128">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="79c67-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="79c67-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="79c67-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="79c67-131">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="79c67-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="79c67-132">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="79c67-132">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="79c67-133">Property Statement</span><span class="sxs-lookup"><span data-stu-id="79c67-133">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="79c67-134">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="79c67-134">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="79c67-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="79c67-135">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="79c67-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79c67-136">See also</span></span>

- [<span data-ttu-id="79c67-137">Protect</span><span class="sxs-lookup"><span data-stu-id="79c67-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="79c67-138">Friend</span><span class="sxs-lookup"><span data-stu-id="79c67-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="79c67-139">Privé</span><span class="sxs-lookup"><span data-stu-id="79c67-139">Private</span></span>](private.md)
- [<span data-ttu-id="79c67-140">Protégé privé</span><span class="sxs-lookup"><span data-stu-id="79c67-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="79c67-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="79c67-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="79c67-142">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79c67-142">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="79c67-143">Procédures</span><span class="sxs-lookup"><span data-stu-id="79c67-143">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="79c67-144">Structures</span><span class="sxs-lookup"><span data-stu-id="79c67-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="79c67-145">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="79c67-145">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
