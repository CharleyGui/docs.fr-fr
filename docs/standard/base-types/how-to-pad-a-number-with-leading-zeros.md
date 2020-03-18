---
title: 'Comment : remplir un nombre avec des zéros non significatifs'
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
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131976"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="97d9c-102">Comment : remplir un nombre avec des zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="97d9c-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="97d9c-103">Vous pouvez ajouter des zéros non significatifs à un entier en utilisant la [chaîne de format numérique standard](../../../docs/standard/base-types/standard-numeric-format-strings.md) « D » avec un spécificateur de précision.</span><span class="sxs-lookup"><span data-stu-id="97d9c-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="97d9c-104">Vous pouvez ajouter des zéros non significatifs aux nombres entiers et à virgule flottante en utilisant une [chaîne de format numérique personnalisée](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="97d9c-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="97d9c-105">Cet article montre comment utiliser les deux méthodes pour remplir un nombre avec des zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="97d9c-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="97d9c-106">Pour remplir un entier avec des zéros non significatifs dans la limite d'une longueur spécifique</span><span class="sxs-lookup"><span data-stu-id="97d9c-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="97d9c-107">Déterminez le nombre minimal de chiffres que la valeur entière doit afficher.</span><span class="sxs-lookup"><span data-stu-id="97d9c-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="97d9c-108">Incluez des chiffres non significatifs dans ce nombre.</span><span class="sxs-lookup"><span data-stu-id="97d9c-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="97d9c-109">Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="97d9c-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="97d9c-110">Pour afficher l’entier comme valeur décimale, appelez sa méthode `ToString(String)`, puis passez la chaîne « D*n* » comme valeur du paramètre `format`, où *n* représente la longueur minimale de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d9c-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="97d9c-111">Pour afficher l’entier comme valeur hexadécimale, appelez sa méthode `ToString(String)`, puis transmettez la chaîne « X*n* » comme valeur du paramètre de format, où *n* représente la longueur minimale de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d9c-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="97d9c-112">Vous pouvez également utiliser la chaîne de format dans une chaîne interpolée dans [C#](../../csharp/language-reference/tokens/interpolated.md) et [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), ou vous pouvez appeler une méthode, telle que <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, qui utilise la [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="97d9c-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>

<span data-ttu-id="97d9c-113">L'exemple suivant met en forme plusieurs valeurs entières avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères.</span><span class="sxs-lookup"><span data-stu-id="97d9c-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="97d9c-114">Pour remplir un entier avec un nombre spécifique de zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="97d9c-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="97d9c-115">Déterminez le nombre de zéros non significatifs que la valeur entière doit afficher.</span><span class="sxs-lookup"><span data-stu-id="97d9c-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="97d9c-116">Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="97d9c-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="97d9c-117">Une mise en forme en tant que valeur décimale nécessite l’utilisation du spécificateur de format standard « D ».</span><span class="sxs-lookup"><span data-stu-id="97d9c-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="97d9c-118">Une mise en forme en tant que valeur hexadécimale nécessite l’utilisation du spécificateur de format standard « X ».</span><span class="sxs-lookup"><span data-stu-id="97d9c-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="97d9c-119">Déterminez la longueur de la chaîne numérique non remplie en appelant la méthode `ToString("D").Length` ou `ToString("X").Length` de la valeur entière.</span><span class="sxs-lookup"><span data-stu-id="97d9c-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="97d9c-120">Ajoutez le nombre de zéros non significatifs à inclure dans la chaîne mise en forme à la longueur de la chaîne numérique non remplie.</span><span class="sxs-lookup"><span data-stu-id="97d9c-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="97d9c-121">L’ajout du nombre de zéros non significatifs définit la longueur totale de la chaîne remplie.</span><span class="sxs-lookup"><span data-stu-id="97d9c-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="97d9c-122">Appelez la méthode `ToString(String)` de la valeur entière, puis transmettez la chaîne « D*n* » pour les chaînes décimales et la chaîne « X*n* » pour les chaînes hexadécimales, où *n* représente la longueur totale de la chaîne remplie.</span><span class="sxs-lookup"><span data-stu-id="97d9c-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="97d9c-123">Vous pouvez également utiliser la chaîne de format « D*n* » ou « X*n* » dans une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="97d9c-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="97d9c-124">L'exemple suivant remplit une valeur entière avec cinq zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="97d9c-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="97d9c-125">Pour remplir une valeur numérique avec des zéros non significatifs dans la limite d'une longueur spécifique</span><span class="sxs-lookup"><span data-stu-id="97d9c-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="97d9c-126">Déterminez le nombre de chiffres à gauche du séparateur décimal qui doivent apparaître dans la représentation du nombre sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d9c-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="97d9c-127">Incluez des zéros non significatifs dans ce nombre total de chiffres.</span><span class="sxs-lookup"><span data-stu-id="97d9c-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="97d9c-128">Définissez une chaîne de format numérique personnalisée qui utilise l’espace réservé du zéro « 0 » pour représenter le nombre minimal de zéros.</span><span class="sxs-lookup"><span data-stu-id="97d9c-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="97d9c-129">Appelez la méthode `ToString(String)` du nombre et transmettez-lui la chaîne de format personnalisée.</span><span class="sxs-lookup"><span data-stu-id="97d9c-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="97d9c-130">Vous pouvez également utiliser la chaîne de format personnalisée avec l’interpolation de chaîne ou avec une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="97d9c-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="97d9c-131">L’exemple suivant met en forme plusieurs valeurs numériques avec des zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="97d9c-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="97d9c-132">Par conséquent, la longueur totale du nombre mis en forme est de huit chiffres minimum à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="97d9c-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="97d9c-133">Pour remplir une valeur numérique avec un nombre spécifique de zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="97d9c-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="97d9c-134">Déterminez le nombre de zéros non significatifs que la valeur numérique doit avoir.</span><span class="sxs-lookup"><span data-stu-id="97d9c-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="97d9c-135">Déterminez le nombre de chiffres à gauche du séparateur décimal dans la chaîne numérique non remplie :</span><span class="sxs-lookup"><span data-stu-id="97d9c-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="97d9c-136">Déterminez si la représentation sous forme de chaîne d'un nombre comprend un séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="97d9c-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="97d9c-137">Si tel est le cas, déterminez le nombre de caractères à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="97d9c-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="97d9c-138">-ou-</span><span class="sxs-lookup"><span data-stu-id="97d9c-138">-or-</span></span>

         <span data-ttu-id="97d9c-139">Sinon, déterminez la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d9c-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="97d9c-140">Créez une chaîne de format personnalisée qui utilise :</span><span class="sxs-lookup"><span data-stu-id="97d9c-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="97d9c-141">L’espace réservé du zéro « 0 » pour chaque zéro non significatif qui apparaît dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d9c-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="97d9c-142">L’espace réservé du zéro ou l’espace réservé de chiffre « # » pour représenter chaque chiffre dans la chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="97d9c-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="97d9c-143">Fournissez la chaîne de format personnalisée comme paramètre à la méthode `ToString(String)` du nombre ou à une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="97d9c-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="97d9c-144">L'exemple suivant remplit deux valeurs <xref:System.Double> avec cinq zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="97d9c-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="97d9c-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97d9c-145">See also</span></span>

- [<span data-ttu-id="97d9c-146">Chaînes de format numérique personnalisées</span><span class="sxs-lookup"><span data-stu-id="97d9c-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="97d9c-147">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="97d9c-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="97d9c-148">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="97d9c-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
