---
title: Interpolation de chaîne en C#
description: Découvrez comment inclure des résultats d’expressions mises en forme dans une chaîne de résultat en C# avec une interpolation de chaîne.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 068a30bdcb96140787a38e9ae52f9c62d8a57c96
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063226"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="e6908-103">Interpolation de chaîne en C\#</span><span class="sxs-lookup"><span data-stu-id="e6908-103">String interpolation in C\#</span></span>

<span data-ttu-id="e6908-104">Ce tutoriel vous montre comment utiliser une [interpolation de chaîne](../language-reference/tokens/interpolated.md) pour mettre en forme et inclure des résultats d’expressions dans une chaîne de résultat.</span><span class="sxs-lookup"><span data-stu-id="e6908-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="e6908-105">Les exemples supposent que vous êtes familiarisé avec les concepts de base de C# et la mise en forme des types .NET.</span><span class="sxs-lookup"><span data-stu-id="e6908-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="e6908-106">Si vous ne connaissez pas l’interpolation de chaînes ou la mise en forme de types .NET, consultez d’abord le [tutoriel interactif sur l’interpolation de chaînes](exploration/interpolated-strings.yml).</span><span class="sxs-lookup"><span data-stu-id="e6908-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="e6908-107">Pour plus d’informations sur la mise en forme des types dans .NET, consultez la rubrique [Mise en forme des types dans .NET](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="e6908-108">Introduction</span><span class="sxs-lookup"><span data-stu-id="e6908-108">Introduction</span></span>

