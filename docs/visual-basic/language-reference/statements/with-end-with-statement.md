---
title: With...End With, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 3d26932c23299c6fbcb53b1389abd7694f529eef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963330"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="cb5d1-102">With...End With, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb5d1-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="cb5d1-103">Exécute une série d'instructions qui font référence à plusieurs reprises à un objet ou une structure unique afin que ces instructions puissent utiliser une syntaxe simplifiée lors de l'accès aux membres de l'objet ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="cb5d1-104">Lorsque vous utilisez une structure, vous ne pouvez lire que les valeurs des membres ou des méthodes invoke. En outre, vous obtenez une erreur si vous tentez d'assigner des valeurs aux membres d'une structure utilisée dans une instruction `With...End With`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5d1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb5d1-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="cb5d1-106">Composants</span><span class="sxs-lookup"><span data-stu-id="cb5d1-106">Parts</span></span>  
  
|<span data-ttu-id="cb5d1-107">Terme</span><span class="sxs-lookup"><span data-stu-id="cb5d1-107">Term</span></span>|<span data-ttu-id="cb5d1-108">Définition</span><span class="sxs-lookup"><span data-stu-id="cb5d1-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="cb5d1-109">Requis.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-109">Required.</span></span> <span data-ttu-id="cb5d1-110">Expression qui correspond à un objet.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="cb5d1-111">L'expression peut être arbitrairement complexe et n'est évaluée qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="cb5d1-112">L'expression peut correspondre à tout type de données, y compris des types élémentaires.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="cb5d1-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-113">Optional.</span></span> <span data-ttu-id="cb5d1-114">Une ou plusieurs instructions entre `With` et `End With` qui peuvent faire référence aux membres d'un objet produit par l'évaluation de `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="cb5d1-115">Requis.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-115">Required.</span></span> <span data-ttu-id="cb5d1-116">Met fin à la définition du bloc `With`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb5d1-117">Notes</span><span class="sxs-lookup"><span data-stu-id="cb5d1-117">Remarks</span></span>  
 <span data-ttu-id="cb5d1-118">À l'aide de `With...End With`, vous pouvez exécuter une série d'instructions sur un objet spécifique sans avoir à spécifier plusieurs fois le nom de cet objet.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="cb5d1-119">Dans un bloc d'instructions `With`, vous pouvez spécifier un membre de l'objet en commençant par un point, comme si l'instruction `With` le précédait.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="cb5d1-120">Par exemple, pour modifier plusieurs propriétés d'un seul objet, placez les instructions d'assignation de propriétés dans le bloc `With...End With`. Vous ne faites ainsi référence qu'une seule fois à l'objet, au lieu de le faire à chaque assignation de propriété.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="cb5d1-121">Si votre code accède au même objet dans plusieurs instructions, vous bénéficiez des avantages suivants via l'instruction `With` :</span><span class="sxs-lookup"><span data-stu-id="cb5d1-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
- <span data-ttu-id="cb5d1-122">Vous n'avez pas besoin d'évaluer une expression complexe plusieurs fois, ni d'assigner le résultat à une variable temporaire pour faire référence à ses membres à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
- <span data-ttu-id="cb5d1-123">Vous rendez votre code plus lisible en éliminant les expressions qualifiantes répétitives.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="cb5d1-124">Le type de données de `objectExpression` peut être un type de classe ou de structure, ou même un type élémentaire Visual Basic, tel que `Integer`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="cb5d1-125">Si `objectExpression` est autre chose qu'un objet, vous ne pouvez lire que les valeurs de ses membres ou de ses méthodes invoke. En outre, vous obtenez une erreur si vous tentez d'assigner des valeurs aux membres d'une structure utilisée dans une instruction `With...End With`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="cb5d1-126">Il s'agit de la même erreur que celle que vous obtenez si vous appelez une méthode qui a retourné une structure et qui a immédiatement accédé à une valeur pour l'assigner à un membre du résultat de la fonction, par exemple `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="cb5d1-127">Dans les deux cas, le problème vient du fait que la structure existe uniquement dans la pile des appels. Par ailleurs, il n'existe aucun moyen dans ce cas pour qu'un membre de structure modifié puisse écrire dans un emplacement de manière à ce qu'une autre partie du code du programme puisse observer la modification.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="cb5d1-128">`objectExpression` est évalué une seule fois, à l'entrée dans le bloc.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="cb5d1-129">Vous ne pouvez pas réassigner `objectExpression` à partir de l'intérieur du bloc `With`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="cb5d1-130">Dans un bloc `With`, vous pouvez accéder aux méthodes et propriétés de l'objet spécifié uniquement sans les qualifier.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="cb5d1-131">Vous pouvez utiliser les méthodes et propriétés des autres objets, mais vous devez les qualifier par leurs noms d'objets.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="cb5d1-132">Vous pouvez placer une instruction `With...End With` dans une autre.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="cb5d1-133">Les instructions `With...End With` imbriquées peuvent prêter à confusion si les objets référencés ne sont pas clairs d'après le contexte.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="cb5d1-134">Vous devez fournir une référence qualifiée complète à un objet qui se trouve dans un bloc `With` externe lorsque l'objet est référencé à partir de l'intérieur d'un bloc `With`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="cb5d1-135">Vous ne pouvez pas créer de branche dans un bloc d’instructions `With` à partir de l’extérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="cb5d1-136">À moins que le bloc ne contienne une boucle, les instructions ne sont exécutées qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="cb5d1-137">Vous pouvez imbriquer différentes sortes de structures de contrôle.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="cb5d1-138">Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="cb5d1-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb5d1-139">Vous pouvez également utiliser le mot clé `With` dans les initialiseurs d'objets.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="cb5d1-140">Pour plus d’informations et d’exemples [, consultez Initialiseurs d’objets: Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) nommés et anonymes et [types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="cb5d1-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="cb5d1-141">Si vous utilisez un bloc `With` uniquement pour initialiser les propriétés ou les champs d'un objet que vous venez d'instancier, utilisez plutôt un initialiseur d'objet à la place.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb5d1-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb5d1-142">Example</span></span>  
 <span data-ttu-id="cb5d1-143">Dans l'exemple suivant, chaque bloc `With` exécute une série d'instructions sur un seul objet.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="cb5d1-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb5d1-144">Example</span></span>  
 <span data-ttu-id="cb5d1-145">L'exemple suivant imbrique les instructions `With…End With`.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="cb5d1-146">Dans l'instruction `With` imbriquée, la syntaxe fait référence à l'objet interne.</span><span class="sxs-lookup"><span data-stu-id="cb5d1-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cb5d1-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb5d1-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="cb5d1-148">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="cb5d1-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="cb5d1-149">Initialiseurs d’objets: Types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="cb5d1-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="cb5d1-150">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="cb5d1-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
