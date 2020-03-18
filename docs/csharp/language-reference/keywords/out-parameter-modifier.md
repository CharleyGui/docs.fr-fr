---
title: out, modificateur de paramètre - Référence C#
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f963188d77685bb81f7dc9fb3794e343114fe3c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173560"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="fc46a-102">out, modificateur de paramètre (référence C#)</span><span class="sxs-lookup"><span data-stu-id="fc46a-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="fc46a-103">Le mot clé `out` entraîne le passage des arguments par référence.</span><span class="sxs-lookup"><span data-stu-id="fc46a-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="fc46a-104">Il fait du paramètre formel un alias de l’argument, qui doit être une variable.</span><span class="sxs-lookup"><span data-stu-id="fc46a-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="fc46a-105">En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="fc46a-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="fc46a-106">Il est similaire au mot clé [ref](ref.md), à la différence que `ref` nécessite que la variable soit initialisée avant d’être passée.</span><span class="sxs-lookup"><span data-stu-id="fc46a-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="fc46a-107">Il est également similaire au mot clé [in](in-parameter-modifier.md), à la différence que `in` n’autorise pas la méthode appelée à modifier la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="fc46a-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="fc46a-108">Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`.</span><span class="sxs-lookup"><span data-stu-id="fc46a-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="fc46a-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fc46a-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="fc46a-110">Le mot clé `out` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est covariant.</span><span class="sxs-lookup"><span data-stu-id="fc46a-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="fc46a-111">Pour plus d’informations sur l’utilisation du mot clé `out` dans ce contexte, consultez [out, modificateur générique](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="fc46a-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="fc46a-112">Les variables passées comme arguments `out` n’ont pas à être initialisées avant d’être passées dans un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="fc46a-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="fc46a-113">Toutefois, la méthode appelée doit assigner une valeur avant le retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="fc46a-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="fc46a-114">Les mots clés `in`, `ref` et `out` ne sont pas considérés comme faisant partie de la signature de méthode à des fins de résolution de surcharge.</span><span class="sxs-lookup"><span data-stu-id="fc46a-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="fc46a-115">Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l’une d’elles accepte un argument `ref` ou `in` et que l’autre accepte un argument `out`.</span><span class="sxs-lookup"><span data-stu-id="fc46a-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="fc46a-116">Le code suivant, par exemple, ne se compilera pas :</span><span class="sxs-lookup"><span data-stu-id="fc46a-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="fc46a-117">Toutefois, la surcharge est autorisée si une méthode prend un argument `ref`, `in` ou `out`, et que l’autre méthode n’a aucun de ces modificateurs, comme suit :</span><span class="sxs-lookup"><span data-stu-id="fc46a-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="fc46a-118">Le compilateur choisit la meilleure surcharge en mettant en correspondance les modificateurs de paramètre sur le site d’appel et les modificateurs de paramètre utilisés dans l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="fc46a-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="fc46a-119">Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.</span><span class="sxs-lookup"><span data-stu-id="fc46a-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="fc46a-120">Vous ne pouvez pas utiliser les mots clés `in`, `ref` ou `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="fc46a-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="fc46a-121">Méthodes async, que vous définissez à l’aide du modificateur [async](./async.md).</span><span class="sxs-lookup"><span data-stu-id="fc46a-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="fc46a-122">Les méthodes Iterator, qui incluent une instruction [yield return](./yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="fc46a-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="fc46a-123">Déclarer des paramètres `out`</span><span class="sxs-lookup"><span data-stu-id="fc46a-123">Declaring `out` parameters</span></span>

<span data-ttu-id="fc46a-124">Il arrive souvent que l’on déclare une méthode avec des arguments `out` pour qu’elle retourne plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="fc46a-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="fc46a-125">À compter de C# 7.0, vous pouvez recourir aux [tuples](../../tuples.md) dans ce type de scénario.</span><span class="sxs-lookup"><span data-stu-id="fc46a-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="fc46a-126">L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="fc46a-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="fc46a-127">Notez que le troisième argument reçoit la valeur null.</span><span class="sxs-lookup"><span data-stu-id="fc46a-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="fc46a-128">Cela permet aux méthodes de retourner des valeurs le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fc46a-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="fc46a-129">Appel d’une méthode avec un argument `out`</span><span class="sxs-lookup"><span data-stu-id="fc46a-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="fc46a-130">Dans C# 6 et les versions antérieures, vous devez déclarer une variable dans une instruction distincte avant de la passer comme argument `out`.</span><span class="sxs-lookup"><span data-stu-id="fc46a-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="fc46a-131">L’exemple suivant déclare une variable nommée `number` avant de la passer à la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), qui tente de convertir une chaîne en nombre.</span><span class="sxs-lookup"><span data-stu-id="fc46a-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="fc46a-132">À compter de C# 7.0, vous pouvez déclarer la variable `out` dans la liste d’arguments de l’appel de méthode au lieu de le faire dans une déclaration de variable distincte.</span><span class="sxs-lookup"><span data-stu-id="fc46a-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="fc46a-133">Cette technique rend le code plus simple et plus lisible, et vous empêche également d’assigner par inadvertance une valeur à la variable avant l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="fc46a-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="fc46a-134">L’exemple suivant est semblable au précédent, sauf qu’il définit la variable `number` dans l’appel de la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="fc46a-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="fc46a-135">Dans l’exemple précédent, la variable `number` est fortement typée en `int`.</span><span class="sxs-lookup"><span data-stu-id="fc46a-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="fc46a-136">Vous pouvez également déclarer une variable locale implicitement typée, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fc46a-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="fc46a-137">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="fc46a-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc46a-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc46a-138">See also</span></span>

- [<span data-ttu-id="fc46a-139">Référence C</span><span class="sxs-lookup"><span data-stu-id="fc46a-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc46a-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fc46a-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc46a-141">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="fc46a-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="fc46a-142">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="fc46a-142">Method Parameters</span></span>](./method-parameters.md)
