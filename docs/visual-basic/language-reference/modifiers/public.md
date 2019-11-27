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
# <a name="public-visual-basic"></a><span data-ttu-id="ae4ab-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-102">Public (Visual Basic)</span></span>
<span data-ttu-id="ae4ab-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés n’ont pas de restrictions d’accès.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae4ab-104">Notes</span><span class="sxs-lookup"><span data-stu-id="ae4ab-104">Remarks</span></span>  
 <span data-ttu-id="ae4ab-105">Si vous publiez un composant ou un ensemble de composants, par exemple une bibliothèque de classes, vous souhaitez généralement que les éléments de programmation soient accessibles par tout code qui interagit avec votre assembly.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="ae4ab-106">Pour conférer un accès illimité à un élément, vous pouvez le déclarer avec `Public`.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="ae4ab-107">L’accès public est le niveau normal d’un élément de programmation lorsque vous n’avez pas besoin de limiter l’accès à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="ae4ab-108">Notez que le niveau d’accès d’un élément déclaré dans une interface, un module, une classe ou une structure est défini par défaut sur `Public` si vous ne le déclarez pas dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ae4ab-109">Règles</span><span class="sxs-lookup"><span data-stu-id="ae4ab-109">Rules</span></span>  
  
- <span data-ttu-id="ae4ab-110">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="ae4ab-110">**Declaration Context.**</span></span> <span data-ttu-id="ae4ab-111">Vous pouvez utiliser `Public` uniquement au niveau du module, de l’interface ou de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="ae4ab-112">Cela signifie que le contexte de déclaration pour un élément de `Public` doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure, et ne peut pas être une procédure.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ae4ab-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="ae4ab-113">Behavior</span></span>  
  
- <span data-ttu-id="ae4ab-114">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="ae4ab-114">**Access Level.**</span></span> <span data-ttu-id="ae4ab-115">Tout le code qui peut accéder à un module, une classe ou une structure peut accéder à ses éléments `Public`.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="ae4ab-116">**Accès par défaut.**</span><span class="sxs-lookup"><span data-stu-id="ae4ab-116">**Default Access.**</span></span> <span data-ttu-id="ae4ab-117">Les variables locales à l’intérieur d’une procédure utilisent par défaut un accès public, et vous ne pouvez pas utiliser de modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="ae4ab-118">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="ae4ab-118">**Access Modifiers.**</span></span> <span data-ttu-id="ae4ab-119">Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="ae4ab-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="ae4ab-120">Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ae4ab-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="ae4ab-121">Le modificateur `Public` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="ae4ab-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ae4ab-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ae4ab-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="ae4ab-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="ae4ab-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ae4ab-125">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="ae4ab-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="ae4ab-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="ae4ab-128">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="ae4ab-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ae4ab-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="ae4ab-131">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="ae4ab-132">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="ae4ab-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="ae4ab-133">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ae4ab-134">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="ae4ab-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae4ab-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae4ab-136">See also</span></span>

- [<span data-ttu-id="ae4ab-137">Protected</span><span class="sxs-lookup"><span data-stu-id="ae4ab-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="ae4ab-138">Friend</span><span class="sxs-lookup"><span data-stu-id="ae4ab-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="ae4ab-139">Private</span><span class="sxs-lookup"><span data-stu-id="ae4ab-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="ae4ab-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="ae4ab-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="ae4ab-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="ae4ab-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="ae4ab-142">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae4ab-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ae4ab-143">Procédures</span><span class="sxs-lookup"><span data-stu-id="ae4ab-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ae4ab-144">Structures</span><span class="sxs-lookup"><span data-stu-id="ae4ab-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ae4ab-145">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="ae4ab-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
