---
description: var-référence C#
title: var-référence C#
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608710"
---
# <a name="var-c-reference"></a><span data-ttu-id="7f2fc-103">var (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7f2fc-103">var (C# reference)</span></span>

<span data-ttu-id="7f2fc-104">À compter de C# 3, les variables déclarées au niveau de la portée de la méthode peuvent avoir un « type » implicite `var` .</span><span class="sxs-lookup"><span data-stu-id="7f2fc-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="7f2fc-105">Une variable locale implicitement typée est fortement typée comme si vous aviez déclaré vous-même le type, alors que c’est le compilateur qui détermine le type.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="7f2fc-106">Les deux déclarations suivantes d’`i` sont équivalentes fonctionnellement :</span><span class="sxs-lookup"><span data-stu-id="7f2fc-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="7f2fc-107">Quand `var` est utilisé avec les [types référence Nullable](../builtin-types/nullable-reference-types.md) activés, il implique toujours un type référence Nullable même si le type d’expression n’accepte pas la valeur null.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="7f2fc-108">Le `var` mot clé est couramment utilisé avec les expressions d’appel de constructeur.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="7f2fc-109">L’utilisation de `var` vous permet de ne pas répéter un nom de type dans une déclaration de variable et une instanciation d’objet, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7f2fc-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="7f2fc-110">À compter de C# 9,0, vous pouvez utiliser une [ `new` expression](../operators/new-operator.md) de type cible comme alternative :</span><span class="sxs-lookup"><span data-stu-id="7f2fc-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a><span data-ttu-id="7f2fc-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7f2fc-111">Example</span></span>

<span data-ttu-id="7f2fc-112">L’exemple suivant présente deux expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-112">The following example shows two query expressions.</span></span> <span data-ttu-id="7f2fc-113">Dans la première expression, l’utilisation de `var` est autorisée, mais n’est pas obligatoire parce que le type du résultat de la requête peut être déclaré explicitement en tant que `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-113">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="7f2fc-114">Toutefois, dans la deuxième expression où `var` est utilisé, le résultat peut être une collection de types anonymes, et le nom de ce type n’est pas accessible sauf par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-114">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="7f2fc-115">Si vous utilisez `var`, vous n’avez pas besoin de créer une classe pour le résultat.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-115">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="7f2fc-116">Notez que, dans le deuxième exemple, la variable d’itération `foreach``item` doit également être implicitement typée.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-116">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="7f2fc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f2fc-117">See also</span></span>

- [<span data-ttu-id="7f2fc-118">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="7f2fc-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7f2fc-119">Variables locales implicitement typées</span><span class="sxs-lookup"><span data-stu-id="7f2fc-119">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="7f2fc-120">Relations de types dans les opérations de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="7f2fc-120">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
