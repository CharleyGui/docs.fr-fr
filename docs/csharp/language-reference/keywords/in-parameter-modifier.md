---
title: in, modificateur de paramètre - Référence C#
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: cbde7a571fb71ed7577077c77a5c61db553ec859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173612"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="543c6-102">in, modificateur de paramètre (référence C#)</span><span class="sxs-lookup"><span data-stu-id="543c6-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="543c6-103">Le mot clé `in` entraîne le passage des arguments par référence.</span><span class="sxs-lookup"><span data-stu-id="543c6-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="543c6-104">Il fait du paramètre formel un alias de l’argument, qui doit être une variable.</span><span class="sxs-lookup"><span data-stu-id="543c6-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="543c6-105">En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="543c6-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="543c6-106">Il est similaire aux mots clés [ref](ref.md) ou [out](out-parameter-modifier.md), sauf que les arguments `in` ne peuvent pas être modifiés par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="543c6-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="543c6-107">Alors que la modification des arguments `ref` est facultative, les arguments `out` doivent être modifiés par la méthode appelée ; ces modifications sont observables dans le contexte d’appel.</span><span class="sxs-lookup"><span data-stu-id="543c6-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="543c6-108">L’exemple précédent montre que le modificateur `in` n’est généralement pas nécessaire sur le site d’appel.</span><span class="sxs-lookup"><span data-stu-id="543c6-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="543c6-109">Il l’est uniquement dans la déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="543c6-109">It is only required in the method declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="543c6-110">Le mot clé `in` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est contravariant, dans le cadre d’une instruction `foreach` ou d’une clause `join` dans une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="543c6-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="543c6-111">Pour plus d’informations sur l’utilisation du mot clé `in` dans ces contextes, consultez [in](in.md), qui fournit des liens vers toutes ces utilisations.</span><span class="sxs-lookup"><span data-stu-id="543c6-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="543c6-112">Les variables passées comme des arguments `in` doivent être initialisées avant d’être passées dans un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="543c6-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="543c6-113">Toutefois, la méthode appelée ne peut pas attribuer de valeur ou modifier l’argument.</span><span class="sxs-lookup"><span data-stu-id="543c6-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="543c6-114">Le modificateur de paramètre `in` est disponible dans C# 7.2 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="543c6-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="543c6-115">Les versions précédentes génèrent une erreur de compilateur `CS8107` (« La fonctionnalité "références en lecture seule" n’est pas disponible dans C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="543c6-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="543c6-116">Utilisez la version 7.2 ou supérieure du langage. » Pour configurer la version du langage du compilateur, consultez [Sélectionner la version du langage C#](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="543c6-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="543c6-117">Les mots clés `in`, `ref` et `out` ne sont pas considérés comme faisant partie de la signature de méthode à des fins de résolution de surcharge.</span><span class="sxs-lookup"><span data-stu-id="543c6-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="543c6-118">Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l’une d’elles accepte un argument `ref` ou `in` et que l’autre accepte un argument `out`.</span><span class="sxs-lookup"><span data-stu-id="543c6-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="543c6-119">Le code suivant, par exemple, ne se compilera pas :</span><span class="sxs-lookup"><span data-stu-id="543c6-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="543c6-120">Une surcharge basée sur la présence de `in` est autorisée :</span><span class="sxs-lookup"><span data-stu-id="543c6-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="543c6-121">Règles de résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="543c6-121">Overload resolution rules</span></span>

<span data-ttu-id="543c6-122">Vous pouvez comprendre les règles de résolution de surcharge pour les méthodes par valeur par rapport à celles qui utilisent des arguments `in` en comprenant pourquoi on utilise des arguments `in`.</span><span class="sxs-lookup"><span data-stu-id="543c6-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="543c6-123">Vous pouvez optimiser les performances en définissant des méthodes à l’aide de paramètres `in`.</span><span class="sxs-lookup"><span data-stu-id="543c6-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="543c6-124">Certains arguments de type `struct` peuvent être volumineux et, quand les méthodes sont appelées dans des boucles serrées ou des chemins de code critiques, le coût de la copie de ces structures est crucial.</span><span class="sxs-lookup"><span data-stu-id="543c6-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="543c6-125">Les méthodes déclarent des paramètres `in` pour spécifier que des arguments peuvent être passés par référence en toute sécurité, car la méthode appelée ne modifie pas l’état de l’argument.</span><span class="sxs-lookup"><span data-stu-id="543c6-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="543c6-126">Le passage de ces arguments par référence permet d’éviter une copie (potentiellement) coûteuse.</span><span class="sxs-lookup"><span data-stu-id="543c6-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span>

