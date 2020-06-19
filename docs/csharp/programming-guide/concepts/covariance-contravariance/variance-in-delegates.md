---
title: Variance dans les délégués (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 7370813179040f54e65adf3b568a1fd914223f1d
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990035"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="bfd9a-102">Variance dans les délégués (C#)</span><span class="sxs-lookup"><span data-stu-id="bfd9a-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="bfd9a-103">.NET Framework 3.5 a introduit la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués pour tous les délégués dans C#.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="bfd9a-104">Cela signifie que vous pouvez assigner aux délégués non seulement les méthodes ayant des signatures correspondantes, mais également des méthodes qui retournent des types plus dérivés (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="bfd9a-105">Cela inclut à la fois des délégués génériques et non génériques.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="bfd9a-106">Par exemple, considérez le code suivant, qui a deux classes et deux délégués : génériques et non génériques.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="bfd9a-107">Quand vous créez des délégués des types `SampleDelegate` ou `SampleGenericDelegate<A, R>`, vous pouvez assigner l’une des méthodes suivantes à ces délégués.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="bfd9a-108">L’exemple de code suivant illustre la conversion implicite entre la signature de méthode et le type délégué.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="bfd9a-109">Pour obtenir d’autres exemples, consultez [Utilisation de la variance dans les délégués (C#)](./using-variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="bfd9a-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="bfd9a-110">Variance dans les paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="bfd9a-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="bfd9a-111">Dans .NET Framework 4 ou version ultérieure, vous pouvez activer la conversion implicite entre les délégués afin que les délégués génériques ayant des types différents spécifiés par les paramètres de type générique puissent être assignés les uns aux autres, si les types sont hérités les uns des autres comme requis par la variance.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="bfd9a-112">Pour activer la conversion implicite, vous devez déclarer explicitement les paramètres génériques dans un délégué comme covariant ou contravariant à l’aide du mot clé `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="bfd9a-113">L’exemple de code suivant indique comment vous pouvez créer un délégué ayant un paramètre de type générique covariant.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 <span data-ttu-id="bfd9a-114">Si vous utilisez uniquement la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués et que vous n’utilisez pas les mots clés `in` et `out`, vous pouvez réaliser qu’il est parfois possible d’instancier des délégués avec des expressions ou méthodes lambda identiques, mais que vous ne pouvez pas assigner un délégué à un autre.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="bfd9a-115">Dans l’exemple de code suivant, `SampleGenericDelegate<String>` ne peut pas être converti explicitement en `SampleGenericDelegate<Object>`, même si `String` hérite de `Object`.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="bfd9a-116">Vous pouvez résoudre ce problème en marquant le paramètre générique `T` avec le mot clé `out`.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a><span data-ttu-id="bfd9a-117">Délégués génériques qui ont des paramètres de type Variant dans .NET</span><span class="sxs-lookup"><span data-stu-id="bfd9a-117">Generic Delegates That Have Variant Type Parameters in .NET</span></span>

<span data-ttu-id="bfd9a-118">.NET Framework 4 a introduit la prise en charge de la variance pour les paramètres de type générique dans plusieurs délégués génériques existants :</span><span class="sxs-lookup"><span data-stu-id="bfd9a-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="bfd9a-119">Les délégués `Action` de l’espace de noms <xref:System>, par exemple, <xref:System.Action%601> et <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="bfd9a-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="bfd9a-120">Les délégués `Func` de l’espace de noms <xref:System>, par exemple, <xref:System.Func%601> et <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="bfd9a-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="bfd9a-121">Le délégué <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="bfd9a-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="bfd9a-122">Le délégué <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="bfd9a-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="bfd9a-123">Le délégué <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="bfd9a-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="bfd9a-124">Pour obtenir plus d’informations et d’exemples, consultez [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="bfd9a-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="bfd9a-125">Déclaration de paramètres de type variant dans les délégués génériques</span><span class="sxs-lookup"><span data-stu-id="bfd9a-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="bfd9a-126">Si un délégué générique possède des paramètres de type générique covariant ou contravariant, il peut être désigné sous le nom de *délégué générique variant*.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="bfd9a-127">Vous pouvez déclarer un paramètre de type générique covariant dans un délégué générique à l’aide du mot clé `out`.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="bfd9a-128">Le type covariant peut être utilisé uniquement comme type de retour de méthode et non comme type d’arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="bfd9a-129">L’exemple de code suivant indique comment déclarer un délégué générique covariant.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="bfd9a-130">Vous pouvez déclarer un paramètre de type générique contravariant dans un délégué générique à l’aide du mot clé `in`.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="bfd9a-131">Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme type de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="bfd9a-132">L’exemple de code suivant indique comment déclarer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="bfd9a-133">Les paramètres `ref`, `in` et `out` en C# ne peuvent pas être marqués comme étant variants.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="bfd9a-134">Il est également possible de prendre en charge à la fois la variance et la covariance dans le même délégué, mais pour des paramètres de type différents.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="bfd9a-135">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="bfd9a-136">Instanciation et appel de délégués génériques variants</span><span class="sxs-lookup"><span data-stu-id="bfd9a-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="bfd9a-137">Vous pouvez instancier et appeler des délégués variants de la même façon que vous instanciez et appelez des délégués invariants.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="bfd9a-138">Dans l’exemple suivant, le délégué est instancié par une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="bfd9a-139">Combinaison des délégués génériques variants</span><span class="sxs-lookup"><span data-stu-id="bfd9a-139">Combining Variant Generic Delegates</span></span>  

<span data-ttu-id="bfd9a-140">Ne combinez pas les délégués variants.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-140">Don't combine variant delegates.</span></span> <span data-ttu-id="bfd9a-141">La méthode <xref:System.Delegate.Combine%2A> ne prend pas en charge la conversion des délégués variants et nécessite le même type pour tous les délégués.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="bfd9a-142">Il peut s’ensuivre une exception runtime quand vous combinez les délégués à l’aide de la méthode <xref:System.Delegate.Combine%2A> ou de l’opérateur `+`, comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="bfd9a-143">Variance dans les paramètres de type générique pour les types valeur et référence</span><span class="sxs-lookup"><span data-stu-id="bfd9a-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="bfd9a-144">La variance pour les paramètres de type générique est prise en charge uniquement pour les types référence.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="bfd9a-145">Par exemple, `DVariant<int>` ne peut pas être converti implicitement en `DVariant<Object>` ni `DVariant<long>` parce que l’entier est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="bfd9a-146">L’exemple suivant montre que la variance dans les paramètres de type générique n’est pas prise en charge pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="bfd9a-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfd9a-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfd9a-147">See also</span></span>

- [<span data-ttu-id="bfd9a-148">Génériques</span><span class="sxs-lookup"><span data-stu-id="bfd9a-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="bfd9a-149">Utilisation de la variance pour les délégués génériques Func et Action (C#)</span><span class="sxs-lookup"><span data-stu-id="bfd9a-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="bfd9a-150">Comment combiner des délégués (délégués multicast)</span><span class="sxs-lookup"><span data-stu-id="bfd9a-150">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