<span data-ttu-id="e6908-109">La fonctionnalité [Interpolation de chaîne](../language-reference/tokens/interpolated.md) s’appuie sur la fonctionnalité [Mise en forme composite](../../standard/base-types/composite-formatting.md) et fournit une syntaxe plus lisible et plus pratique pour inclure des résultats d’expressions mises en forme dans une chaîne de résultat.</span><span class="sxs-lookup"><span data-stu-id="e6908-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="e6908-110">Pour identifier un littéral de chaîne comme chaîne interpolée, préfixez-la du symbole `$`.</span><span class="sxs-lookup"><span data-stu-id="e6908-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="e6908-111">Vous pouvez incorporer n’importe quelle expression C# valide qui retourne une valeur dans une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="e6908-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="e6908-112">Dans l’exemple suivant, dès qu’une expression est évaluée, son résultat est converti en chaîne et est inclus dans une chaîne de résultat :</span><span class="sxs-lookup"><span data-stu-id="e6908-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="e6908-113">Comme le montre l’exemple, vous incluez une expression dans une chaîne interpolée en la plaçant entre des accolades :</span><span class="sxs-lookup"><span data-stu-id="e6908-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="e6908-114">Les chaînes interpolées prennent en charge toutes les fonctions de la fonctionnalité [Mise en forme de chaîne composite](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="e6908-115">Elles constituent ainsi une alternative plus lisible à l’utilisation de la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6908-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="e6908-116">Comment spécifier une chaîne de format pour une expression interpolée</span><span class="sxs-lookup"><span data-stu-id="e6908-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="e6908-117">Vous spécifiez une chaîne de format prise en charge par le type du résultat d’expression en plaçant un signe deux-points (« : ») et la chaîne de format après l’expression interpolée :</span><span class="sxs-lookup"><span data-stu-id="e6908-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="e6908-118">L’exemple suivant montre comment spécifier des chaînes de format standard et personnalisées pour des expressions qui produisent des résultats de type date/heure ou numérique :</span><span class="sxs-lookup"><span data-stu-id="e6908-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="e6908-119">Pour plus d’informations, consultez la section [Composant de chaîne de format](../../standard/base-types/composite-formatting.md#format-string-component) de la rubrique [Mise en forme composite](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="e6908-120">Cette section fournit des liens vers les rubriques qui décrivent les chaînes de format standard et personnalisées prises en charge par les types de base .NET.</span><span class="sxs-lookup"><span data-stu-id="e6908-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="e6908-121">Comment contrôler la largeur de champ et l’alignement de l’expression interpolée mise en forme</span><span class="sxs-lookup"><span data-stu-id="e6908-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="e6908-122">Vous spécifiez la largeur minimale du champ et l’alignement du résultat d’expression mise en forme en plaçant une virgule («, ») et l’expression de constante à la fin de l’expression interpolée :</span><span class="sxs-lookup"><span data-stu-id="e6908-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="e6908-123">Si la valeur de *l’alignement* est positive, le résultat de l’expression mise en forme est aligné à droite ; si la valeur est négative, il est aligné à gauche.</span><span class="sxs-lookup"><span data-stu-id="e6908-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="e6908-124">Si vous devez spécifier à la fois un alignement et une chaîne de format, commencez par le composant d’alignement :</span><span class="sxs-lookup"><span data-stu-id="e6908-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="e6908-125">L’exemple suivant montre comment spécifier l’alignement ; il utilise des caractères de barre verticale (« | ») pour délimiter les champs texte :</span><span class="sxs-lookup"><span data-stu-id="e6908-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="e6908-126">Comme le montre l’exemple de sortie, si la longueur du résultat d’expression mise en forme dépasse la largeur de champ spécifiée, la valeur de *l’alignement* est ignorée.</span><span class="sxs-lookup"><span data-stu-id="e6908-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="e6908-127">Pour plus d’informations, consultez la section [Composant d’alignement](../../standard/base-types/composite-formatting.md#alignment-component) de la rubrique [Mise en forme composite](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="e6908-128">Comment utiliser des séquences d’échappement dans une chaîne interpolée</span><span class="sxs-lookup"><span data-stu-id="e6908-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="e6908-129">Les chaînes interpolées prennent en charge toutes les séquences d’échappement qui peuvent être utilisés dans les littéraux de chaîne ordinaires.</span><span class="sxs-lookup"><span data-stu-id="e6908-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="e6908-130">Pour plus d’informations, consultez [Séquences d’échappement de chaîne](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="e6908-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="e6908-131">Pour interpréter les séquences d’échappement littéralement, utilisez un littéral de chaîne [textuelle](../language-reference/tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="e6908-132">Une chaîne interpolée textuelle commence par le caractère `$` suivi du caractère `@`.</span><span class="sxs-lookup"><span data-stu-id="e6908-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="e6908-133">Pour inclure une accolade, « { » ou «} », dans une chaîne de résultat, utilisez deux accolades, « {{ » ou «}} ».</span><span class="sxs-lookup"><span data-stu-id="e6908-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="e6908-134">Pour plus d’informations, consultez la section [Échappement des accolades](../../standard/base-types/composite-formatting.md#escaping-braces) de la rubrique [Mise en forme composite](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="e6908-135">L’exemple suivant montre comment inclure des accolades dans une chaîne de résultat et construire une chaîne interpolée textuelle :</span><span class="sxs-lookup"><span data-stu-id="e6908-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="e6908-136">Comment utiliser un opérateur conditionnel ternaire `?:` dans une expression interpolée</span><span class="sxs-lookup"><span data-stu-id="e6908-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="e6908-137">Comme le caractère deux-points (« : ») a une signification spéciale dans un élément avec une expression interpolée, pour utiliser un [opérateur conditionnel](../language-reference/operators/conditional-operator.md) dans une expression, placez-le entre parenthèses, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e6908-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="e6908-138">Comment créer une chaîne de résultat spécifique à une culture avec une interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="e6908-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="e6908-139">Par défaut, une chaîne interpolée utilise la culture active définie par la propriété <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> pour toutes les opérations de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e6908-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="e6908-140">Utilisez la conversion implicite d’une chaîne interpolée en une instance de <xref:System.FormattableString?displayProperty=nameWithType> et appelez sa méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> pour créer une chaîne de résultat spécifique à une culture.</span><span class="sxs-lookup"><span data-stu-id="e6908-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="e6908-141">L’exemple suivant montre comment effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="e6908-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="e6908-142">Comme le montre l’exemple, vous pouvez utiliser une même instance de <xref:System.FormattableString> pour générer plusieurs chaînes de résultat pour différentes cultures.</span><span class="sxs-lookup"><span data-stu-id="e6908-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="e6908-143">Comment créer une chaîne de résultat avec la culture invariante</span><span class="sxs-lookup"><span data-stu-id="e6908-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="e6908-144">Avec la méthode <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>, vous pouvez utiliser la méthode statique <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> pour résoudre une chaîne interpolée en une chaîne de résultat pour <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="e6908-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="e6908-145">L’exemple suivant montre comment effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="e6908-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="e6908-146">Conclusion</span><span class="sxs-lookup"><span data-stu-id="e6908-146">Conclusion</span></span>

<span data-ttu-id="e6908-147">Ce tutoriel décrit des scénarios courants d’utilisation de l’interpolation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e6908-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="e6908-148">Pour plus d’informations sur l’interpolation de chaîne, consultez la rubrique [Interpolation de chaîne](../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="e6908-149">Pour plus d’informations sur la mise en forme des types dans .NET, consultez les rubriques [Mise en forme des types dans .NET](../../standard/base-types/formatting-types.md) et [Mise en forme composite](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e6908-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6908-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6908-150">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="e6908-151">Chaînes</span><span class="sxs-lookup"><span data-stu-id="e6908-151">Strings</span></span>](../programming-guide/strings/index.md)
