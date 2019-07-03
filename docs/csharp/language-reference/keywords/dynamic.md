---
title: dynamic - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: c8748f1869e8e2d5246910fac0100a6c70790579
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306648"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="166f4-102">dynamic (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="166f4-102">dynamic (C# Reference)</span></span>

<span data-ttu-id="166f4-103">Le type `dynamic` permet aux opérations dans lesquelles il se produit de contourner la vérification de type au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="166f4-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="166f4-104">Au lieu de cela, ces opérations sont résolues au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="166f4-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="166f4-105">Le type `dynamic` simplifie l’accès aux API COM telles que les API Office Automation, et également aux API dynamiques telles que les bibliothèques IronPython et au modèle DOM (Document Object Model) HTML.</span><span class="sxs-lookup"><span data-stu-id="166f4-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="166f4-106">Le type `dynamic` se comporte comme le type `object` dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="166f4-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="166f4-107">Toutefois, les opérations qui contiennent des expressions de type `dynamic` ne sont pas résolues et leur type n’est pas vérifié par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="166f4-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="166f4-108">Le compilateur empaquète des informations sur l’opération, qui sont ensuite utilisées pour évaluer l’opération au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="166f4-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="166f4-109">Dans le cadre du processus, les variables de type `dynamic` sont compilées dans des variables de type `object`.</span><span class="sxs-lookup"><span data-stu-id="166f4-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="166f4-110">Ainsi, le type `dynamic` existe seulement au moment de la compilation, et non au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="166f4-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="166f4-111">L’exemple suivant compare une variable de type `dynamic` à une variable de type `object`.</span><span class="sxs-lookup"><span data-stu-id="166f4-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="166f4-112">Pour vérifier le type de chaque variable au moment de la compilation, placez le pointeur de la souris sur `dyn` ou `obj` dans les instructions `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="166f4-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="166f4-113">IntelliSense affiche **dynamic** pour `dyn` et **object** pour `obj`.</span><span class="sxs-lookup"><span data-stu-id="166f4-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="166f4-114">Les instructions `WriteLine` affichent les types d’exécution de `dyn` et `obj`.</span><span class="sxs-lookup"><span data-stu-id="166f4-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="166f4-115">À ce stade, tous deux ont le même type, entier.</span><span class="sxs-lookup"><span data-stu-id="166f4-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="166f4-116">La sortie suivante est produite :</span><span class="sxs-lookup"><span data-stu-id="166f4-116">The following output is produced:</span></span>

`System.Int32`

`System.Int32`

<span data-ttu-id="166f4-117">Pour voir la différence entre `dyn` et `obj` au moment de la compilation, ajoutez les deux lignes suivantes entre les déclarations et les instructions `WriteLine` de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="166f4-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="166f4-118">Une erreur du compilateur est signalée pour la tentative d’ajout d’un entier et un d’objet dans l’expression `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="166f4-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="166f4-119">Toutefois, aucune erreur n’est signalée pour `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="166f4-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="166f4-120">L’expression qui contient `dyn` n’est pas vérifié au moment de la compilation, car le type de `dyn` est `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="166f4-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

## <a name="context"></a><span data-ttu-id="166f4-121">Contexte</span><span class="sxs-lookup"><span data-stu-id="166f4-121">Context</span></span>

<span data-ttu-id="166f4-122">Le mot clé `dynamic` peut apparaître directement ou en tant que composant d’un type construit dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="166f4-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>

- <span data-ttu-id="166f4-123">Dans les déclarations, comme le type d’une propriété, d’un champ, d’un indexeur, d’un paramètre, d’une valeur de retour, d’une variable locale ou d’une contrainte de type.</span><span class="sxs-lookup"><span data-stu-id="166f4-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="166f4-124">La définition de classe suivante utilise `dynamic` dans plusieurs déclarations différentes.</span><span class="sxs-lookup"><span data-stu-id="166f4-124">The following class definition uses `dynamic` in several different declarations.</span></span>

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- <span data-ttu-id="166f4-125">Dans les conversions de type explicites, comme le type cible d’une conversion.</span><span class="sxs-lookup"><span data-stu-id="166f4-125">In explicit type conversions, as the target type of a conversion.</span></span>

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- <span data-ttu-id="166f4-126">Dans tout contexte où les types servent de valeurs, comme sur le côté droit d’un opérateur `is` ou d’un opérateur `as`, ou comme argument de `typeof` dans le cadre d’un type construit.</span><span class="sxs-lookup"><span data-stu-id="166f4-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="166f4-127">Par exemple, `dynamic` peut être utilisé dans les expressions suivantes.</span><span class="sxs-lookup"><span data-stu-id="166f4-127">For example, `dynamic` can be used in the following expressions.</span></span>

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a><span data-ttu-id="166f4-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="166f4-128">Example</span></span>

<span data-ttu-id="166f4-129">L’exemple suivant utilise `dynamic` dans plusieurs déclarations.</span><span class="sxs-lookup"><span data-stu-id="166f4-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="166f4-130">La méthode `Main` compare également la vérification de type au moment de la compilation avec la vérification de type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="166f4-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

<span data-ttu-id="166f4-131">Pour obtenir plus d’informations et d’exemples, consultez [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="166f4-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="166f4-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="166f4-132">See also</span></span>

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="166f4-133">Utilisation du type dynamic</span><span class="sxs-lookup"><span data-stu-id="166f4-133">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="166f4-134">object</span><span class="sxs-lookup"><span data-stu-id="166f4-134">object</span></span>](object.md)
- [<span data-ttu-id="166f4-135">is</span><span class="sxs-lookup"><span data-stu-id="166f4-135">is</span></span>](../operators/type-testing-and-conversion-operators.md#is-operator)
- [<span data-ttu-id="166f4-136">as</span><span class="sxs-lookup"><span data-stu-id="166f4-136">as</span></span>](../operators/type-testing-and-conversion-operators.md#as-operator)
- [<span data-ttu-id="166f4-137">typeof</span><span class="sxs-lookup"><span data-stu-id="166f4-137">typeof</span></span>](../operators/type-testing-and-conversion-operators.md#typeof-operator)
- [<span data-ttu-id="166f4-138">Guide pratique pour caster de manière sécurisée avec les critères spéciaux, ainsi que les opérateurs is et as</span><span class="sxs-lookup"><span data-stu-id="166f4-138">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="166f4-139">Procédure pas à pas : création et utilisation d’objets dynamiques</span><span class="sxs-lookup"><span data-stu-id="166f4-139">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
