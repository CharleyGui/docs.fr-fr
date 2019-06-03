---
title: as - Référence C#
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 84e599340877ce52dc6242ea259c69672915c546
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422014"
---
# <a name="as-c-reference"></a><span data-ttu-id="4a2eb-102">as (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4a2eb-102">as (C# Reference)</span></span>
<span data-ttu-id="4a2eb-103">Vous pouvez utiliser l’opérateur `as` pour effectuer certains types de conversions entre des types référence ou des [types Nullable](../../../csharp/programming-guide/nullable-types/index.md) compatibles.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="4a2eb-104">Le code suivant fournit un exemple.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="4a2eb-105">Comme le montre l’exemple, vous devez comparer le résultat de l’expression `as` avec `null` pour vérifier si la conversion a réussi.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="4a2eb-106">À partir de C# 7.0, vous pouvez utiliser l’expression [is](is.md) pour effectuer ce test et affecter une variable de manière conditionnelle en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="4a2eb-107">Dans de nombreux scénarios, elle est plus concise que l’opérateur `as`.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="4a2eb-108">Pour plus d’informations, voir la section [Modèle de type](is.md#type) de l’article [Opérateur `is`](is.md).</span><span class="sxs-lookup"><span data-stu-id="4a2eb-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="4a2eb-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4a2eb-109">Remarks</span></span>  
 <span data-ttu-id="4a2eb-110">L’opérateur `as` est semblable à une opération de cast.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="4a2eb-111">Toutefois, si la conversion n’est pas possible, `as` retourne `null` au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="4a2eb-112">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4a2eb-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="4a2eb-113">Le code est équivalent à l’expression suivante, à la différence que la variable `expression` n’est évaluée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="4a2eb-114">Notez que l’opérateur `as` effectue uniquement des conversions de référence, des conversions Nullable et des conversions boxing.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="4a2eb-115">L’opérateur `as` ne peut pas effectuer d’autres conversions, telles que les conversions définies par l’utilisateur, qui doivent être effectuées à l’aide d’expressions cast.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a2eb-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a2eb-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="4a2eb-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4a2eb-117">C# Language Specification</span></span>  

<span data-ttu-id="4a2eb-118">Pour plus d’informations, consultez [Opérateur as](~/_csharplang/spec/expressions.md#the-as-operator) dans la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a2eb-118">For more information, see [The as operator](~/_csharplang/spec/expressions.md#the-as-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="4a2eb-119">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-119">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="4a2eb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a2eb-120">See also</span></span>

- [<span data-ttu-id="4a2eb-121">Référence C#</span><span class="sxs-lookup"><span data-stu-id="4a2eb-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4a2eb-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4a2eb-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4a2eb-123">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4a2eb-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="4a2eb-124">is</span><span class="sxs-lookup"><span data-stu-id="4a2eb-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="4a2eb-125">?: Opérateur</span><span class="sxs-lookup"><span data-stu-id="4a2eb-125">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)
