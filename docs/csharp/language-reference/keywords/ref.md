---
description: ref, mot clé - Référence C#
title: ref, mot clé - Référence C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: d2855738c723ba6d2437257793f18349b18629dc
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877585"
---
# <a name="ref-c-reference"></a><span data-ttu-id="7cb5b-103">ref (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7cb5b-103">ref (C# Reference)</span></span>

<span data-ttu-id="7cb5b-104">Le mot clé `ref` indique une valeur qui est passée par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-104">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="7cb5b-105">Il est utilisé dans quatre contextes différents :</span><span class="sxs-lookup"><span data-stu-id="7cb5b-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="7cb5b-106">Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="7cb5b-107">Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="7cb5b-108">Dans une signature de méthode, pour retourner une valeur à l’appelant par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="7cb5b-109">Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="7cb5b-110">Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier, ou une variable locale accède généralement à une valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="7cb5b-111">Pour plus d’informations, consultez [Variables locales ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-111">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="7cb5b-112">Dans une déclaration de `struct` pour déclarer un `ref struct` ou un `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-112">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="7cb5b-113">Pour plus d’informations, consultez la section [ `ref` struct](../builtin-types/struct.md#ref-struct) de l’article [types de structures](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="7cb5b-113">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="7cb5b-114">Passage d’un argument par référence</span><span class="sxs-lookup"><span data-stu-id="7cb5b-114">Passing an argument by reference</span></span>

<span data-ttu-id="7cb5b-115">Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-115">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="7cb5b-116">Le mot clé `ref` fait du paramètre formel un alias de l’argument, qui doit être une variable.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-116">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="7cb5b-117">En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-117">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="7cb5b-118">Par exemple, si l’appelant passe une expression de variable locale ou une expression d’accès à un élément de tableau, et que la méthode appelée remplace l’objet auquel fait référence le paramètre ref, la variable locale de l’appelant ou l’élément de tableau fait désormais référence au nouvel objet lorsque la méthode est retournée.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-118">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="7cb5b-119">Ne confondez pas le concept de passage par référence avec celui de types de référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-119">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="7cb5b-120">Les deux concepts ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-120">The two concepts are not the same.</span></span> <span data-ttu-id="7cb5b-121">Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-121">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="7cb5b-122">Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-122">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="7cb5b-123">Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-123">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="7cb5b-124">Un argument passé à un paramètre `ref` ou `in` doit être initialisé avant d’être transmis.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-124">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="7cb5b-125">Cette obligation diffère des paramètres [out](out-parameter-modifier.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-125">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="7cb5b-126">Les membres d’une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref`, `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-126">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="7cb5b-127">Une erreur de compilation se produit si la seule différence entre deux membres d’un type est que l’un d’eux a un paramètre `ref` et que l’autre un a un paramètre `out` ou `in`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-127">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="7cb5b-128">Le code suivant, par exemple, ne se compile pas.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-128">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="7cb5b-129">Toutefois, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref`, `in` ou `out` et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-129">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="7cb5b-130">Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `in`, `ref` et `out` font partie de la signature et ne correspondent pas l’un à l’autre.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-130">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="7cb5b-131">Les propriétés ne sont pas des variables.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-131">Properties are not variables.</span></span> <span data-ttu-id="7cb5b-132">Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-132">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="7cb5b-133">Vous ne pouvez pas utiliser les mots clés `ref`, `in` ou `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="7cb5b-133">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="7cb5b-134">Méthodes async, que vous définissez à l’aide du modificateur [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-134">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="7cb5b-135">Les méthodes Iterator, qui incluent une instruction [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-135">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="7cb5b-136">En outre, les [méthodes d’extension](../../programming-guide/classes-and-structs/extension-methods.md) présentent les restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="7cb5b-136">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="7cb5b-137">Le `out` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-137">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="7cb5b-138">Le `ref` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension lorsque l’argument n’est pas un struct, ou un type générique qui n’est pas imposé comme struct.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-138">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="7cb5b-139">Le `in` mot clé ne peut pas être utilisé, sauf si le premier argument est un struct.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-139">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="7cb5b-140">Le `in` mot clé ne peut pas être utilisé sur un type générique, même lorsqu’il est imposé comme struct.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-140">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="7cb5b-141">Passage d’un argument par référence : exemple</span><span class="sxs-lookup"><span data-stu-id="7cb5b-141">Passing an argument by reference: An example</span></span>

<span data-ttu-id="7cb5b-142">Les exemples précédents passent les types valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-142">The previous examples pass value types by reference.</span></span> <span data-ttu-id="7cb5b-143">Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-143">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="7cb5b-144">Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-144">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="7cb5b-145">L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-145">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="7cb5b-146">Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-146">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="7cb5b-147">L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-147">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="7cb5b-148">Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-148">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="7cb5b-149">Valeurs de retour de référence</span><span class="sxs-lookup"><span data-stu-id="7cb5b-149">Reference return values</span></span>

<span data-ttu-id="7cb5b-150">Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-150">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="7cb5b-151">Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et cette modification est reflétée dans l’état de l’objet dans la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-151">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="7cb5b-152">Une valeur de retour de référence est définie à l’aide du mot clé `ref` :</span><span class="sxs-lookup"><span data-stu-id="7cb5b-152">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="7cb5b-153">Dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-153">In the method signature.</span></span> <span data-ttu-id="7cb5b-154">Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-154">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="7cb5b-155">Entre le jeton `return` et la variable retournée dans une instruction `return` dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-155">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="7cb5b-156">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7cb5b-156">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="7cb5b-157">Pour que l’appelant puisse modifier l’état de l’objet, la valeur de retour de référence doit être stockée dans une variable qui est explicitement définie comme [variable locale ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-157">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="7cb5b-158">Voici un exemple plus complet de retour de référence, qui illustre la signature de la méthode et le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-158">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="7cb5b-159">La méthode appelée peut également déclarer la valeur renvoyée en tant que `ref readonly` pour renvoyer la valeur par référence et faire en sorte que le code d'appel ne puisse pas modifier la valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-159">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="7cb5b-160">La méthode d’appel peut éviter de copier la valeur retournée en stockant la valeur dans une variable de référence locale en [lecture seule](#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="7cb5b-160">The calling method can avoid copying the returned value by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="7cb5b-161">Pour obtenir un exemple, consultez [un exemple de retours REF et de variables locales Ref](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-161">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="7cb5b-162">Variables locales ref</span><span class="sxs-lookup"><span data-stu-id="7cb5b-162">Ref locals</span></span>

<span data-ttu-id="7cb5b-163">Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `return ref`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-163">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="7cb5b-164">Vous ne pouvez pas initialiser une variable locale ref en valeur de retour non ref.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-164">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="7cb5b-165">En d’autres termes, la partie droite de l’initialisation doit être une référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-165">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="7cb5b-166">Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-166">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="7cb5b-167">Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-167">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="7cb5b-168">Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="7cb5b-168">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="7cb5b-169">Vous pouvez accéder à une valeur par référence de la même façon.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-169">You can access a value by reference in the same way.</span></span> <span data-ttu-id="7cb5b-170">Dans certains cas, l’accès à une valeur par référence augmente les performances en évitant une opération de copie potentiellement coûteuse.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-170">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="7cb5b-171">Par exemple, l’instruction suivante montre comment il est possible de définir une valeur locale ref qui est utilisée pour référencer une valeur.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-171">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="7cb5b-172">Dans les deux exemples `ref` , le mot clé doit être utilisé aux deux emplacements, ou le compilateur génère l’erreur CS8172, « impossible d’initialiser une variable par référence avec une valeur ».</span><span class="sxs-lookup"><span data-stu-id="7cb5b-172">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="7cb5b-173">À partir de C# 7.3, la variable d’itération de l’instruction `foreach` peut être une variable locale ref ou une variable locale ref readonly.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-173">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="7cb5b-174">Pour plus d’informations, voir l’article [Instruction foreach](foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-174">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="7cb5b-175">À compter de C# 7,3, vous pouvez également réassigner une variable locale Ref locale ou ref ReadOnly avec l' [opérateur d’assignation de référence](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="7cb5b-175">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="7cb5b-176">Variable locale ref readonly</span><span class="sxs-lookup"><span data-stu-id="7cb5b-176">Ref readonly locals</span></span>

<span data-ttu-id="7cb5b-177">Une variable locale ref readonly est utilisée pour se référer à des valeurs renvoyées par la méthode ou par la propriété comprenant `ref readonly` dans sa signature et utilise `return ref`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-177">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="7cb5b-178">Une variable `ref readonly` combine les propriétés d’une variable locale `ref` avec une variable `readonly` : c’est un alias du stockage auquel elle est assignée et qui ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-178">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="7cb5b-179">Exemple de retours ref et de variables locales ref</span><span class="sxs-lookup"><span data-stu-id="7cb5b-179">A ref returns and ref locals example</span></span>

<span data-ttu-id="7cb5b-180">L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-180">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="7cb5b-181">Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-181">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="7cb5b-182">Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-182">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="7cb5b-183">Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7cb5b-183">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="7cb5b-184">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7cb5b-184">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7cb5b-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cb5b-185">See also</span></span>

- [<span data-ttu-id="7cb5b-186">Écrire du code efficace sécurisé</span><span class="sxs-lookup"><span data-stu-id="7cb5b-186">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="7cb5b-187">Retours ref et variables locales ref</span><span class="sxs-lookup"><span data-stu-id="7cb5b-187">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="7cb5b-188">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="7cb5b-188">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="7cb5b-189">Passer des paramètres</span><span class="sxs-lookup"><span data-stu-id="7cb5b-189">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="7cb5b-190">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="7cb5b-190">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="7cb5b-191">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7cb5b-191">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7cb5b-192">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7cb5b-192">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7cb5b-193">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="7cb5b-193">C# Keywords</span></span>](index.md)
