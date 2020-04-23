---
title: ref, mot clé - Référence C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 07e1b49605c83908f7b9af25e0cb2599a97257c5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102071"
---
# <a name="ref-c-reference"></a><span data-ttu-id="81c1c-102">ref (référence C#)</span><span class="sxs-lookup"><span data-stu-id="81c1c-102">ref (C# Reference)</span></span>

<span data-ttu-id="81c1c-103">Le mot clé `ref` indique une valeur qui est passée par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="81c1c-104">Il est utilisé dans quatre contextes différents :</span><span class="sxs-lookup"><span data-stu-id="81c1c-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="81c1c-105">Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="81c1c-106">Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="81c1c-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="81c1c-107">Dans une signature de méthode, pour retourner une valeur à l’appelant par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="81c1c-108">Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="81c1c-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="81c1c-109">Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier, ou une variable locale accède généralement à une valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="81c1c-110">Pour plus d’informations, consultez [Variables locales ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="81c1c-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="81c1c-111">Dans une déclaration de `struct` pour déclarer un `ref struct` ou un `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="81c1c-112">Pour plus d’informations, consultez la [ `ref` ](../builtin-types/struct.md#ref-struct) section struct de l’article des types [structure.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="81c1c-112">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="81c1c-113">Passage d’un argument par référence</span><span class="sxs-lookup"><span data-stu-id="81c1c-113">Passing an argument by reference</span></span>

<span data-ttu-id="81c1c-114">Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur.</span><span class="sxs-lookup"><span data-stu-id="81c1c-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="81c1c-115">Le mot clé `ref` fait du paramètre formel un alias de l’argument, qui doit être une variable.</span><span class="sxs-lookup"><span data-stu-id="81c1c-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="81c1c-116">En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="81c1c-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="81c1c-117">Par exemple, si l’appelant passe une expression variable locale ou une expression d’accès à l’élément de tableau, et que la méthode appelée remplace l’objet auquel le paramètre de réf se réfère, alors la variable locale de l’appelant ou l’élément de tableau se réfère maintenant au nouvel objet lorsque la méthode revient.</span><span class="sxs-lookup"><span data-stu-id="81c1c-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="81c1c-118">Ne confondez pas le concept de passage par référence avec celui de types de référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="81c1c-119">Les deux concepts ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="81c1c-119">The two concepts are not the same.</span></span> <span data-ttu-id="81c1c-120">Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="81c1c-121">Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="81c1c-122">Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="81c1c-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="81c1c-123">Un argument passé à un paramètre `ref` ou `in` doit être initialisé avant d’être transmis.</span><span class="sxs-lookup"><span data-stu-id="81c1c-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="81c1c-124">Cette obligation diffère des paramètres [out](out-parameter-modifier.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.</span><span class="sxs-lookup"><span data-stu-id="81c1c-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="81c1c-125">Les membres d’une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref`, `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="81c1c-126">Une erreur de compilation se produit si la seule différence entre deux membres d’un type est que l’un d’eux a un paramètre `ref` et que l’autre un a un paramètre `out` ou `in`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="81c1c-127">Le code suivant, par exemple, ne se compile pas.</span><span class="sxs-lookup"><span data-stu-id="81c1c-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="81c1c-128">Toutefois, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref`, `in` ou `out` et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="81c1c-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="81c1c-129">Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `in`, `ref` et `out` font partie de la signature et ne correspondent pas l’un à l’autre.</span><span class="sxs-lookup"><span data-stu-id="81c1c-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="81c1c-130">Les propriétés ne sont pas des variables.</span><span class="sxs-lookup"><span data-stu-id="81c1c-130">Properties are not variables.</span></span> <span data-ttu-id="81c1c-131">Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="81c1c-132">Vous ne pouvez pas utiliser les mots clés `ref`, `in` ou `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="81c1c-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="81c1c-133">Méthodes async, que vous définissez à l’aide du modificateur [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="81c1c-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="81c1c-134">Les méthodes Iterator, qui incluent une instruction [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="81c1c-135">En outre, les [méthodes d’extension](../../programming-guide/classes-and-structs/extension-methods.md) ont les restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="81c1c-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="81c1c-136">Le `out` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="81c1c-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="81c1c-137">Le `ref` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension lorsque l’argument n’est pas une struction, ou un type générique non contraint d’être une struction.</span><span class="sxs-lookup"><span data-stu-id="81c1c-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="81c1c-138">Le `in` mot clé ne peut pas être utilisé à moins que le premier argument soit une struction.</span><span class="sxs-lookup"><span data-stu-id="81c1c-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="81c1c-139">Le `in` mot clé ne peut pas être utilisé sur n’importe quel type générique, même lorsqu’il est contraint d’être une struction.</span><span class="sxs-lookup"><span data-stu-id="81c1c-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="81c1c-140">Passage d’un argument par référence : exemple</span><span class="sxs-lookup"><span data-stu-id="81c1c-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="81c1c-141">Les exemples précédents passent les types valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="81c1c-142">Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="81c1c-143">Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="81c1c-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="81c1c-144">L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="81c1c-145">Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant.</span><span class="sxs-lookup"><span data-stu-id="81c1c-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="81c1c-146">L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="81c1c-147">Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="81c1c-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="81c1c-148">Valeurs de retour de référence</span><span class="sxs-lookup"><span data-stu-id="81c1c-148">Reference return values</span></span>

<span data-ttu-id="81c1c-149">Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="81c1c-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="81c1c-150">Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et que le changement se reflète dans l’état de l’objet dans la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="81c1c-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="81c1c-151">Une valeur de retour de référence est définie à l’aide du mot clé `ref` :</span><span class="sxs-lookup"><span data-stu-id="81c1c-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="81c1c-152">Dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="81c1c-152">In the method signature.</span></span> <span data-ttu-id="81c1c-153">Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="81c1c-154">Entre le jeton `return` et la variable retournée dans une instruction `return` dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="81c1c-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="81c1c-155">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="81c1c-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="81c1c-156">Pour que l’appelant puisse modifier l’état de l’objet, la valeur de retour de référence doit être stockée dans une variable qui est explicitement définie comme [variable locale ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="81c1c-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="81c1c-157">Voici un exemple de retour ref plus complet, montrant à la fois la signature de la méthode et le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="81c1c-157">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="81c1c-158">La méthode appelée peut également déclarer la valeur renvoyée en tant que `ref readonly` pour renvoyer la valeur par référence et faire en sorte que le code d'appel ne puisse pas modifier la valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="81c1c-158">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="81c1c-159">La méthode d’appel peut éviter de copier la valeur renvoyée en stockant la valeur dans une variable [ref readonly](#ref-readonly-locals) locale.</span><span class="sxs-lookup"><span data-stu-id="81c1c-159">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="81c1c-160">Par exemple, voir [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="81c1c-160">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="81c1c-161">Variables locales ref</span><span class="sxs-lookup"><span data-stu-id="81c1c-161">Ref locals</span></span>

<span data-ttu-id="81c1c-162">Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `return ref`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-162">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="81c1c-163">Vous ne pouvez pas initialiser une variable locale ref en valeur de retour non ref.</span><span class="sxs-lookup"><span data-stu-id="81c1c-163">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="81c1c-164">En d’autres termes, le côté droit de l’initialisation doit être une référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-164">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="81c1c-165">Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-165">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="81c1c-166">Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="81c1c-166">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="81c1c-167">Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="81c1c-167">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="81c1c-168">Vous pouvez accéder à une valeur par référence de la même façon.</span><span class="sxs-lookup"><span data-stu-id="81c1c-168">You can access a value by reference in the same way.</span></span> <span data-ttu-id="81c1c-169">Dans certains cas, l’accès à une valeur par référence augmente les performances en évitant une opération de copie potentiellement coûteuse.</span><span class="sxs-lookup"><span data-stu-id="81c1c-169">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="81c1c-170">Par exemple, l’instruction suivante montre comment il est possible de définir une valeur locale ref qui est utilisée pour référencer une valeur.</span><span class="sxs-lookup"><span data-stu-id="81c1c-170">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="81c1c-171">Dans les `ref` deux exemples, le mot clé doit être utilisé dans les deux endroits, ou le compilateur génère l’erreur CS8172, "Ne peut pas initialiser une variable de référence avec une valeur."</span><span class="sxs-lookup"><span data-stu-id="81c1c-171">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="81c1c-172">À partir de C# 7.3, la variable d’itération de l’instruction `foreach` peut être une variable locale ref ou une variable locale ref readonly.</span><span class="sxs-lookup"><span data-stu-id="81c1c-172">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="81c1c-173">Pour plus d’informations, voir l’article [Instruction foreach](foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="81c1c-173">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="81c1c-174">En commençant également par C 7.3, vous pouvez réaffecter une variable locale ou réactive avec [l’opérateur d’affectation d’arbitres.](../operators/assignment-operator.md#ref-assignment-operator)</span><span class="sxs-lookup"><span data-stu-id="81c1c-174">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="81c1c-175">Variable locale ref readonly</span><span class="sxs-lookup"><span data-stu-id="81c1c-175">Ref readonly locals</span></span>

<span data-ttu-id="81c1c-176">Une variable locale ref readonly est utilisée pour se référer à des valeurs renvoyées par la méthode ou par la propriété comprenant `ref readonly` dans sa signature et utilise `return ref`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-176">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="81c1c-177">Une variable `ref readonly` combine les propriétés d’une variable locale `ref` avec une variable `readonly` : c’est un alias du stockage auquel elle est assignée et qui ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="81c1c-177">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="81c1c-178">Exemple de retours ref et de variables locales ref</span><span class="sxs-lookup"><span data-stu-id="81c1c-178">A ref returns and ref locals example</span></span>

<span data-ttu-id="81c1c-179">L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-179">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="81c1c-180">Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-180">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="81c1c-181">Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="81c1c-181">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="81c1c-182">Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="81c1c-182">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="81c1c-183">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="81c1c-183">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81c1c-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81c1c-184">See also</span></span>

- [<span data-ttu-id="81c1c-185">Rédiger un code efficace en toute sécurité</span><span class="sxs-lookup"><span data-stu-id="81c1c-185">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="81c1c-186">Retours ref et variables locales ref</span><span class="sxs-lookup"><span data-stu-id="81c1c-186">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="81c1c-187">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="81c1c-187">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="81c1c-188">Paramètres de passage</span><span class="sxs-lookup"><span data-stu-id="81c1c-188">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="81c1c-189">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="81c1c-189">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="81c1c-190">Référence C</span><span class="sxs-lookup"><span data-stu-id="81c1c-190">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81c1c-191">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="81c1c-191">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81c1c-192">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="81c1c-192">C# Keywords</span></span>](index.md)
