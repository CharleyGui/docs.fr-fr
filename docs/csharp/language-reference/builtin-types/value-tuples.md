---
title: Types de tuple-référence C#
description: 'En savoir plus sur les tuples C# : structures de données légères que vous pouvez utiliser pour regrouper des éléments de données faiblement liés'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: d996c7afecba1b58bfd8337fa444fd71790dd482
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471770"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="3a82f-103">Types de tuples (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3a82f-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="3a82f-104">Disponible en C# 7,0 et versions ultérieures, la fonctionnalité de *tuples* fournit une syntaxe concise pour regrouper plusieurs éléments de données dans une structure de données légère.</span><span class="sxs-lookup"><span data-stu-id="3a82f-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="3a82f-105">L’exemple suivant montre comment vous pouvez déclarer une variable de tuple, l’initialiser et accéder à ses membres de données :</span><span class="sxs-lookup"><span data-stu-id="3a82f-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/shared/ValueTuples.cs#Introduction)]

<span data-ttu-id="3a82f-106">Comme le montre l’exemple précédent, pour définir un type de tuple, vous spécifiez les types de tous ses membres de données et, éventuellement, les [noms de champs](#tuple-field-names).</span><span class="sxs-lookup"><span data-stu-id="3a82f-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="3a82f-107">Vous ne pouvez pas définir de méthodes dans un type de tuple, mais vous pouvez utiliser les méthodes fournies par .NET, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/shared/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="3a82f-108">À compter de C# 7,3, les types de tuple prennent en charge les [opérateurs d’égalité](../operators/equality-operators.md) `==` et `!=` .</span><span class="sxs-lookup"><span data-stu-id="3a82f-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="3a82f-109">Pour plus d’informations, consultez la section [égalité des tuples](#tuple-equality) .</span><span class="sxs-lookup"><span data-stu-id="3a82f-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="3a82f-110">Les types de tuples sont des [types valeur](value-types.md); les éléments de tuple sont des champs publics.</span><span class="sxs-lookup"><span data-stu-id="3a82f-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="3a82f-111">Cela rend les types valeur *mutable* de tuples.</span><span class="sxs-lookup"><span data-stu-id="3a82f-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="3a82f-112">La fonctionnalité des tuples requiert le <xref:System.ValueTuple?displayProperty=nameWithType> type et les types génériques associés (par exemple, <xref:System.ValueTuple%602?displayProperty=nameWithType> ), qui sont disponibles dans .net Core et .NET Framework 4,7 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3a82f-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="3a82f-113">Pour utiliser des tuples dans un projet qui cible .NET Framework 4.6.2 ou version antérieure, ajoutez le package NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) au projet.</span><span class="sxs-lookup"><span data-stu-id="3a82f-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="3a82f-114">Vous pouvez définir des tuples avec un grand nombre d’éléments arbitraires :</span><span class="sxs-lookup"><span data-stu-id="3a82f-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/shared/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="3a82f-115">Cas d’usage de tuples</span><span class="sxs-lookup"><span data-stu-id="3a82f-115">Use cases of tuples</span></span>

<span data-ttu-id="3a82f-116">L’un des cas d’utilisation les plus courants de tuples est le type de retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3a82f-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="3a82f-117">Autrement dit, au lieu de définir des [ `out` paramètres de méthode](../keywords/out-parameter-modifier.md), vous pouvez regrouper les résultats de méthode dans un type de retour de tuple, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/shared/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="3a82f-118">Comme le montre l’exemple précédent, vous pouvez utiliser l’instance de tuple retournée directement ou la [décomposer](#tuple-assignment-and-deconstruction) dans des variables distinctes.</span><span class="sxs-lookup"><span data-stu-id="3a82f-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="3a82f-119">Vous pouvez également utiliser des types de tuples au lieu de [types anonymes](../../programming-guide/classes-and-structs/anonymous-types.md). par exemple, dans les requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="3a82f-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="3a82f-120">Pour plus d’informations, consultez [choix entre les types de tuples et anonymes](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span><span class="sxs-lookup"><span data-stu-id="3a82f-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="3a82f-121">En général, vous utilisez des tuples pour regrouper des éléments de données faiblement liés.</span><span class="sxs-lookup"><span data-stu-id="3a82f-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="3a82f-122">Cela est généralement utile dans les méthodes utilitaires privées et internes.</span><span class="sxs-lookup"><span data-stu-id="3a82f-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="3a82f-123">Dans le cas d’une API publique, envisagez de définir une [classe](../keywords/class.md) ou un type de [structure](struct.md) .</span><span class="sxs-lookup"><span data-stu-id="3a82f-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="3a82f-124">Noms de champs de Tuple</span><span class="sxs-lookup"><span data-stu-id="3a82f-124">Tuple field names</span></span>

<span data-ttu-id="3a82f-125">Vous pouvez spécifier explicitement les noms des champs de tuple dans une expression d’initialisation de tuple ou dans la définition d’un type de tuple, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/shared/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="3a82f-126">À compter de C# 7,1, si vous ne spécifiez pas de nom de champ, il peut être déduit à partir du nom de la variable correspondante dans une expression d’initialisation de tuple, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/shared/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="3a82f-127">C’est ce que l’on appelle des initialiseurs de projection de Tuple.</span><span class="sxs-lookup"><span data-stu-id="3a82f-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="3a82f-128">Le nom d’une variable n’est pas projeté sur un nom de champ de tuple dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="3a82f-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="3a82f-129">Le nom du candidat est un nom de membre d’un type de tuple, par exemple,, `Item3` `ToString` ou `Rest` .</span><span class="sxs-lookup"><span data-stu-id="3a82f-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="3a82f-130">Le nom du candidat est un doublon d’un autre nom de champ de tuple, explicite ou implicite.</span><span class="sxs-lookup"><span data-stu-id="3a82f-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="3a82f-131">Dans ce cas, vous spécifiez explicitement le nom d’un champ ou vous accédez à un champ par son nom par défaut.</span><span class="sxs-lookup"><span data-stu-id="3a82f-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="3a82f-132">Les noms par défaut des champs de tuple sont `Item1` , `Item2` , `Item3` et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="3a82f-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="3a82f-133">Vous pouvez toujours utiliser le nom par défaut d’un champ, même lorsqu’un nom de champ est spécifié de manière explicite ou déduite, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/shared/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="3a82f-134">Les [comparaisons d’égalité](#tuple-equality) des tuples et [des tuples](#tuple-assignment-and-deconstruction) ne prennent pas en compte les noms de champs.</span><span class="sxs-lookup"><span data-stu-id="3a82f-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="3a82f-135">Au moment de la compilation, le compilateur remplace les noms de champs non par défaut par les noms par défaut correspondants.</span><span class="sxs-lookup"><span data-stu-id="3a82f-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="3a82f-136">Par conséquent, les noms de champs explicitement spécifiés ou inférés ne sont pas disponibles au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3a82f-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="3a82f-137">Assignation et déconstruction de Tuple</span><span class="sxs-lookup"><span data-stu-id="3a82f-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="3a82f-138">C# prend en charge l’assignation entre les types tuple qui satisfont les deux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a82f-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="3a82f-139">les deux types de tuples ont le même nombre d’éléments</span><span class="sxs-lookup"><span data-stu-id="3a82f-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="3a82f-140">pour chaque position de tuple, le type de l’élément de tuple de droite est le même que ou implicitement convertible en type de l’élément de tuple de gauche correspondant</span><span class="sxs-lookup"><span data-stu-id="3a82f-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="3a82f-141">Les valeurs d’éléments tuples sont assignées à la suite de l’ordre des éléments de Tuple.</span><span class="sxs-lookup"><span data-stu-id="3a82f-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="3a82f-142">Les noms des champs de tuple sont ignorés et non assignés, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/shared/ValueTuples.cs#Assignment)]

<span data-ttu-id="3a82f-143">Vous pouvez également utiliser l’opérateur `=` d’assignation pour *déconstruire* une instance de tuple dans des variables distinctes.</span><span class="sxs-lookup"><span data-stu-id="3a82f-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="3a82f-144">Pour ce faire, vous pouvez procéder de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a82f-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="3a82f-145">Déclarez explicitement le type de chaque variable à l’intérieur des parenthèses :</span><span class="sxs-lookup"><span data-stu-id="3a82f-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/shared/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="3a82f-146">Utilisez le `var` mot clé en dehors des parenthèses pour déclarer les variables implicitement typées et laisser le compilateur déduire leurs types :</span><span class="sxs-lookup"><span data-stu-id="3a82f-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/shared/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="3a82f-147">Utiliser des variables existantes :</span><span class="sxs-lookup"><span data-stu-id="3a82f-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/shared/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="3a82f-148">Pour plus d’informations sur la déconstruction de tuples et d’autres types, consultez déconstruction de [tuples et d’autres types](../../deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="3a82f-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="3a82f-149">Égalité des tuples</span><span class="sxs-lookup"><span data-stu-id="3a82f-149">Tuple equality</span></span>

<span data-ttu-id="3a82f-150">À compter de C# 7.3, les types tuple prennent en charge les opérateurs `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="3a82f-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="3a82f-151">Ces opérateurs comparent les membres de l’opérande de gauche avec les membres correspondants de l’opérande de droite suivant l’ordre des éléments de Tuple.</span><span class="sxs-lookup"><span data-stu-id="3a82f-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/shared/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="3a82f-152">Comme le montre l’exemple précédent, `==` les `!=` opérations et ne prennent pas en compte les noms de champs de Tuple.</span><span class="sxs-lookup"><span data-stu-id="3a82f-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="3a82f-153">Deux tuples sont comparables lorsque les deux conditions suivantes sont satisfaites :</span><span class="sxs-lookup"><span data-stu-id="3a82f-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="3a82f-154">Les deux tuples ont le même nombre d’éléments.</span><span class="sxs-lookup"><span data-stu-id="3a82f-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="3a82f-155">Par exemple, `t1 != t2` ne compile pas si `t1` et `t2` ont un nombre d’éléments différent.</span><span class="sxs-lookup"><span data-stu-id="3a82f-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="3a82f-156">Pour chaque position de tuple, les éléments correspondants des opérandes de tuple de gauche et de droite sont comparables aux `==` opérateurs et `!=` .</span><span class="sxs-lookup"><span data-stu-id="3a82f-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="3a82f-157">Par exemple, `(1, (2, 3)) == ((1, 2), 3)` ne se compile `1` pas, car n’est pas comparable à `(1, 2)` .</span><span class="sxs-lookup"><span data-stu-id="3a82f-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="3a82f-158">Les `==` `!=` opérateurs et comparent les tuples en mode court-circuit.</span><span class="sxs-lookup"><span data-stu-id="3a82f-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="3a82f-159">Autrement dit, une opération s’arrête dès qu’elle rencontre une paire d’éléments non égaux ou atteint les terminaisons des tuples.</span><span class="sxs-lookup"><span data-stu-id="3a82f-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="3a82f-160">Toutefois, avant toute comparaison, *tous les* éléments tuples sont évalués, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a82f-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/shared/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="3a82f-161">Tuples en tant que paramètres de sortie</span><span class="sxs-lookup"><span data-stu-id="3a82f-161">Tuples as out parameters</span></span>

<span data-ttu-id="3a82f-162">En règle générale, vous refactorisez une méthode qui a des [ `out` paramètres](../keywords/out-parameter-modifier.md) dans une méthode qui retourne un tuple.</span><span class="sxs-lookup"><span data-stu-id="3a82f-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="3a82f-163">Toutefois, il existe des cas dans lesquels un `out` paramètre peut être de type Tuple.</span><span class="sxs-lookup"><span data-stu-id="3a82f-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="3a82f-164">L’exemple suivant montre comment utiliser des tuples en tant que `out` Paramètres :</span><span class="sxs-lookup"><span data-stu-id="3a82f-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/shared/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="3a82f-165">Tuples et `System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="3a82f-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="3a82f-166">Les tuples C#, qui sont sauvegardés par les <xref:System.ValueTuple?displayProperty=nameWithType> types, sont différents des tuples représentés par les <xref:System.Tuple?displayProperty=nameWithType> types.</span><span class="sxs-lookup"><span data-stu-id="3a82f-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="3a82f-167">Les principales différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a82f-167">The main differences are as follows:</span></span>

- <span data-ttu-id="3a82f-168">`ValueTuple` les types sont des [types valeur](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="3a82f-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="3a82f-169">`Tuple` les types sont des [types référence](../keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="3a82f-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="3a82f-170">`ValueTuple` les types sont mutables.</span><span class="sxs-lookup"><span data-stu-id="3a82f-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="3a82f-171">`Tuple` les types sont immuables.</span><span class="sxs-lookup"><span data-stu-id="3a82f-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="3a82f-172">Les membres de données de `ValueTuple` types sont des champs.</span><span class="sxs-lookup"><span data-stu-id="3a82f-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="3a82f-173">Les membres de données de `Tuple` types sont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="3a82f-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3a82f-174">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3a82f-174">C# language specification</span></span>

<span data-ttu-id="3a82f-175">Pour plus d’informations, consultez les notes de la proposition de fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a82f-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="3a82f-176">Déduire les noms de tuples (également appelés initialiseurs de projection de Tuple)</span><span class="sxs-lookup"><span data-stu-id="3a82f-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="3a82f-177">Prise en charge pour `==` et `!=` sur les types de Tuple</span><span class="sxs-lookup"><span data-stu-id="3a82f-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="3a82f-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a82f-178">See also</span></span>

- [<span data-ttu-id="3a82f-179">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="3a82f-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3a82f-180">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="3a82f-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="3a82f-181">Choix entre les types de tuples et anonymes</span><span class="sxs-lookup"><span data-stu-id="3a82f-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
