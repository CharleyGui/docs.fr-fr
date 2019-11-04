---
title: Tableau des formats des résultats numériques - Référence C#
ms.custom: seodec18
description: En savoir plus sur les chaînes de format numériques standard C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 2cba5e704787ae6368b2543c985babf2fde3b4dd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422752"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="c49e0-103">Tableau des formats des résultats numériques (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c49e0-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="c49e0-104">Le tableau suivant montre les spécificateurs de format pris en charge pour la mise en forme des résultats numériques.</span><span class="sxs-lookup"><span data-stu-id="c49e0-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="c49e0-105">Le résultat mis en forme dans la dernière colonne correspond à « en-US » <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="c49e0-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="c49e0-106">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="c49e0-106">Format specifier</span></span>|<span data-ttu-id="c49e0-107">Description</span><span class="sxs-lookup"><span data-stu-id="c49e0-107">Description</span></span>|<span data-ttu-id="c49e0-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="c49e0-108">Examples</span></span>|<span data-ttu-id="c49e0-109">Résultat</span><span class="sxs-lookup"><span data-stu-id="c49e0-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="c49e0-110">C ou c</span><span class="sxs-lookup"><span data-stu-id="c49e0-110">C or c</span></span>|<span data-ttu-id="c49e0-111">Devise</span><span class="sxs-lookup"><span data-stu-id="c49e0-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="c49e0-112">$2.50</span><span class="sxs-lookup"><span data-stu-id="c49e0-112">$2.50</span></span><br /><br /> <span data-ttu-id="c49e0-113">($2.50)</span><span class="sxs-lookup"><span data-stu-id="c49e0-113">($2.50)</span></span>|  
|<span data-ttu-id="c49e0-114">D ou d</span><span class="sxs-lookup"><span data-stu-id="c49e0-114">D or d</span></span>|<span data-ttu-id="c49e0-115">Decimal</span><span class="sxs-lookup"><span data-stu-id="c49e0-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="c49e0-116">00025</span><span class="sxs-lookup"><span data-stu-id="c49e0-116">00025</span></span>|  
|<span data-ttu-id="c49e0-117">E ou e</span><span class="sxs-lookup"><span data-stu-id="c49e0-117">E or e</span></span>|<span data-ttu-id="c49e0-118">Exponentiel</span><span class="sxs-lookup"><span data-stu-id="c49e0-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="c49e0-119">2.50E+005</span><span class="sxs-lookup"><span data-stu-id="c49e0-119">2.50E+005</span></span>|  
|<span data-ttu-id="c49e0-120">F ou f</span><span class="sxs-lookup"><span data-stu-id="c49e0-120">F or f</span></span>|<span data-ttu-id="c49e0-121">Virgule fixe</span><span class="sxs-lookup"><span data-stu-id="c49e0-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="c49e0-122">2.50</span><span class="sxs-lookup"><span data-stu-id="c49e0-122">2.50</span></span><br /><br /> <span data-ttu-id="c49e0-123">3</span><span class="sxs-lookup"><span data-stu-id="c49e0-123">3</span></span>|  
|<span data-ttu-id="c49e0-124">G ou g</span><span class="sxs-lookup"><span data-stu-id="c49e0-124">G or g</span></span>|<span data-ttu-id="c49e0-125">Général</span><span class="sxs-lookup"><span data-stu-id="c49e0-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="c49e0-126">2,5</span><span class="sxs-lookup"><span data-stu-id="c49e0-126">2.5</span></span>|  
|<span data-ttu-id="c49e0-127">N ou n</span><span class="sxs-lookup"><span data-stu-id="c49e0-127">N or n</span></span>|<span data-ttu-id="c49e0-128">Numérique</span><span class="sxs-lookup"><span data-stu-id="c49e0-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="c49e0-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="c49e0-129">2,500,000.00</span></span>|  
|<span data-ttu-id="c49e0-130">P ou p</span><span class="sxs-lookup"><span data-stu-id="c49e0-130">P or p</span></span>|<span data-ttu-id="c49e0-131">Pourcentage</span><span class="sxs-lookup"><span data-stu-id="c49e0-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="c49e0-132">25.00%</span><span class="sxs-lookup"><span data-stu-id="c49e0-132">25.00%</span></span>|  
|<span data-ttu-id="c49e0-133">R ou r</span><span class="sxs-lookup"><span data-stu-id="c49e0-133">R or r</span></span>|<span data-ttu-id="c49e0-134">Aller-retour</span><span class="sxs-lookup"><span data-stu-id="c49e0-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="c49e0-135">2,5</span><span class="sxs-lookup"><span data-stu-id="c49e0-135">2.5</span></span>|  
|<span data-ttu-id="c49e0-136">X ou x</span><span class="sxs-lookup"><span data-stu-id="c49e0-136">X or x</span></span>|<span data-ttu-id="c49e0-137">Hexadécimal</span><span class="sxs-lookup"><span data-stu-id="c49e0-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="c49e0-138">FA</span><span class="sxs-lookup"><span data-stu-id="c49e0-138">FA</span></span><br /><br /> <span data-ttu-id="c49e0-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="c49e0-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="c49e0-140">Notes</span><span class="sxs-lookup"><span data-stu-id="c49e0-140">Remarks</span></span>

<span data-ttu-id="c49e0-141">Vous utilisez un spécificateur de format pour créer une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="c49e0-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="c49e0-142">La chaîne de format est au format suivant : `Axx`, où</span><span class="sxs-lookup"><span data-stu-id="c49e0-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="c49e0-143">`A` est le spécificateur de format, qui contrôle le type de mise en forme appliquée à la valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="c49e0-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="c49e0-144">`xx` est le spécificateur de précision, qui affecte le nombre de chiffres dans la sortie mise en forme.</span><span class="sxs-lookup"><span data-stu-id="c49e0-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="c49e0-145">La valeur du spécificateur de précision est comprise entre 0 et 99.</span><span class="sxs-lookup"><span data-stu-id="c49e0-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="c49e0-146">Les spécificateurs de format décimal (« D » ou « d ») et de format hexadécimal (« X » ou « x ») sont pris en charge uniquement pour les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="c49e0-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="c49e0-147">Le spécificateur de format aller-retour (« R » ou « r ») est pris en charge uniquement pour les types <xref:System.Single>, <xref:System.Double> et <xref:System.Numerics.BigInteger>.</span><span class="sxs-lookup"><span data-stu-id="c49e0-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="c49e0-148">Les chaînes de format numériques standard sont prises en charge par :</span><span class="sxs-lookup"><span data-stu-id="c49e0-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="c49e0-149">Certaines surcharges de la méthode `ToString` de tous les types numériques.</span><span class="sxs-lookup"><span data-stu-id="c49e0-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="c49e0-150">Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> et <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c49e0-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="c49e0-151">La [fonctionnalité de mise en forme composite](../../../standard/base-types/composite-formatting.md) de .NET, qui est prise en charge par la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>, par exemple.</span><span class="sxs-lookup"><span data-stu-id="c49e0-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="c49e0-152">[Chaînes interpolées](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="c49e0-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="c49e0-153">Pour plus d’informations, consultez [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="c49e0-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c49e0-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c49e0-154">See also</span></span>

- [<span data-ttu-id="c49e0-155">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="c49e0-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c49e0-156">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c49e0-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c49e0-157">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="c49e0-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="c49e0-158">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="c49e0-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="c49e0-159">Interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="c49e0-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="c49e0-160">string</span><span class="sxs-lookup"><span data-stu-id="c49e0-160">string</span></span>](../builtin-types/reference-types.md)
