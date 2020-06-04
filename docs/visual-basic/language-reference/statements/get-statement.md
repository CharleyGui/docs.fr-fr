---
title: Get, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404600"
---
# <a name="get-statement"></a><span data-ttu-id="f3f21-102">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="f3f21-102">Get Statement</span></span>
<span data-ttu-id="f3f21-103">Déclare une `Get` procédure de propriété utilisée pour récupérer la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3f21-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="f3f21-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="f3f21-105">Parts</span></span>  
  
|<span data-ttu-id="f3f21-106">Terme</span><span class="sxs-lookup"><span data-stu-id="f3f21-106">Term</span></span>|<span data-ttu-id="f3f21-107">Définition</span><span class="sxs-lookup"><span data-stu-id="f3f21-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="f3f21-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f3f21-108">Optional.</span></span> <span data-ttu-id="f3f21-109">Consultez la [liste des attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="f3f21-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="f3f21-110">Facultatif sur au plus une des `Get` instructions et `Set` dans cette propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="f3f21-111">Il peut s'agir d'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3f21-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="f3f21-112">-   [Protect](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="f3f21-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="f3f21-113">-   [Contact](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="f3f21-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="f3f21-114">-   [Priv](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="f3f21-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="f3f21-115">Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f3f21-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="f3f21-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f3f21-116">Optional.</span></span> <span data-ttu-id="f3f21-117">Une ou plusieurs instructions qui s’exécutent lorsque la `Get` procédure de propriété est appelée.</span><span class="sxs-lookup"><span data-stu-id="f3f21-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="f3f21-118">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f3f21-118">Required.</span></span> <span data-ttu-id="f3f21-119">Met fin à la définition de la `Get` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3f21-120">Notes</span><span class="sxs-lookup"><span data-stu-id="f3f21-120">Remarks</span></span>  
 <span data-ttu-id="f3f21-121">Chaque propriété doit avoir une `Get` procédure de propriété, sauf si la propriété est marquée `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="f3f21-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="f3f21-122">La `Get` procédure est utilisée pour retourner la valeur actuelle de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="f3f21-123">Visual Basic appelle automatiquement la procédure d’une propriété `Get` lorsqu’une expression demande la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="f3f21-124">Le corps de la déclaration de propriété peut contenir uniquement les procédures et de la propriété `Get` `Set` entre l' [instruction Property](property-statement.md) et l' `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="f3f21-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="f3f21-125">Elle ne peut pas stocker d’autres éléments que ces procédures.</span><span class="sxs-lookup"><span data-stu-id="f3f21-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="f3f21-126">En particulier, il ne peut pas stocker la valeur actuelle de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="f3f21-127">Vous devez stocker cette valeur en dehors de la propriété, car si vous la stockez à l’intérieur de l’une des procédures de propriété, l’autre procédure de propriété ne peut pas y accéder.</span><span class="sxs-lookup"><span data-stu-id="f3f21-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="f3f21-128">L’approche habituelle consiste à stocker la valeur dans une variable [privée](../modifiers/private.md) déclarée au même niveau que la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="f3f21-129">Vous devez définir une `Get` procédure à l’intérieur de la propriété à laquelle elle s’applique.</span><span class="sxs-lookup"><span data-stu-id="f3f21-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="f3f21-130">La `Get` procédure utilise par défaut le niveau d’accès de sa propriété conteneur, sauf si vous utilisez `accessmodifier` dans l' `Get` instruction.</span><span class="sxs-lookup"><span data-stu-id="f3f21-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f3f21-131">Règles</span><span class="sxs-lookup"><span data-stu-id="f3f21-131">Rules</span></span>  
  
- <span data-ttu-id="f3f21-132">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="f3f21-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="f3f21-133">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` `Set` procédure ou, mais pas pour les deux.</span><span class="sxs-lookup"><span data-stu-id="f3f21-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="f3f21-134">Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="f3f21-135">Par exemple, si la propriété est déclarée `Friend` , vous pouvez déclarer la `Get` procédure `Private` , mais pas `Public` .</span><span class="sxs-lookup"><span data-stu-id="f3f21-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="f3f21-136">Si vous définissez une `ReadOnly` propriété, la `Get` procédure représente la propriété entière.</span><span class="sxs-lookup"><span data-stu-id="f3f21-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="f3f21-137">Vous ne pouvez pas déclarer un niveau d’accès différent pour `Get` , car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="f3f21-138">**Type de retour.**</span><span class="sxs-lookup"><span data-stu-id="f3f21-138">**Return Type.**</span></span> <span data-ttu-id="f3f21-139">L' [instruction Property](property-statement.md) peut déclarer le type de données de la valeur qu’elle retourne.</span><span class="sxs-lookup"><span data-stu-id="f3f21-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="f3f21-140">La `Get` procédure retourne automatiquement ce type de données.</span><span class="sxs-lookup"><span data-stu-id="f3f21-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="f3f21-141">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="f3f21-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="f3f21-142">Si l' `Property` instruction ne spécifie pas `returntype` , la procédure retourne `Object` .</span><span class="sxs-lookup"><span data-stu-id="f3f21-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f3f21-143">Comportement</span><span class="sxs-lookup"><span data-stu-id="f3f21-143">Behavior</span></span>  
  
- <span data-ttu-id="f3f21-144">**Retour d’une procédure.**</span><span class="sxs-lookup"><span data-stu-id="f3f21-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="f3f21-145">Lorsque la `Get` procédure revient au code appelant, l’exécution continue dans l’instruction qui a demandé la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="f3f21-146">`Get`les procédures de propriété peuvent retourner une valeur à l’aide de l' [instruction return](return-statement.md) ou en affectant la valeur de retour au nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="f3f21-147">Pour plus d’informations, consultez « valeur de retour » dans l' [instruction de fonction](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f3f21-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="f3f21-148">Les `Exit Property` `Return` instructions et provoquent une sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="f3f21-149">Un nombre quelconque `Exit Property` d' `Return` instructions et peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des `Exit Property` `Return` instructions et.</span><span class="sxs-lookup"><span data-stu-id="f3f21-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="f3f21-150">**Valeur de retour.**</span><span class="sxs-lookup"><span data-stu-id="f3f21-150">**Return Value.**</span></span> <span data-ttu-id="f3f21-151">Pour retourner une valeur à partir d’une `Get` procédure, vous pouvez affecter la valeur au nom de la propriété ou l’inclure dans une [instruction return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f3f21-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="f3f21-152">L' `Return` instruction assigne simultanément la `Get` valeur de retour de la procédure et quitte la procédure.</span><span class="sxs-lookup"><span data-stu-id="f3f21-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="f3f21-153">Si vous utilisez `Exit Property` sans assigner de valeur au nom de la propriété, la `Get` procédure retourne la valeur par défaut pour le type de données de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="f3f21-154">Pour plus d’informations, consultez « valeur de retour » dans l' [instruction de fonction](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f3f21-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="f3f21-155">L’exemple suivant illustre deux façons dont la propriété en lecture seule `quoteForTheDay` peut retourner la valeur contenue dans la variable privée `quoteValue` .</span><span class="sxs-lookup"><span data-stu-id="f3f21-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="f3f21-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3f21-156">Example</span></span>  
 <span data-ttu-id="f3f21-157">L’exemple suivant utilise l' `Get` instruction pour retourner la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="f3f21-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="f3f21-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3f21-158">See also</span></span>

- [<span data-ttu-id="f3f21-159">Instruction Set</span><span class="sxs-lookup"><span data-stu-id="f3f21-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="f3f21-160">Property Statement</span><span class="sxs-lookup"><span data-stu-id="f3f21-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="f3f21-161">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="f3f21-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="f3f21-162">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="f3f21-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="f3f21-163">Procédure pas à pas : définition de classes</span><span class="sxs-lookup"><span data-stu-id="f3f21-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
