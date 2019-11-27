---
title: 'Comment : convertir des chaînes en tableau d’octets'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 76fde3120ce629ce32f29ca28d90eba24fff726c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351974"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Comment : convertir des chaînes en tableau d'octets en Visual Basic
Cette rubrique montre comment convertir une chaîne en un tableau d’octets.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la méthode <xref:System.Text.Encoding.GetBytes%2A> de la classe d’encodage <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> pour convertir une chaîne en un tableau d’octets.  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 Vous pouvez choisir parmi plusieurs options d’encodage pour convertir une chaîne en un tableau d’octets :  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: obtient un encodage pour le jeu de caractères ASCII (7 bits).  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: obtient un encodage pour la page de codes ANSI actuelle du système.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-16 à l’aide de l’ordre d’octet avec primauté des octets de poids faible (Little-endian).  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-32 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-7.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-8.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [Comment : convertir un tableau d’octets en une chaîne dans Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
