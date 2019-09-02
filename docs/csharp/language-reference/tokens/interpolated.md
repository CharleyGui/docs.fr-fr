---
title: $ - interpolation de chaîne - Référence C#
ms.custom: seodec18
description: L’interpolation de chaîne fournit une syntaxe plus lisible et plus pratique pour mettre en forme la sortie de chaîne que la traditionnelle mise en forme composite de chaîne.
ms.date: 04/29/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 1f0d63a549daa9fecd0cce3a7e5a6496929c37d2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202959"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="3ef3f-103">$ - interpolation de chaîne (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="3ef3f-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="3ef3f-104">Le caractère spécial `$` identifie un littéral de chaîne comme une *chaîne interpolée*.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="3ef3f-105">Une chaîne interpolée est un littéral de chaîne qui peut contenir des *expressions d’interpolation*.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="3ef3f-106">Quand une chaîne interpolée est résolue en une chaîne de résultat, les éléments avec des expressions d’interpolation sont remplacés par les représentations sous forme de chaîne des résultats des expressions.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="3ef3f-107">Cette fonctionnalité est disponible dans C# 6 et les versions ultérieures du langage.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="3ef3f-108">L’interpolation de chaîne offre une syntaxe plus lisible et plus simple pour créer des chaînes mises en forme que la fonctionnalité de [mise en forme de chaîne composite](../../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="3ef3f-109">L’exemple suivant utilise les deux fonctionnalités pour produire la même sortie :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="3ef3f-110">Structure d’une chaîne interpolée</span><span class="sxs-lookup"><span data-stu-id="3ef3f-110">Structure of an interpolated string</span></span>

<span data-ttu-id="3ef3f-111">Pour identifier un littéral de chaîne comme chaîne interpolée, préfixez-la du symbole `$`.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="3ef3f-112">N’ajoutez pas d’espace entre les signes `$` et `"` au début d’un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="3ef3f-113">Cela provoque une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="3ef3f-114">La structure d’un élément avec une expression d’interpolation se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-114">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="3ef3f-115">Les éléments entre crochets sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="3ef3f-116">Le tableau suivant décrit chaque élément :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-116">The following table describes each element:</span></span>

