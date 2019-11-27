---
title: 'Comment : convertir des chaînes hexadécimales en nombres'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347171"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Comment : convertir des chaînes hexadécimales en nombres (Visual Basic)

Cet exemple convertit une chaîne hexadécimale en entier à l’aide de la méthode <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Pour convertir une chaîne hexadécimale en nombre

- Utilisez la méthode <xref:System.Convert.ToInt32(System.String,System.Int32)> pour convertir le nombre exprimé en base-16 en un entier.

  Le premier argument de la méthode <xref:System.Convert.ToInt32(System.String,System.Int32)> est la chaîne à convertir. Le deuxième argument décrit la base dans laquelle le nombre est exprimé ; la notation hexadécimale est de base 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Notez que la chaîne hexadécimale présente les restrictions suivantes :

  - Elle ne peut pas inclure le préfixe `&h`.
  - Elle ne peut pas inclure le séparateur de chiffres `_`.

  Si le préfixe ou un séparateur de chiffres est présent, l’appel à la méthode <xref:System.Convert.ToInt32(System.String,System.Int32)> lève une <xref:System.FormatException>.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
