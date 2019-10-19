---
title: Set, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583238"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="00788-102">Set, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00788-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="00788-103">Déclare une procédure de propriété `Set` utilisée pour assigner une valeur à une propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00788-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00788-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="00788-105">Composants</span><span class="sxs-lookup"><span data-stu-id="00788-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="00788-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="00788-106">Optional.</span></span> <span data-ttu-id="00788-107">Consultez la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="00788-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="00788-108">Facultatif sur au plus une des instructions `Get` et `Set` de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="00788-109">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="00788-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="00788-110">Protected</span><span class="sxs-lookup"><span data-stu-id="00788-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="00788-111">Friend</span><span class="sxs-lookup"><span data-stu-id="00788-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="00788-112">Private</span><span class="sxs-lookup"><span data-stu-id="00788-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="00788-113">Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="00788-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="00788-114">Requis.</span><span class="sxs-lookup"><span data-stu-id="00788-114">Required.</span></span> <span data-ttu-id="00788-115">Paramètre contenant la nouvelle valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="00788-116">Obligatoire si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="00788-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="00788-117">Type de données du paramètre `value`.</span><span class="sxs-lookup"><span data-stu-id="00788-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="00788-118">Le type de données spécifié doit être le même que le type de données de la propriété où cette `Set` instruction est déclarée.</span><span class="sxs-lookup"><span data-stu-id="00788-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="00788-119">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="00788-119">Optional.</span></span> <span data-ttu-id="00788-120">Une ou plusieurs instructions qui s’exécutent lorsque la procédure de propriété `Set` est appelée.</span><span class="sxs-lookup"><span data-stu-id="00788-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="00788-121">Requis.</span><span class="sxs-lookup"><span data-stu-id="00788-121">Required.</span></span> <span data-ttu-id="00788-122">Met fin à la définition de la procédure de propriété `Set`.</span><span class="sxs-lookup"><span data-stu-id="00788-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00788-123">Notes</span><span class="sxs-lookup"><span data-stu-id="00788-123">Remarks</span></span>  
 <span data-ttu-id="00788-124">Chaque propriété doit avoir une procédure de propriété `Set`, sauf si la propriété est marquée comme `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="00788-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="00788-125">La procédure `Set` est utilisée pour définir la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="00788-126">Visual Basic appelle automatiquement la procédure `Set` d’une propriété lorsqu’une instruction d’assignation fournit une valeur à stocker dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="00788-127">Visual Basic passe un paramètre à la procédure `Set` au cours des assignations de propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="00788-128">Si vous ne fournissez pas de paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`.</span><span class="sxs-lookup"><span data-stu-id="00788-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="00788-129">Le paramètre contient la valeur à assigner à la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="00788-130">En général, cette valeur est stockée dans une variable locale privée et elle est retournée à chaque appel de la procédure `Get`.</span><span class="sxs-lookup"><span data-stu-id="00788-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="00788-131">Le corps de la déclaration de propriété peut contenir uniquement les procédures `Get` et `Set` de la propriété entre l' [instruction Property](../../../visual-basic/language-reference/statements/property-statement.md) et l’instruction `End Property`.</span><span class="sxs-lookup"><span data-stu-id="00788-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="00788-132">Elle ne peut pas stocker d’autres éléments que ces procédures.</span><span class="sxs-lookup"><span data-stu-id="00788-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="00788-133">En particulier, il ne peut pas stocker la valeur actuelle de la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="00788-134">Vous devez stocker cette valeur en dehors de la propriété, car si vous la stockez à l’intérieur de l’une des procédures de propriété, l’autre procédure de propriété ne peut pas y accéder.</span><span class="sxs-lookup"><span data-stu-id="00788-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="00788-135">L’approche habituelle consiste à stocker la valeur dans une variable [privée](../../../visual-basic/language-reference/modifiers/private.md) déclarée au même niveau que la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="00788-136">Vous devez définir une procédure `Set` à l’intérieur de la propriété à laquelle elle s’applique.</span><span class="sxs-lookup"><span data-stu-id="00788-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="00788-137">La procédure `Set` a comme valeur par défaut le niveau d’accès de sa propriété conteneur, sauf si vous utilisez `accessmodifier` dans l’instruction `Set`.</span><span class="sxs-lookup"><span data-stu-id="00788-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="00788-138">Règles</span><span class="sxs-lookup"><span data-stu-id="00788-138">Rules</span></span>  
  
- <span data-ttu-id="00788-139">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="00788-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="00788-140">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` ou la procédure `Set`, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="00788-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="00788-141">Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="00788-142">Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Set` `Private`, mais pas `Public`.</span><span class="sxs-lookup"><span data-stu-id="00788-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="00788-143">Si vous définissez une propriété `WriteOnly`, la procédure `Set` représente la propriété entière.</span><span class="sxs-lookup"><span data-stu-id="00788-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="00788-144">Vous ne pouvez pas déclarer un niveau d’accès différent pour `Set`, car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="00788-145">Comportement</span><span class="sxs-lookup"><span data-stu-id="00788-145">Behavior</span></span>  
  
- <span data-ttu-id="00788-146">**Retour d’une procédure de propriété.**</span><span class="sxs-lookup"><span data-stu-id="00788-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="00788-147">Lorsque la procédure `Set` retourne au code appelant, l’exécution continue à suivre l’instruction qui a fourni la valeur à stocker.</span><span class="sxs-lookup"><span data-stu-id="00788-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="00788-148">les procédures de propriété `Set` peuvent être renvoyées à l’aide de l' [instruction return](../../../visual-basic/language-reference/statements/return-statement.md) ou de l' [instruction Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="00788-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="00788-149">Les instructions `Exit Property` et `Return` provoquent une sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="00788-150">Un nombre quelconque d’instructions `Exit Property` et `Return` peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Property` et `Return`.</span><span class="sxs-lookup"><span data-stu-id="00788-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00788-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="00788-151">Example</span></span>  
 <span data-ttu-id="00788-152">L’exemple suivant utilise l’instruction `Set` pour définir la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="00788-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="00788-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00788-153">See also</span></span>

- [<span data-ttu-id="00788-154">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="00788-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="00788-155">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="00788-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="00788-156">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="00788-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="00788-157">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="00788-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