|<span data-ttu-id="3ef3f-117">Élément</span><span class="sxs-lookup"><span data-stu-id="3ef3f-117">Element</span></span>|<span data-ttu-id="3ef3f-118">Description</span><span class="sxs-lookup"><span data-stu-id="3ef3f-118">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="3ef3f-119">Expression qui produit un résultat à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="3ef3f-120">La représentation sous forme de chaîne du résultat `null` est <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="3ef3f-121">Expression constante dont la valeur définit le nombre minimal de caractères dans la représentation sous forme de chaîne du résultat de l’expression d’interpolation.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolation expression.</span></span> <span data-ttu-id="3ef3f-122">Si le nombre est positif, la représentation sous forme de chaîne est alignée à droite ; s’il est négatif, elle est alignée à gauche.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="3ef3f-123">Pour plus d'informations, consultez [Composant d’alignement](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="3ef3f-124">Chaîne de format qui est prise en charge par le type de résultat de l’expression.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="3ef3f-125">Pour plus d'informations, consultez [Composant de chaîne de format](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="3ef3f-126">L’exemple suivant utilise les composants de mise en forme facultatifs décrits ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="3ef3f-127">Caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="3ef3f-127">Special characters</span></span>

<span data-ttu-id="3ef3f-128">Pour ajouter une accolade, « { » ou « } », dans le texte produit par une chaîne interpolée, entrez deux accolades, « {{ » ou « }} ».</span><span class="sxs-lookup"><span data-stu-id="3ef3f-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="3ef3f-129">Pour plus d'informations, consultez [Accolades d’échappement](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="3ef3f-130">Comme le caractère deux-points (« : ») a une signification spéciale dans un élément d’expression d’interpolation, pour utiliser un [opérateur conditionnel](../operators/conditional-operator.md) dans une expression d’interpolation, placez cette expression entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-130">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="3ef3f-131">L’exemple suivant montre comment ajouter une accolade dans une chaîne de résultat et comment utiliser un opérateur conditionnel dans une expression d’interpolation :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="3ef3f-132">Une chaîne interpolée textuelle commence par le caractère `$` suivi du caractère `@`.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="3ef3f-133">Pour plus d’informations sur les chaînes textuelles, consultez les rubriques [string](../keywords/string.md) et [Identificateur textuel](verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="3ef3f-134">Le jeton `$` doit apparaître avant le jeton `@` dans une chaîne interpolée textuelle.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="3ef3f-135">Conversions implicites et spécification de l’implémentation de `IFormatProvider`</span><span class="sxs-lookup"><span data-stu-id="3ef3f-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="3ef3f-136">Trois conversions implicites sont possibles à partir d’une chaîne interpolée :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="3ef3f-137">Conversion d’une chaîne interpolée en instance de <xref:System.String> qui est le résultat de la résolution d’une chaîne interpolée avec des éléments d’expression d’interpolation remplacés par la représentation sous forme de chaîne correctement mise en forme de leurs résultats.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="3ef3f-138">Cette conversion utilise la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="3ef3f-139">Conversion d’une chaîne interpolée en instance <xref:System.FormattableString> qui représente une chaîne de format composite avec les résultats d’expression à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="3ef3f-140">Cette conversion vous permet de créer plusieurs chaînes de résultat avec du contenu propre à la culture à partir d’une seule instance de <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="3ef3f-141">Pour ce faire, appelez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="3ef3f-142">Une surcharge <xref:System.FormattableString.ToString> qui produit une chaîne de résultat pour <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="3ef3f-143">Une méthode <xref:System.FormattableString.Invariant%2A> qui produit une chaîne de résultat pour <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="3ef3f-144">Une méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> qui produit une chaîne de résultat pour une culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="3ef3f-145">Vous pouvez également utiliser la méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> pour fournir une implémentation définie par l’utilisateur de l’interface <xref:System.IFormatProvider> qui prend en charge une mise en forme personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="3ef3f-146">Pour plus d’informations, consultez [Mise en forme personnalisée avec ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="3ef3f-147">Conversion d’une chaîne interpolée en instance <xref:System.IFormattable> qui vous permet aussi de créer plusieurs chaînes de résultat avec du contenu propre à la culture à partir d’une seule instance de <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="3ef3f-148">L’exemple suivant utilise la conversion implicite en <xref:System.FormattableString> pour créer des chaînes de résultat propres à la culture :</span><span class="sxs-lookup"><span data-stu-id="3ef3f-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="3ef3f-149">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3ef3f-149">Additional resources</span></span>

<span data-ttu-id="3ef3f-150">Si vous ne connaissez pas l’interpolation de chaînes, consultez le tutoriel interactif [Interpolation de chaînes en C#](../../tutorials/exploration/interpolated-strings.yml).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="3ef3f-151">Vous pouvez également consulter un autre tutoriel sur l’[interpolation de chaîne en C#](../../tutorials/string-interpolation.md) qui montre comment utiliser des chaînes interpolées pour produire des chaînes mises en forme.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="3ef3f-152">Compilation de chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="3ef3f-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="3ef3f-153">Si une chaîne interpolée est de type `string`, elle est généralement transformée en un appel de méthode <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="3ef3f-154">Le compilateur peut remplacer <xref:System.String.Format%2A?displayProperty=nameWithType> par <xref:System.String.Concat%2A?displayProperty=nameWithType> si le comportement analysé équivaut à une concaténation.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="3ef3f-155">Si une chaîne interpolée est de type <xref:System.IFormattable> ou <xref:System.FormattableString>, le compilateur génère un appel à la méthode <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ef3f-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3ef3f-156">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3ef3f-156">C# language specification</span></span>

<span data-ttu-id="3ef3f-157">Pour plus d’informations, consultez la section [Chaînes interpolées](~/_csharplang/spec/expressions.md#interpolated-strings) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3ef3f-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ef3f-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ef3f-158">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="3ef3f-159">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="3ef3f-159">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="3ef3f-160">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="3ef3f-160">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="3ef3f-161">Chaînes</span><span class="sxs-lookup"><span data-stu-id="3ef3f-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="3ef3f-162">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3ef3f-162">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ef3f-163">Caractères spéciaux C#</span><span class="sxs-lookup"><span data-stu-id="3ef3f-163">C# Special Characters</span></span>](index.md)
- [<span data-ttu-id="3ef3f-164">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3ef3f-164">C# Reference</span></span>](../index.md)
