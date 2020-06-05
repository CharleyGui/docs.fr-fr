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
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Procédure : remplir un nombre avec des zéros non significatifs

Vous pouvez ajouter des zéros non significatifs à un entier en utilisant la [chaîne de format numérique standard](standard-numeric-format-strings.md) « D » avec un spécificateur de précision. Vous pouvez ajouter des zéros non significatifs aux nombres entiers et à virgule flottante en utilisant une [chaîne de format numérique personnalisée](custom-numeric-format-strings.md). Cet article montre comment utiliser les deux méthodes pour remplir un nombre avec des zéros non significatifs.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Pour remplir un entier avec des zéros non significatifs dans la limite d'une longueur spécifique

1. Déterminez le nombre minimal de chiffres que la valeur entière doit afficher. Incluez des chiffres non significatifs dans ce nombre.

1. Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.

    - Pour afficher l’entier comme valeur décimale, appelez sa méthode `ToString(String)`, puis passez la chaîne « D*n* » comme valeur du paramètre `format`, où *n* représente la longueur minimale de la chaîne.

    - Pour afficher l’entier comme valeur hexadécimale, appelez sa méthode `ToString(String)`, puis transmettez la chaîne « X*n* » comme valeur du paramètre de format, où *n* représente la longueur minimale de la chaîne.

Vous pouvez également utiliser la chaîne de format dans une chaîne interpolée dans [C#](../../csharp/language-reference/tokens/interpolated.md) et [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), ou vous pouvez appeler une méthode, telle que <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, qui utilise la [mise en forme composite](composite-formatting.md).

L'exemple suivant met en forme plusieurs valeurs entières avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Pour remplir un entier avec un nombre spécifique de zéros non significatifs

1. Déterminez le nombre de zéros non significatifs que la valeur entière doit afficher.

1. Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.

    - Une mise en forme en tant que valeur décimale nécessite l’utilisation du spécificateur de format standard « D ».

    - Une mise en forme en tant que valeur hexadécimale nécessite l’utilisation du spécificateur de format standard « X ».

1. Déterminez la longueur de la chaîne numérique non remplie en appelant la méthode `ToString("D").Length` ou `ToString("X").Length` de la valeur entière.

1. Ajoutez le nombre de zéros non significatifs à inclure dans la chaîne mise en forme à la longueur de la chaîne numérique non remplie. L’ajout du nombre de zéros non significatifs définit la longueur totale de la chaîne remplie.

1. Appelez la méthode `ToString(String)` de la valeur entière, puis transmettez la chaîne « D*n* » pour les chaînes décimales et la chaîne « X*n* » pour les chaînes hexadécimales, où *n* représente la longueur totale de la chaîne remplie. Vous pouvez également utiliser la chaîne de format « D*n* » ou « X*n* » dans une méthode qui prend en charge la mise en forme composite.

L'exemple suivant remplit une valeur entière avec cinq zéros non significatifs.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Pour remplir une valeur numérique avec des zéros non significatifs dans la limite d'une longueur spécifique

1. Déterminez le nombre de chiffres à gauche du séparateur décimal qui doivent apparaître dans la représentation du nombre sous forme de chaîne. Incluez des zéros non significatifs dans ce nombre total de chiffres.

1. Définissez une chaîne de format numérique personnalisée qui utilise l’espace réservé du zéro « 0 » pour représenter le nombre minimal de zéros.

1. Appelez la méthode `ToString(String)` du nombre et transmettez-lui la chaîne de format personnalisée. Vous pouvez également utiliser la chaîne de format personnalisée avec l’interpolation de chaîne ou avec une méthode qui prend en charge la mise en forme composite.

L’exemple suivant met en forme plusieurs valeurs numériques avec des zéros non significatifs. Par conséquent, la longueur totale du nombre mis en forme est de huit chiffres minimum à gauche du séparateur décimal.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Pour remplir une valeur numérique avec un nombre spécifique de zéros non significatifs

1. Déterminez le nombre de zéros non significatifs que la valeur numérique doit avoir.

1. Déterminez le nombre de chiffres à gauche du séparateur décimal dans la chaîne numérique non remplie :

    1. Déterminez si la représentation sous forme de chaîne d'un nombre comprend un séparateur décimal.

    1. Si tel est le cas, déterminez le nombre de caractères à gauche du séparateur décimal.

         -ou-

         Sinon, déterminez la longueur de la chaîne.

1. Créez une chaîne de format personnalisée qui utilise :

    - L’espace réservé du zéro « 0 » pour chaque zéro non significatif qui apparaît dans la chaîne.

    - L’espace réservé du zéro ou l’espace réservé de chiffre « # » pour représenter chaque chiffre dans la chaîne par défaut.

1. Fournissez la chaîne de format personnalisée comme paramètre à la méthode `ToString(String)` du nombre ou à une méthode qui prend en charge la mise en forme composite.

L'exemple suivant remplit deux valeurs <xref:System.Double> avec cinq zéros non significatifs.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Voir aussi

- [Chaînes de format numériques personnalisées](custom-numeric-format-strings.md)
- [Chaînes de format numériques standard](standard-numeric-format-strings.md)
- [Mise en forme composite](composite-formatting.md)
