---
description: var - Référence C#
title: var - Référence C#
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141710"
---
# <a name="var-c-reference"></a><span data-ttu-id="726be-103">var (référence C#)</span><span class="sxs-lookup"><span data-stu-id="726be-103">var (C# Reference)</span></span>

<span data-ttu-id="726be-104">Depuis Visual C# 3.0, les variables déclarées à la portée de la méthode peuvent avoir un type implicite `var`.</span><span class="sxs-lookup"><span data-stu-id="726be-104">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="726be-105">Une variable locale implicitement typée est fortement typée comme si vous aviez déclaré vous-même le type, alors que c’est le compilateur qui détermine le type.</span><span class="sxs-lookup"><span data-stu-id="726be-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="726be-106">Les deux déclarations suivantes d’`i` sont équivalentes fonctionnellement :</span><span class="sxs-lookup"><span data-stu-id="726be-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="726be-107">Pour plus d’informations, consultez [variables locales implicitement typées](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [relations de types dans les opérations de requête LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="726be-107">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="726be-108">Quand `var` est utilisé avec les types référence Nullable activés, il implique toujours un type référence Nullable même si le type d’expression n’accepte pas la valeur null.</span><span class="sxs-lookup"><span data-stu-id="726be-108">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="726be-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="726be-109">Example</span></span>

<span data-ttu-id="726be-110">L’exemple suivant présente deux expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="726be-110">The following example shows two query expressions.</span></span> <span data-ttu-id="726be-111">Dans la première expression, l’utilisation de `var` est autorisée, mais n’est pas obligatoire parce que le type du résultat de la requête peut être déclaré explicitement en tant que `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="726be-111">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="726be-112">Toutefois, dans la deuxième expression où `var` est utilisé, le résultat peut être une collection de types anonymes, et le nom de ce type n’est pas accessible sauf par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="726be-112">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="726be-113">Si vous utilisez `var`, vous n’avez pas besoin de créer une classe pour le résultat.</span><span class="sxs-lookup"><span data-stu-id="726be-113">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="726be-114">Notez que, dans le deuxième exemple, la variable d’itération `foreach``item` doit également être implicitement typée.</span><span class="sxs-lookup"><span data-stu-id="726be-114">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="726be-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="726be-115">See also</span></span>

- [<span data-ttu-id="726be-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="726be-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="726be-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="726be-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="726be-118">Variables locales implicitement typées</span><span class="sxs-lookup"><span data-stu-id="726be-118">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
