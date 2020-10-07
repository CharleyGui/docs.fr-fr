---
title: Chaînes interpolées
ms.date: 10/31/2017
ms.openlocfilehash: c427b48ce58a59ff3878f24f1989db6ac8c8239a
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805276"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="4dc1d-102">Chaînes interpolées (référence Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dc1d-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="4dc1d-103">Permettent de construire des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-103">Used to construct strings.</span></span>  <span data-ttu-id="4dc1d-104">Une chaîne interpolée ressemble à une chaîne de modèle contenant des *expressions interpolées*.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="4dc1d-105">Une chaîne interpolée retourne une chaîne qui remplace les expressions interpolées qu’elle contient par leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="4dc1d-106">Cette fonctionnalité est disponible dans Visual Basic 14 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="4dc1d-107">Les arguments d’une chaîne interpolée sont plus faciles à comprendre qu’une [chaîne de format composite](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="4dc1d-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="4dc1d-108">Par exemple, la chaîne interpolée</span><span class="sxs-lookup"><span data-stu-id="4dc1d-108">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="4dc1d-109">contient deux expressions interpolées, ’{name}’ et ’{hours:hh}’.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="4dc1d-110">La chaîne de format composite équivalente est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

<span data-ttu-id="4dc1d-111">La structure d’une chaîne interpolée est :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-111">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="4dc1d-112">où :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-112">where:</span></span>

- <span data-ttu-id="4dc1d-113">*field-width* est un entier signé qui indique le nombre de caractères du champ.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="4dc1d-114">S’il est positif, le champ est aligné à droite ; s’il est négatif, il est aligné à gauche.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="4dc1d-115">*format-string* est une chaîne de format qui convient au type d’objet mis en forme.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="4dc1d-116">Par exemple, pour une <xref:System.DateTime> valeur, il peut s’agir d’une [chaîne de format de date et d’heure standard](../../../../standard/base-types/standard-date-and-time-format-strings.md) telle que « d » ou « d ».</span><span class="sxs-lookup"><span data-stu-id="4dc1d-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4dc1d-117">N’ajoutez pas d’espace blanc entre les signes `$` et `"` au début de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="4dc1d-118">Cela provoque une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-118">Doing so causes a compiler error.</span></span>

<span data-ttu-id="4dc1d-119">Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="4dc1d-120">La chaîne interpolée est évaluée à chaque exécution du code contenant la chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="4dc1d-121">Cela vous permet de séparer la définition et l’évaluation d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="4dc1d-122">Pour ajouter une accolade ("{" ou "}") dans une chaîne interpolée, utilisez deux accolades "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="4dc1d-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="4dc1d-123">Pour plus d’informations, consultez la section « Conversions implicites ».</span><span class="sxs-lookup"><span data-stu-id="4dc1d-123">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="4dc1d-124">Si la chaîne interpolée contient d’autres caractères ayant une signification particulière dans une chaîne interpolée, comme le guillemet ("), les deux-points (:) ou la virgule (,), ils doivent être échappés s’ils se trouvent dans du texte littéral, ou être inclus dans une expression délimitée par des parenthèses s’ils s’agit d’éléments de langage inclus dans une expression interpolée.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="4dc1d-125">L’exemple suivant échappe les guillemets pour les inclure dans la chaîne de résultat :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-125">The following example escapes quotation marks to include them in the result string:</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="4dc1d-126">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="4dc1d-126">Implicit Conversions</span></span>

<span data-ttu-id="4dc1d-127">Trois conversions de type implicite sont possibles à partir d’une chaîne interpolée :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-127">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="4dc1d-128">La conversion d’une chaîne interpolée en un <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="4dc1d-129">L’exemple suivant retourne une chaîne dont les expressions de chaîne interpolée ont été remplacées par leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="4dc1d-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="4dc1d-131">Il s’agit du résultat final d’une interprétation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="4dc1d-132">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont converties en une seule accolade.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="4dc1d-133">La conversion d’une chaîne interpolée en variable <xref:System.IFormattable> qui permet de créer plusieurs chaînes de résultats avec un contenu spécifique de la culture, à partir d’une seule instance <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="4dc1d-134">Ce type de conversion est utile pour inclure des éléments, tels que les formats numériques et les formats de date adaptés à une culture.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="4dc1d-135">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées tant que vous ne mettez pas en forme la chaîne en appelant explicitement ou implicitement la méthode <xref:System.Object.ToString>.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="4dc1d-136">Toutes les expressions d’interpolation contenues sont converties en {0} , {1} , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="4dc1d-137">L’exemple suivant utilise la réflexion pour afficher les membres ainsi que les valeurs de champ et de propriété d’une variable <xref:System.IFormattable> créée à partir d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="4dc1d-138">Il passe également la variable <xref:System.IFormattable> à la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="4dc1d-139">Notez que la chaîne interpolée ne peut être inspectée qu’à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="4dc1d-140">Si elle est passée à une méthode de mise en forme de chaîne, telle que <xref:System.Console.WriteLine(System.String)>, ses éléments de mise en forme sont résolus et la chaîne de résultat est retournée.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="4dc1d-141">Conversion d’une chaîne interpolée en une <xref:System.FormattableString> variable qui représente une chaîne de format composite.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="4dc1d-142">L’inspection de la chaîne de format composite et de son rendu sous forme de chaîne de résultat, peut, par exemple, vous aider à réduire les risques d’attaque par injection pendant la création d’une requête.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="4dc1d-143">Un <xref:System.FormattableString> comprend également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="4dc1d-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="4dc1d-144">Une surcharge <xref:System.FormattableString.ToString> qui produit une chaîne de résultat pour <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="4dc1d-145"><xref:System.FormattableString.Invariant%2A>Méthode qui produit une chaîne pour <xref:System.Globalization.CultureInfo.InvariantCulture> .</span><span class="sxs-lookup"><span data-stu-id="4dc1d-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="4dc1d-146">Une méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> qui produit une chaîne de résultat pour une culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="4dc1d-147">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées sous la forme d’accolades doubles jusqu’à ce que vous le formatiez.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="4dc1d-148">Toutes les expressions d’interpolation contenues sont converties en {0} , {1} , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="4dc1d-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="4dc1d-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dc1d-149">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="4dc1d-150">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dc1d-150">Visual Basic Language Reference</span></span>](index.md)
