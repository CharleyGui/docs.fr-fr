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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="90e1a-102">Comment : convertir des chaînes hexadécimales en nombres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90e1a-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="90e1a-103">Cet exemple convertit une chaîne hexadécimale en entier à l’aide de la méthode <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90e1a-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="90e1a-104">Pour convertir une chaîne hexadécimale en nombre</span><span class="sxs-lookup"><span data-stu-id="90e1a-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="90e1a-105">Utilisez la méthode <xref:System.Convert.ToInt32(System.String,System.Int32)> pour convertir le nombre exprimé en base-16 en un entier.</span><span class="sxs-lookup"><span data-stu-id="90e1a-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="90e1a-106">Le premier argument de la méthode <xref:System.Convert.ToInt32(System.String,System.Int32)> est la chaîne à convertir.</span><span class="sxs-lookup"><span data-stu-id="90e1a-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="90e1a-107">Le deuxième argument décrit la base dans laquelle le nombre est exprimé ; la notation hexadécimale est de base 16.</span><span class="sxs-lookup"><span data-stu-id="90e1a-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="90e1a-108">Notez que la chaîne hexadécimale présente les restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="90e1a-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="90e1a-109">Elle ne peut pas inclure le préfixe `&h`.</span><span class="sxs-lookup"><span data-stu-id="90e1a-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="90e1a-110">Elle ne peut pas inclure le séparateur de chiffres `_`.</span><span class="sxs-lookup"><span data-stu-id="90e1a-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="90e1a-111">Si le préfixe ou un séparateur de chiffres est présent, l’appel à la méthode <xref:System.Convert.ToInt32(System.String,System.Int32)> lève une <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="90e1a-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="90e1a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90e1a-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
