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
ms.openlocfilehash: 853faf481e546f2980d799d5daf50a14c608c052
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345470"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="147a5-103">Tableau des formats des résultats numériques (référence C#)</span><span class="sxs-lookup"><span data-stu-id="147a5-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="147a5-104">Le tableau suivant montre les spécificateurs de format pris en charge pour la mise en forme des résultats numériques.</span><span class="sxs-lookup"><span data-stu-id="147a5-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="147a5-105">Le résultat mis en forme dans la dernière colonne correspond à « en-US » <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="147a5-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="147a5-106">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="147a5-106">Format specifier</span></span>|<span data-ttu-id="147a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="147a5-107">Description</span></span>|<span data-ttu-id="147a5-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="147a5-108">Examples</span></span>|<span data-ttu-id="147a5-109">Résultat</span><span class="sxs-lookup"><span data-stu-id="147a5-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="147a5-110">C ou c</span><span class="sxs-lookup"><span data-stu-id="147a5-110">C or c</span></span>|<span data-ttu-id="147a5-111">Devise</span><span class="sxs-lookup"><span data-stu-id="147a5-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="147a5-112">\\$2,50</span><span class="sxs-lookup"><span data-stu-id="147a5-112">\\$2.50</span></span><br /><br /> <span data-ttu-id="147a5-113">(\\$2,50)</span><span class="sxs-lookup"><span data-stu-id="147a5-113">(\\$2.50)</span></span>|  
|<span data-ttu-id="147a5-114">D ou d</span><span class="sxs-lookup"><span data-stu-id="147a5-114">D or d</span></span>|<span data-ttu-id="147a5-115">Decimal</span><span class="sxs-lookup"><span data-stu-id="147a5-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="147a5-116">00025</span><span class="sxs-lookup"><span data-stu-id="147a5-116">00025</span></span>|  
|<span data-ttu-id="147a5-117">E ou e</span><span class="sxs-lookup"><span data-stu-id="147a5-117">E or e</span></span>|<span data-ttu-id="147a5-118">Exponentiel</span><span class="sxs-lookup"><span data-stu-id="147a5-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="147a5-119">2.50E+005</span><span class="sxs-lookup"><span data-stu-id="147a5-119">2.50E+005</span></span>|  
|<span data-ttu-id="147a5-120">F ou f</span><span class="sxs-lookup"><span data-stu-id="147a5-120">F or f</span></span>|<span data-ttu-id="147a5-121">Virgule fixe</span><span class="sxs-lookup"><span data-stu-id="147a5-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="147a5-122">2.50</span><span class="sxs-lookup"><span data-stu-id="147a5-122">2.50</span></span><br /><br /> <span data-ttu-id="147a5-123">3</span><span class="sxs-lookup"><span data-stu-id="147a5-123">3</span></span>|  
|<span data-ttu-id="147a5-124">G ou g</span><span class="sxs-lookup"><span data-stu-id="147a5-124">G or g</span></span>|<span data-ttu-id="147a5-125">Général</span><span class="sxs-lookup"><span data-stu-id="147a5-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="147a5-126">2,5</span><span class="sxs-lookup"><span data-stu-id="147a5-126">2.5</span></span>|  
|<span data-ttu-id="147a5-127">N ou n</span><span class="sxs-lookup"><span data-stu-id="147a5-127">N or n</span></span>|<span data-ttu-id="147a5-128">Numérique</span><span class="sxs-lookup"><span data-stu-id="147a5-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="147a5-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="147a5-129">2,500,000.00</span></span>|  
|<span data-ttu-id="147a5-130">P ou p</span><span class="sxs-lookup"><span data-stu-id="147a5-130">P or p</span></span>|<span data-ttu-id="147a5-131">Pourcentage</span><span class="sxs-lookup"><span data-stu-id="147a5-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="147a5-132">25.00%</span><span class="sxs-lookup"><span data-stu-id="147a5-132">25.00%</span></span>|  
|<span data-ttu-id="147a5-133">R ou r</span><span class="sxs-lookup"><span data-stu-id="147a5-133">R or r</span></span>|<span data-ttu-id="147a5-134">Aller-retour</span><span class="sxs-lookup"><span data-stu-id="147a5-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="147a5-135">2,5</span><span class="sxs-lookup"><span data-stu-id="147a5-135">2.5</span></span>|  
|<span data-ttu-id="147a5-136">X ou x</span><span class="sxs-lookup"><span data-stu-id="147a5-136">X or x</span></span>|<span data-ttu-id="147a5-137">Hexadécimal</span><span class="sxs-lookup"><span data-stu-id="147a5-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="147a5-138">FA</span><span class="sxs-lookup"><span data-stu-id="147a5-138">FA</span></span><br /><br /> <span data-ttu-id="147a5-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="147a5-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="147a5-140">Notes</span><span class="sxs-lookup"><span data-stu-id="147a5-140">Remarks</span></span>

<span data-ttu-id="147a5-141">Vous utilisez un spécificateur de format pour créer une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="147a5-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="147a5-142">La chaîne de format est au format suivant : `Axx`, où</span><span class="sxs-lookup"><span data-stu-id="147a5-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="147a5-143">`A` est le spécificateur de format, qui contrôle le type de mise en forme appliquée à la valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="147a5-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="147a5-144">`xx` est le spécificateur de précision, qui affecte le nombre de chiffres dans la sortie mise en forme.</span><span class="sxs-lookup"><span data-stu-id="147a5-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="147a5-145">La valeur du spécificateur de précision est comprise entre 0 et 99.</span><span class="sxs-lookup"><span data-stu-id="147a5-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="147a5-146">Les spécificateurs de format décimal (« D » ou « d ») et de format hexadécimal (« X » ou « x ») sont pris en charge uniquement pour les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="147a5-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="147a5-147">Le spécificateur de format aller-retour (« R » ou « r ») est pris en charge uniquement pour les types <xref:System.Single>, <xref:System.Double> et <xref:System.Numerics.BigInteger>.</span><span class="sxs-lookup"><span data-stu-id="147a5-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="147a5-148">Les chaînes de format numériques standard sont prises en charge par :</span><span class="sxs-lookup"><span data-stu-id="147a5-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="147a5-149">Certaines surcharges de la méthode `ToString` de tous les types numériques.</span><span class="sxs-lookup"><span data-stu-id="147a5-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="147a5-150">Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> et <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="147a5-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="147a5-151">La [fonctionnalité de mise en forme composite](../../../standard/base-types/composite-formatting.md) de .NET, qui est prise en charge par la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>, par exemple.</span><span class="sxs-lookup"><span data-stu-id="147a5-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="147a5-152">[Chaînes interpolées](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="147a5-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="147a5-153">Pour plus d’informations, consultez [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="147a5-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="147a5-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="147a5-154">See also</span></span>

- [<span data-ttu-id="147a5-155">Référence C#</span><span class="sxs-lookup"><span data-stu-id="147a5-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="147a5-156">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="147a5-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="147a5-157">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="147a5-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="147a5-158">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="147a5-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="147a5-159">Interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="147a5-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="147a5-160">string</span><span class="sxs-lookup"><span data-stu-id="147a5-160">string</span></span>](../builtin-types/reference-types.md)
