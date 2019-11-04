---
title: Variables locales implicitement typées - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 7010c38797ab64e5106c96c06cd814c143ca9c24
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419386"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="a8937-102">Variables locales implicitement typées (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a8937-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="a8937-103">Les variables locales peuvent être déclarées sans donner de type explicite.</span><span class="sxs-lookup"><span data-stu-id="a8937-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="a8937-104">Le mot clé `var` indique au compilateur de déduire le type de la variable à partir de l’expression située à droite de l’instruction d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="a8937-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="a8937-105">Le type déduit peut être un type intégré, un type anonyme, un type défini par l’utilisateur ou un type défini dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8937-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="a8937-106">Pour plus d’informations sur l’initialisation des tableaux avec `var`, consultez [Tableaux implicitement typés](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a8937-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="a8937-107">Les exemples suivants montrent différentes manières de déclarer des variables locales avec `var` :</span><span class="sxs-lookup"><span data-stu-id="a8937-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="a8937-108">Il est important de comprendre que le mot clé `var` n’est pas « variant » et qu’il n’indique pas que la variable est peu typée ou à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="a8937-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="a8937-109">Cela signifie simplement que le compilateur détermine et assigne le type qui convient le mieux.</span><span class="sxs-lookup"><span data-stu-id="a8937-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="a8937-110">Le mot clé `var` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="a8937-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="a8937-111">Dans des variables locales (variables déclarées dans la portée de la méthode), comme indiqué dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="a8937-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="a8937-112">Dans une instruction d’initialisation [for](../../language-reference/keywords/for.md)</span><span class="sxs-lookup"><span data-stu-id="a8937-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for(var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="a8937-113">Dans une instruction d’initialisation [foreach](../../language-reference/keywords/foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="a8937-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach(var item in list){...}
    ```

- <span data-ttu-id="a8937-114">Dans une instruction [using](../../language-reference/keywords/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a8937-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="a8937-115">Pour plus d’informations, consultez [Guide pratique pour utiliser des tableaux et des variables locales implicitement typés dans une expression de requête](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="a8937-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="a8937-116">Types var et anonymes</span><span class="sxs-lookup"><span data-stu-id="a8937-116">var and anonymous types</span></span>

<span data-ttu-id="a8937-117">Dans de nombreux cas, l’utilisation de `var` est facultative et sert uniquement à simplifier la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a8937-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="a8937-118">Toutefois, lorsqu’une variable est initialisée avec un type anonyme, vous devez déclarer la variable en tant que `var` si vous savez déjà que vous aurez besoin d’accéder aux propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="a8937-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="a8937-119">Il s’agit d’un scénario courant avec les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8937-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="a8937-120">Pour plus d’informations, consultez la page [Types anonymes](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8937-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="a8937-121">Du point de vue de votre code source, un type anonyme n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="a8937-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="a8937-122">Par conséquent, si une variable de requête a été initialisée avec `var`, la seule façon d’accéder aux propriétés de la séquence d’objets retournée consiste à utiliser `var` comme type pour la variable d’itération de l’instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="a8937-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="a8937-123">Notes</span><span class="sxs-lookup"><span data-stu-id="a8937-123">Remarks</span></span>

<span data-ttu-id="a8937-124">Les restrictions suivantes s’appliquent aux déclarations de variables implicitement typées :</span><span class="sxs-lookup"><span data-stu-id="a8937-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="a8937-125">`var` peut être utilisé uniquement lorsqu’une variable locale est déclarée et initialisée dans la même instruction. La variable ne peut pas être initialisée vers la valeur Null, vers un groupe de méthodes ou vers une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="a8937-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="a8937-126">`var` ne peut pas être utilisé dans les champs situés dans la portée de la classe.</span><span class="sxs-lookup"><span data-stu-id="a8937-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="a8937-127">Les variables déclarées à l’aide de `var` ne peuvent pas être utilisées dans l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="a8937-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="a8937-128">En d’autres termes, l’expression `: int i = (i = 20);` est légale, mais l’expression `var i = (i = 20);` génère une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="a8937-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="a8937-129">Il n’est pas possible d’initialiser plusieurs variables implicitement typées dans la même instruction.</span><span class="sxs-lookup"><span data-stu-id="a8937-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="a8937-130">Si un type nommé `var` se trouve dans la portée, le mot clé `var` est résolu en ce nom de type et n’est pas considéré comme faisant partie d’une déclaration de variable locale implicitement typée.</span><span class="sxs-lookup"><span data-stu-id="a8937-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="a8937-131">Le typage implicite avec le mot clé `var` ne peut être appliqué qu’aux variables comprises dans la portée de la méthode locale.</span><span class="sxs-lookup"><span data-stu-id="a8937-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="a8937-132">Le typage implicite n’est pas disponible pour les champs de classe, car le compilateur C# rencontrerait un paradoxe logique pendant le traitement du code : le compilateur a besoin de connaître le type du champ, mais il ne peut pas déterminer le type tant que l’expression d’assignation n’est pas analysée, et l’expression ne peut pas être évaluée sans connaître le type.</span><span class="sxs-lookup"><span data-stu-id="a8937-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="a8937-133">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a8937-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="a8937-134">`bookTitles` est un champ de classe de type `var`.</span><span class="sxs-lookup"><span data-stu-id="a8937-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="a8937-135">Le champ n’ayant aucune expression à évaluer, le compilateur ne peut pas déduire le type que `bookTitles` est censé avoir.</span><span class="sxs-lookup"><span data-stu-id="a8937-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="a8937-136">De plus, l’ajout d’une expression au champ (comme vous le feriez pour une variable locale) est également insuffisant :</span><span class="sxs-lookup"><span data-stu-id="a8937-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="a8937-137">Quand le compilateur rencontre des champs pendant la compilation du code, il enregistre le type de chaque champ avant de traiter toutes les expressions associées.</span><span class="sxs-lookup"><span data-stu-id="a8937-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="a8937-138">Le compilateur rencontre le même paradoxe en essayant d’analyser `bookTitles` : il doit connaître le type du champ, mais il détermine normalement le type de `var` en analysant l’expression, ce qui est impossible sans connaître le type au préalable.</span><span class="sxs-lookup"><span data-stu-id="a8937-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="a8937-139">`var` peut également être utile avec les expressions de requête dans lesquelles il est difficile de déterminer le type construit exact de la variable de requête.</span><span class="sxs-lookup"><span data-stu-id="a8937-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="a8937-140">Cela peut se produire avec les opérations de regroupement et de classement.</span><span class="sxs-lookup"><span data-stu-id="a8937-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="a8937-141">Le mot clé `var` peut également être utile lorsque le type de la variable est fastidieux à taper, ou bien lorsqu’il est évident ou lorsqu’il n’aide pas à la lisibilité du code.</span><span class="sxs-lookup"><span data-stu-id="a8937-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="a8937-142">Par exemple, `var` est utile avec les types génériques imbriqués tels que ceux utilisés avec les opérations de groupe.</span><span class="sxs-lookup"><span data-stu-id="a8937-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="a8937-143">Dans la requête suivante, le type de la variable de requête est `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="a8937-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="a8937-144">Tant que les personnes qui doivent gérer votre code comprennent ceci, le typage implicite peut tout à fait être utilisé pour rendre votre code plus concis et simplifier sa gestion.</span><span class="sxs-lookup"><span data-stu-id="a8937-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="a8937-145">Toutefois, l’utilisation de `var` risque de rendre votre code plus difficile à comprendre pour les autres développeurs.</span><span class="sxs-lookup"><span data-stu-id="a8937-145">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="a8937-146">C’est pourquoi, en général, la documentation C# utilise `var` uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a8937-146">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8937-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8937-147">See also</span></span>

- [<span data-ttu-id="a8937-148">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="a8937-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="a8937-149">Tableaux implicitement typés</span><span class="sxs-lookup"><span data-stu-id="a8937-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="a8937-150">Comment : utiliser des tableaux et des variables locales implicitement typés dans une expression de requête</span><span class="sxs-lookup"><span data-stu-id="a8937-150">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="a8937-151">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="a8937-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="a8937-152">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="a8937-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="a8937-153">var</span><span class="sxs-lookup"><span data-stu-id="a8937-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="a8937-154">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="a8937-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="a8937-155">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="a8937-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="a8937-156">for</span><span class="sxs-lookup"><span data-stu-id="a8937-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="a8937-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="a8937-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="a8937-158">using, instruction</span><span class="sxs-lookup"><span data-stu-id="a8937-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
