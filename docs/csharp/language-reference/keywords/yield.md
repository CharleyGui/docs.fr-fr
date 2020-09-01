---
description: yield, mot clé contextuel - Référence C#
title: yield, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c8caf7e34397faf9f7085d6634287cffcb37eb08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141879"
---
# <a name="yield-c-reference"></a><span data-ttu-id="d14dc-103">yield (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="d14dc-103">yield (C# Reference)</span></span>

<span data-ttu-id="d14dc-104">Lorsque vous utilisez le `yield` [mot clé contextuel](index.md#contextual-keywords) dans une instruction, vous indiquez que la méthode, l'opérateur ou l'accesseur `get` dans lequel il apparaît est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="d14dc-104">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="d14dc-105">L'utilisation de `yield` pour définir un itérateur rend une classe explicite supplémentaire inutile (la classe qui contient l'état d'une énumération ; pour obtenir un exemple, consultez <xref:System.Collections.Generic.IEnumerator%601>) lorsque vous implémentez les modèles <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour un type de collection personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d14dc-105">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="d14dc-106">L'exemple suivant montre les deux formulaires de l'instruction `yield`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-106">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="d14dc-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d14dc-107">Remarks</span></span>

<span data-ttu-id="d14dc-108">Utilisez une instruction `yield return` pour retourner chaque élément un par un.</span><span class="sxs-lookup"><span data-stu-id="d14dc-108">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="d14dc-109">La séquence retournée par une méthode d’itérateur peut être consommée à l’aide d’une instruction [foreach](foreach-in.md) ou d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="d14dc-109">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="d14dc-110">Chaque itération de la boucle `foreach` appelle la méthode Iterator.</span><span class="sxs-lookup"><span data-stu-id="d14dc-110">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="d14dc-111">Lorsqu'une instruction `yield return` est atteinte dans la méthode Iterator, `expression` est retourné, et l'emplacement dans le code est conservé.</span><span class="sxs-lookup"><span data-stu-id="d14dc-111">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="d14dc-112">L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.</span><span class="sxs-lookup"><span data-stu-id="d14dc-112">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="d14dc-113">Utilisez une instruction `yield break` pour terminer l'itération.</span><span class="sxs-lookup"><span data-stu-id="d14dc-113">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="d14dc-114">Pour plus d’informations sur les itérateurs, consultez [Itérateurs](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="d14dc-114">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="d14dc-115">Méthodes Iterator et accesseurs get</span><span class="sxs-lookup"><span data-stu-id="d14dc-115">Iterator methods and get accessors</span></span>

<span data-ttu-id="d14dc-116">La déclaration d’un itérateur doit respecter les exigences suivantes :</span><span class="sxs-lookup"><span data-stu-id="d14dc-116">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="d14dc-117">Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="d14dc-117">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="d14dc-118">La déclaration ne peut avoir aucun paramètre [in, ](in-parameter-modifier.md) [ref](ref.md) ou [out](out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="d14dc-118">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="d14dc-119">Le type `yield` d'un itérateur qui retourne <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> est `object`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-119">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="d14dc-120">Si l'itérateur retourne <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, il doit exister une conversion implicite du type de l'expression dans l'instruction `yield return` au paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="d14dc-120">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="d14dc-121">Vous ne pouvez pas inclure une instruction `yield return` ou `yield break` dans :</span><span class="sxs-lookup"><span data-stu-id="d14dc-121">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="d14dc-122">[Expressions lambda](../operators/lambda-expressions.md) et [méthodes anonymes](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d14dc-122">[Lambda expressions](../operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="d14dc-123">Méthodes qui contiennent des blocs unsafe.</span><span class="sxs-lookup"><span data-stu-id="d14dc-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="d14dc-124">Pour plus d’informations, consultez [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="d14dc-124">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="d14dc-125">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="d14dc-125">Exception handling</span></span>

<span data-ttu-id="d14dc-126">Il ne peut pas y avoir d'instruction `yield return` dans un bloc try-catch.</span><span class="sxs-lookup"><span data-stu-id="d14dc-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="d14dc-127">Une instruction `yield return` peut se trouver dans le bloc try d'une instruction try-finally.</span><span class="sxs-lookup"><span data-stu-id="d14dc-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="d14dc-128">Une instruction `yield break` peut se trouver dans un bloc try ou un bloc catch mais pas dans un bloc finally.</span><span class="sxs-lookup"><span data-stu-id="d14dc-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="d14dc-129">Si le corps `foreach` (en dehors de la méthode Iterator) lève une exception, un bloc `finally` de la méthode Iterator est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d14dc-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="d14dc-130">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="d14dc-130">Technical implementation</span></span>

<span data-ttu-id="d14dc-131">Le code suivant retourne `IEnumerable<string>` depuis une méthode Iterator, puis itère au sein de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="d14dc-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="d14dc-132">L'appel à `MyIteratorMethod` n'exécute pas le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d14dc-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="d14dc-133">À la place, l'appel retourne `IEnumerable<string>` dans la variable `elements`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="d14dc-134">Dans une itération de la boucle `foreach`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="d14dc-135">Cet appel exécute le corps de `MyIteratorMethod` jusqu'à ce que l'instruction `yield return` suivante soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="d14dc-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="d14dc-136">L’expression retournée par l’instruction `yield return` détermine non seulement la valeur de la variable `element` pour la consommation par le corps de boucle, mais également la propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de `elements`, qui est `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="d14dc-137">À chaque itération suivante de la boucle `foreach`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="d14dc-138">La boucle `foreach` se termine lorsque à la fin de la méthode Iterator ou lorsqu'une instruction `yield break` est atteinte.</span><span class="sxs-lookup"><span data-stu-id="d14dc-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="d14dc-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="d14dc-139">Example</span></span>

<span data-ttu-id="d14dc-140">L'exemple suivant comprend une instruction `yield return` située dans une boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="d14dc-141">Chaque itération du corps d’instruction `foreach` dans la méthode `Main` crée un appel à la fonction d’itérateur `Power`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="d14dc-142">Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `yield return`, qui se produit pendant l'itération suivante de la boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="d14dc-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="d14dc-143">Le type de retour de la méthode Iterator est <xref:System.Collections.IEnumerable>, qui est un type interface itérateur.</span><span class="sxs-lookup"><span data-stu-id="d14dc-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="d14dc-144">Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.</span><span class="sxs-lookup"><span data-stu-id="d14dc-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="d14dc-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="d14dc-145">Example</span></span>

<span data-ttu-id="d14dc-146">L'exemple suivant illustre un accesseur `get` qui est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="d14dc-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="d14dc-147">Dans cet exemple, chaque instruction `yield return` retourne une instance d'une classe définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d14dc-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="d14dc-148">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d14dc-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d14dc-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d14dc-149">See also</span></span>

- [<span data-ttu-id="d14dc-150">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d14dc-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d14dc-151">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d14dc-151">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d14dc-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="d14dc-152">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="d14dc-153">Iterators</span><span class="sxs-lookup"><span data-stu-id="d14dc-153">Iterators</span></span>](../../iterators.md)
