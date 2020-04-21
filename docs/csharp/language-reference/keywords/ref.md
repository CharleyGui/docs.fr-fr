---
title: ref, mot clé - Référence C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 494a46040d6cc33c5284449779fae89705fd29c2
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738822"
---
# <a name="ref-c-reference"></a><span data-ttu-id="ad359-102">ref (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ad359-102">ref (C# Reference)</span></span>

<span data-ttu-id="ad359-103">Le mot clé `ref` indique une valeur qui est passée par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="ad359-104">Il est utilisé dans quatre contextes différents :</span><span class="sxs-lookup"><span data-stu-id="ad359-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="ad359-105">Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="ad359-106">Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="ad359-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="ad359-107">Dans une signature de méthode, pour retourner une valeur à l’appelant par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="ad359-108">Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="ad359-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="ad359-109">Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier, ou une variable locale accède généralement à une valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="ad359-110">Pour plus d’informations, consultez [Variables locales ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="ad359-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="ad359-111">Dans une déclaration de `struct` pour déclarer un `ref struct` ou un `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="ad359-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="ad359-112">Pour plus d’informations, consultez la [ `ref` ](../builtin-types/struct.md#ref-struct) section struct de l’article des types [structure.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="ad359-112">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="ad359-113">Passage d’un argument par référence</span><span class="sxs-lookup"><span data-stu-id="ad359-113">Passing an argument by reference</span></span>

<span data-ttu-id="ad359-114">Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur.</span><span class="sxs-lookup"><span data-stu-id="ad359-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="ad359-115">Le mot clé `ref` fait du paramètre formel un alias de l’argument, qui doit être une variable.</span><span class="sxs-lookup"><span data-stu-id="ad359-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="ad359-116">En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="ad359-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="ad359-117">Par exemple, si l’appelant passe une expression variable locale ou une expression d’accès à l’élément de tableau, et que la méthode appelée remplace l’objet auquel le paramètre de réf se réfère, alors la variable locale de l’appelant ou l’élément de tableau se réfère maintenant au nouvel objet lorsque la méthode revient.</span><span class="sxs-lookup"><span data-stu-id="ad359-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="ad359-118">Ne confondez pas le concept de passage par référence avec celui de types de référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="ad359-119">Les deux concepts ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="ad359-119">The two concepts are not the same.</span></span> <span data-ttu-id="ad359-120">Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="ad359-121">Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="ad359-122">Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ad359-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="ad359-123">Un argument passé à un paramètre `ref` ou `in` doit être initialisé avant d’être transmis.</span><span class="sxs-lookup"><span data-stu-id="ad359-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="ad359-124">Cette obligation diffère des paramètres [out](out-parameter-modifier.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.</span><span class="sxs-lookup"><span data-stu-id="ad359-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="ad359-125">Les membres d’une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref`, `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="ad359-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="ad359-126">Une erreur de compilation se produit si la seule différence entre deux membres d’un type est que l’un d’eux a un paramètre `ref` et que l’autre un a un paramètre `out` ou `in`.</span><span class="sxs-lookup"><span data-stu-id="ad359-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="ad359-127">Le code suivant, par exemple, ne se compile pas.</span><span class="sxs-lookup"><span data-stu-id="ad359-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="ad359-128">Toutefois, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref`, `in` ou `out` et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ad359-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="ad359-129">Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `in`, `ref` et `out` font partie de la signature et ne correspondent pas l’un à l’autre.</span><span class="sxs-lookup"><span data-stu-id="ad359-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="ad359-130">Les propriétés ne sont pas des variables.</span><span class="sxs-lookup"><span data-stu-id="ad359-130">Properties are not variables.</span></span> <span data-ttu-id="ad359-131">Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.</span><span class="sxs-lookup"><span data-stu-id="ad359-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="ad359-132">Vous ne pouvez pas utiliser les mots clés `ref`, `in` ou `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="ad359-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="ad359-133">Méthodes async, que vous définissez à l’aide du modificateur [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="ad359-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="ad359-134">Les méthodes Iterator, qui incluent une instruction [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="ad359-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="ad359-135">En outre, les [méthodes d’extension](../../programming-guide/classes-and-structs/extension-methods.md) ont les restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad359-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="ad359-136">Le `out` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="ad359-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="ad359-137">Le `ref` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension lorsque l’argument n’est pas une struction, ou un type générique non contraint d’être une struction.</span><span class="sxs-lookup"><span data-stu-id="ad359-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="ad359-138">Le `in` mot clé ne peut pas être utilisé à moins que le premier argument soit une struction.</span><span class="sxs-lookup"><span data-stu-id="ad359-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="ad359-139">Le `in` mot clé ne peut pas être utilisé sur n’importe quel type générique, même lorsqu’il est contraint d’être une struction.</span><span class="sxs-lookup"><span data-stu-id="ad359-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="ad359-140">Passage d’un argument par référence : exemple</span><span class="sxs-lookup"><span data-stu-id="ad359-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="ad359-141">Les exemples précédents passent les types valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="ad359-142">Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="ad359-143">Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ad359-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="ad359-144">L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="ad359-145">Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ad359-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="ad359-146">L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="ad359-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="ad359-147">Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ad359-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="ad359-148">Valeurs de retour de référence</span><span class="sxs-lookup"><span data-stu-id="ad359-148">Reference return values</span></span>

<span data-ttu-id="ad359-149">Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ad359-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="ad359-150">Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et ce changement est reflété dans l’état de l’objet qui contient la méthode.</span><span class="sxs-lookup"><span data-stu-id="ad359-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="ad359-151">Une valeur de retour de référence est définie à l’aide du mot clé `ref` :</span><span class="sxs-lookup"><span data-stu-id="ad359-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="ad359-152">Dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ad359-152">In the method signature.</span></span> <span data-ttu-id="ad359-153">Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="ad359-154">Entre le jeton `return` et la variable retournée dans une instruction `return` dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="ad359-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="ad359-155">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ad359-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="ad359-156">Pour que l’appelant puisse modifier l’état de l’objet, la valeur de retour de référence doit être stockée dans une variable qui est explicitement définie comme [variable locale ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="ad359-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="ad359-157">La méthode appelée peut également déclarer la valeur renvoyée en tant que `ref readonly` pour renvoyer la valeur par référence et faire en sorte que le code d'appel ne puisse pas modifier la valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="ad359-157">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="ad359-158">La méthode d’appel peut éviter de copier la valeur renvoyée en stockant la valeur dans une variable [ref readonly](#ref-readonly-locals) locale.</span><span class="sxs-lookup"><span data-stu-id="ad359-158">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="ad359-159">Par exemple, voir [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="ad359-159">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="ad359-160">Variables locales ref</span><span class="sxs-lookup"><span data-stu-id="ad359-160">Ref locals</span></span>

<span data-ttu-id="ad359-161">Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `return ref`.</span><span class="sxs-lookup"><span data-stu-id="ad359-161">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="ad359-162">Vous ne pouvez pas initialiser une variable locale ref en valeur de retour non ref.</span><span class="sxs-lookup"><span data-stu-id="ad359-162">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="ad359-163">En d’autres termes, le côté droit de l’initialisation doit être une référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-163">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="ad359-164">Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-164">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="ad359-165">Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="ad359-165">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="ad359-166">Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="ad359-166">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="ad359-167">Vous pouvez accéder à une valeur par référence de la même façon.</span><span class="sxs-lookup"><span data-stu-id="ad359-167">You can access a value by reference in the same way.</span></span> <span data-ttu-id="ad359-168">Dans certains cas, l’accès à une valeur par référence augmente les performances en évitant une opération de copie potentiellement coûteuse.</span><span class="sxs-lookup"><span data-stu-id="ad359-168">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="ad359-169">Par exemple, l’instruction suivante montre comment il est possible de définir une valeur locale ref qui est utilisée pour référencer une valeur.</span><span class="sxs-lookup"><span data-stu-id="ad359-169">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="ad359-170">Dans les `ref` deux exemples, le mot clé doit être utilisé dans les deux endroits, ou le compilateur génère l’erreur CS8172, "Ne peut pas initialiser une variable de référence avec une valeur."</span><span class="sxs-lookup"><span data-stu-id="ad359-170">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="ad359-171">À partir de C# 7.3, la variable d’itération de l’instruction `foreach` peut être une variable locale ref ou une variable locale ref readonly.</span><span class="sxs-lookup"><span data-stu-id="ad359-171">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="ad359-172">Pour plus d’informations, voir l’article [Instruction foreach](foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="ad359-172">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="ad359-173">En commençant également par C 7.3, vous pouvez réaffecter une variable locale ou réactive avec [l’opérateur d’affectation d’arbitres.](../operators/assignment-operator.md#ref-assignment-operator)</span><span class="sxs-lookup"><span data-stu-id="ad359-173">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="ad359-174">Variable locale ref readonly</span><span class="sxs-lookup"><span data-stu-id="ad359-174">Ref readonly locals</span></span>

<span data-ttu-id="ad359-175">Une variable locale ref readonly est utilisée pour se référer à des valeurs renvoyées par la méthode ou par la propriété comprenant `ref readonly` dans sa signature et utilise `return ref`.</span><span class="sxs-lookup"><span data-stu-id="ad359-175">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="ad359-176">Une variable `ref readonly` combine les propriétés d’une variable locale `ref` avec une variable `readonly` : c’est un alias du stockage auquel elle est assignée et qui ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="ad359-176">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="ad359-177">Exemple de retours ref et de variables locales ref</span><span class="sxs-lookup"><span data-stu-id="ad359-177">A ref returns and ref locals example</span></span>

<span data-ttu-id="ad359-178">L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="ad359-178">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="ad359-179">Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`.</span><span class="sxs-lookup"><span data-stu-id="ad359-179">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="ad359-180">Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="ad359-180">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="ad359-181">Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ad359-181">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="ad359-182">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ad359-182">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad359-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad359-183">See also</span></span>

- [<span data-ttu-id="ad359-184">Rédiger un code efficace en toute sécurité</span><span class="sxs-lookup"><span data-stu-id="ad359-184">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="ad359-185">Retours ref et variables locales ref</span><span class="sxs-lookup"><span data-stu-id="ad359-185">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="ad359-186">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="ad359-186">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="ad359-187">Paramètres de passage</span><span class="sxs-lookup"><span data-stu-id="ad359-187">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="ad359-188">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="ad359-188">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="ad359-189">Référence C</span><span class="sxs-lookup"><span data-stu-id="ad359-189">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad359-190">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="ad359-190">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad359-191">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="ad359-191">C# Keywords</span></span>](index.md)
