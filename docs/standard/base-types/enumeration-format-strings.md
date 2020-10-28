---
title: Chaînes de format d’énumération
description: Créez des chaînes de format d’énumération à l’aide de la méthode Enum. ToString dans .NET. Mettre en forme les valeurs numériques, hexadécimales ou de chaîne des membres de l’énumération.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: e4d8ca27d99c211653269b2477be8f5632b78229
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888657"
---
# <a name="enumeration-format-strings"></a>Chaînes de format d’énumération

Vous pouvez utiliser la méthode <xref:System.Enum.ToString%2A?displayProperty=nameWithType> pour créer un objet de chaîne qui représente la valeur numérique, hexadécimale ou de chaîne d’un membre d’énumération. Cette méthode prend l’une des chaînes de mise en forme d’énumération pour spécifier la valeur à retourner.

Les sections suivantes répertorient les chaînes de mise en forme d’énumération et les valeurs qu’elles retournent. Ces spécificateurs de format ne respectent pas la casse.

## <a name="g-or-g"></a>G ou g

Affiche l’entrée d’énumération comme valeur de chaîne, dans la mesure du possible ; sinon, affiche la valeur entière de l’instance actuelle. Si l’énumération est définie avec l’attribut **Flags** défini, les valeurs de chaîne de chaque entrée valide sont concaténées et séparées par des virgules. Si l’attribut **Flags** n’est pas défini, une valeur non valide s’affiche comme entrée numérique. L’exemple suivant illustre le spécificateur de format G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F ou f

Affiche l’entrée d’énumération comme valeur de chaîne, si possible. Si la valeur peut être complètement affichée comme somme des entrées de l’énumération (même si l’attribut **Flags** n’est pas présent), les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules. Si la valeur ne peut pas être complètement déterminée par les entrées de l’énumération, la valeur est mise en forme comme valeur entière. L’exemple suivant illustre le spécificateur de format F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D ou d

Affiche l’entrée d’énumération comme valeur entière dans la représentation la plus courte possible. L’exemple suivant illustre le spécificateur de format D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X ou x

Affiche l’entrée d’énumération comme valeur hexadécimale. La valeur est représentée avec des zéros interligne si nécessaire, pour vérifier que la chaîne de résultat a deux caractères pour chaque octet dans le [type numérique sous-jacent](xref:System.Enum.GetUnderlyingType%2A) du type d’énumération. L’exemple suivant illustre le spécificateur de format X. Dans l’exemple, le type sous-jacent des deux <xref:System.ConsoleColor> et <xref:System.IO.FileAttributes> est <xref:System.Int32> ou un entier de 32 bits (ou 4 octets), ce qui produit une chaîne de résultat de 8 caractères.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Exemple

L’exemple suivant définit une énumération appelée `Colors` qui se compose de trois entrées : `Red`, `Blue` et `Green`.

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Une fois que l’énumération est définie, une instance peut être déclarée de la manière suivante.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

La méthode `Color.ToString(System.String)` peut ensuite être utilisée pour afficher la valeur d’énumération de différentes manières, selon le spécificateur de format qui lui est passé.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Voir aussi

- [Mise en forme des types](formatting-types.md)