<span data-ttu-id="543c6-127">La spécification de `in` pour des arguments au niveau de l’appel de site est généralement facultative.</span><span class="sxs-lookup"><span data-stu-id="543c6-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="543c6-128">Il n’existe aucune différence sémantique entre le passage d’arguments par valeur et leur passage par référence à l’aide du modificateur `in`.</span><span class="sxs-lookup"><span data-stu-id="543c6-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="543c6-129">Le modificateur `in` sur le site d’appel est facultatif, car vous n’avez pas besoin d’indiquer que la valeur de l’argument peut être changée.</span><span class="sxs-lookup"><span data-stu-id="543c6-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="543c6-130">Vous ajoutez explicitement le modificateur `in` sur le site d’appel pour vérifier que l’argument est passé par référence, non par valeur.</span><span class="sxs-lookup"><span data-stu-id="543c6-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="543c6-131">L’utilisation explicite de `in` a les deux effets suivants :</span><span class="sxs-lookup"><span data-stu-id="543c6-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="543c6-132">Tout d’abord, la spécification de `in` sur le site d’appel force le compilateur à sélectionner une méthode définie avec un paramètre `in` correspondant.</span><span class="sxs-lookup"><span data-stu-id="543c6-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="543c6-133">Sinon, quand deux méthodes diffèrent uniquement par la présence de `in`, la surcharge par valeur convient mieux.</span><span class="sxs-lookup"><span data-stu-id="543c6-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="543c6-134">Ensuite, la spécification de `in` déclare votre intention de passer un argument par référence.</span><span class="sxs-lookup"><span data-stu-id="543c6-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="543c6-135">L’argument utilisé avec `in` doit représenter un emplacement directement référençable.</span><span class="sxs-lookup"><span data-stu-id="543c6-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="543c6-136">Les mêmes règles générales pour les arguments `out` et `ref` s’appliquent : vous ne pouvez pas utiliser de constantes, de propriétés ordinaires ou d’autres expressions qui produisent des valeurs.</span><span class="sxs-lookup"><span data-stu-id="543c6-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="543c6-137">Sinon, l’omission de `in` sur le site d’appel informe le compilateur que vous l’autorisez à créer une variable temporaire à passer par référence en lecture seule à la méthode.</span><span class="sxs-lookup"><span data-stu-id="543c6-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="543c6-138">Le compilateur crée une variable temporaire pour surmonter plusieurs restrictions avec les arguments `in` :</span><span class="sxs-lookup"><span data-stu-id="543c6-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="543c6-139">Une variable temporaire autorise des constantes au moment de la compilation comme paramètres `in`.</span><span class="sxs-lookup"><span data-stu-id="543c6-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="543c6-140">Une variable temporaire autorise des propriétés ou d’autres expressions pour les paramètres `in`.</span><span class="sxs-lookup"><span data-stu-id="543c6-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="543c6-141">Une variable temporaire autorise des arguments pour lesquels il existe une conversion implicite de type d’argument en type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="543c6-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="543c6-142">Dans toutes les instances précédentes, le compilateur crée une variable temporaire qui stocke la valeur de la constante, la propriété ou une autre expression.</span><span class="sxs-lookup"><span data-stu-id="543c6-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="543c6-143">Le code suivant illustre ces règles :</span><span class="sxs-lookup"><span data-stu-id="543c6-143">The following code illustrates these rules:</span></span>

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="543c6-144">Supposons à présent qu’une autre méthode utilisant des arguments par valeur est disponible.</span><span class="sxs-lookup"><span data-stu-id="543c6-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="543c6-145">Les résultats changent comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="543c6-145">The results change as shown in the following code:</span></span>

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="543c6-146">Le seul appel de méthode dans lequel l’argument est passé par référence est le dernier.</span><span class="sxs-lookup"><span data-stu-id="543c6-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="543c6-147">Le code précédent utilise `int` comme type d’argument par souci de simplicité.</span><span class="sxs-lookup"><span data-stu-id="543c6-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="543c6-148">Comme `int` n’est pas plus volumineux qu’une référence dans la plupart des ordinateurs modernes, il n’y aucun avantage à passer un seul `int` comme référence en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="543c6-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span>

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="543c6-149">Limitations sur les paramètres `in`</span><span class="sxs-lookup"><span data-stu-id="543c6-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="543c6-150">Vous ne pouvez pas utiliser les mots clés `in`, `ref` ou `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="543c6-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="543c6-151">Méthodes async, que vous définissez à l’aide du modificateur [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="543c6-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="543c6-152">Les méthodes Iterator, qui incluent une instruction [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="543c6-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="543c6-153">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="543c6-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="543c6-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="543c6-154">See also</span></span>

- [<span data-ttu-id="543c6-155">Référence C</span><span class="sxs-lookup"><span data-stu-id="543c6-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="543c6-156">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="543c6-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="543c6-157">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="543c6-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="543c6-158">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="543c6-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="543c6-159">Écrire du code sécurisé et efficace</span><span class="sxs-lookup"><span data-stu-id="543c6-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
