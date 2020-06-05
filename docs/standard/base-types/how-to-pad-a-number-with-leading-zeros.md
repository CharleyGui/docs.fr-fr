---
title: 'Procédure : remplir un nombre avec des zéros non significatifs'
description: Apprenez à remplir un nombre avec des zéros non significatifs. Ajoutez des zéros non significatifs à des entiers ou des valeurs numériques à une longueur totale spécifique ou à un nombre spécifique de zéros non significatifs.
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: 6ef0ddb37f1bc73254aa639d7c018ec6a01abd9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447184"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="5223c-104">Procédure : remplir un nombre avec des zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="5223c-104">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="5223c-105">Vous pouvez ajouter des zéros non significatifs à un entier en utilisant la [chaîne de format numérique standard](standard-numeric-format-strings.md) « D » avec un spécificateur de précision.</span><span class="sxs-lookup"><span data-stu-id="5223c-105">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="5223c-106">Vous pouvez ajouter des zéros non significatifs aux nombres entiers et à virgule flottante en utilisant une [chaîne de format numérique personnalisée](custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="5223c-106">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="5223c-107">Cet article montre comment utiliser les deux méthodes pour remplir un nombre avec des zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="5223c-107">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="5223c-108">Pour remplir un entier avec des zéros non significatifs dans la limite d'une longueur spécifique</span><span class="sxs-lookup"><span data-stu-id="5223c-108">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="5223c-109">Déterminez le nombre minimal de chiffres que la valeur entière doit afficher.</span><span class="sxs-lookup"><span data-stu-id="5223c-109">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="5223c-110">Incluez des chiffres non significatifs dans ce nombre.</span><span class="sxs-lookup"><span data-stu-id="5223c-110">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="5223c-111">Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="5223c-111">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="5223c-112">Pour afficher l’entier comme valeur décimale, appelez sa méthode `ToString(String)`, puis passez la chaîne « D*n* » comme valeur du paramètre `format`, où *n* représente la longueur minimale de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="5223c-112">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="5223c-113">Pour afficher l’entier comme valeur hexadécimale, appelez sa méthode `ToString(String)`, puis transmettez la chaîne « X*n* » comme valeur du paramètre de format, où *n* représente la longueur minimale de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="5223c-113">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="5223c-114">Vous pouvez également utiliser la chaîne de format dans une chaîne interpolée dans [C#](../../csharp/language-reference/tokens/interpolated.md) et [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), ou vous pouvez appeler une méthode, telle que <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, qui utilise la [mise en forme composite](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="5223c-114">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="5223c-115">L'exemple suivant met en forme plusieurs valeurs entières avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères.</span><span class="sxs-lookup"><span data-stu-id="5223c-115">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="5223c-116">Pour remplir un entier avec un nombre spécifique de zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="5223c-116">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="5223c-117">Déterminez le nombre de zéros non significatifs que la valeur entière doit afficher.</span><span class="sxs-lookup"><span data-stu-id="5223c-117">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="5223c-118">Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="5223c-118">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="5223c-119">Une mise en forme en tant que valeur décimale nécessite l’utilisation du spécificateur de format standard « D ».</span><span class="sxs-lookup"><span data-stu-id="5223c-119">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="5223c-120">Une mise en forme en tant que valeur hexadécimale nécessite l’utilisation du spécificateur de format standard « X ».</span><span class="sxs-lookup"><span data-stu-id="5223c-120">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="5223c-121">Déterminez la longueur de la chaîne numérique non remplie en appelant la méthode `ToString("D").Length` ou `ToString("X").Length` de la valeur entière.</span><span class="sxs-lookup"><span data-stu-id="5223c-121">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="5223c-122">Ajoutez le nombre de zéros non significatifs à inclure dans la chaîne mise en forme à la longueur de la chaîne numérique non remplie.</span><span class="sxs-lookup"><span data-stu-id="5223c-122">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="5223c-123">L’ajout du nombre de zéros non significatifs définit la longueur totale de la chaîne remplie.</span><span class="sxs-lookup"><span data-stu-id="5223c-123">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="5223c-124">Appelez la méthode `ToString(String)` de la valeur entière, puis transmettez la chaîne « D*n* » pour les chaînes décimales et la chaîne « X*n* » pour les chaînes hexadécimales, où *n* représente la longueur totale de la chaîne remplie.</span><span class="sxs-lookup"><span data-stu-id="5223c-124">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="5223c-125">Vous pouvez également utiliser la chaîne de format « D*n* » ou « X*n* » dans une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="5223c-125">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="5223c-126">L'exemple suivant remplit une valeur entière avec cinq zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="5223c-126">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="5223c-127">Pour remplir une valeur numérique avec des zéros non significatifs dans la limite d'une longueur spécifique</span><span class="sxs-lookup"><span data-stu-id="5223c-127">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="5223c-128">Déterminez le nombre de chiffres à gauche du séparateur décimal qui doivent apparaître dans la représentation du nombre sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5223c-128">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="5223c-129">Incluez des zéros non significatifs dans ce nombre total de chiffres.</span><span class="sxs-lookup"><span data-stu-id="5223c-129">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="5223c-130">Définissez une chaîne de format numérique personnalisée qui utilise l’espace réservé du zéro « 0 » pour représenter le nombre minimal de zéros.</span><span class="sxs-lookup"><span data-stu-id="5223c-130">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="5223c-131">Appelez la méthode `ToString(String)` du nombre et transmettez-lui la chaîne de format personnalisée.</span><span class="sxs-lookup"><span data-stu-id="5223c-131">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="5223c-132">Vous pouvez également utiliser la chaîne de format personnalisée avec l’interpolation de chaîne ou avec une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="5223c-132">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="5223c-133">L’exemple suivant met en forme plusieurs valeurs numériques avec des zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="5223c-133">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="5223c-134">Par conséquent, la longueur totale du nombre mis en forme est de huit chiffres minimum à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="5223c-134">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="5223c-135">Pour remplir une valeur numérique avec un nombre spécifique de zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="5223c-135">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="5223c-136">Déterminez le nombre de zéros non significatifs que la valeur numérique doit avoir.</span><span class="sxs-lookup"><span data-stu-id="5223c-136">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="5223c-137">Déterminez le nombre de chiffres à gauche du séparateur décimal dans la chaîne numérique non remplie :</span><span class="sxs-lookup"><span data-stu-id="5223c-137">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="5223c-138">Déterminez si la représentation sous forme de chaîne d'un nombre comprend un séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="5223c-138">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="5223c-139">Si tel est le cas, déterminez le nombre de caractères à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="5223c-139">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="5223c-140">-ou-</span><span class="sxs-lookup"><span data-stu-id="5223c-140">-or-</span></span>

         <span data-ttu-id="5223c-141">Sinon, déterminez la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="5223c-141">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="5223c-142">Créez une chaîne de format personnalisée qui utilise :</span><span class="sxs-lookup"><span data-stu-id="5223c-142">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="5223c-143">L’espace réservé du zéro « 0 » pour chaque zéro non significatif qui apparaît dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="5223c-143">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="5223c-144">L’espace réservé du zéro ou l’espace réservé de chiffre « # » pour représenter chaque chiffre dans la chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="5223c-144">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="5223c-145">Fournissez la chaîne de format personnalisée comme paramètre à la méthode `ToString(String)` du nombre ou à une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="5223c-145">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="5223c-146">L'exemple suivant remplit deux valeurs <xref:System.Double> avec cinq zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="5223c-146">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="5223c-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5223c-147">See also</span></span>

- [<span data-ttu-id="5223c-148">Chaînes de format numériques personnalisées</span><span class="sxs-lookup"><span data-stu-id="5223c-148">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="5223c-149">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="5223c-149">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="5223c-150">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="5223c-150">Composite Formatting</span></span>](composite-formatting.md)
