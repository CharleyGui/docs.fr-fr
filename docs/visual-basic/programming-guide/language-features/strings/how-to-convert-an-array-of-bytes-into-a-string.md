---
title: 'Comment : convertir un tableau d’octets en une chaîne'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 8c1d9d1d2e89390873bc1c3dbb9623f047433a9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351980"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Comment : convertir un tableau d'octets en chaîne en Visual Basic
Cette rubrique montre comment convertir les octets d’un tableau d’octets en une chaîne.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la méthode <xref:System.Text.Encoding.GetString%2A> de la classe d’encodage <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> pour convertir tous les octets d’un tableau d’octets en chaîne.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Vous pouvez choisir parmi plusieurs options d’encodage pour convertir un tableau d’octets en une chaîne :  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: obtient un encodage pour le jeu de caractères ASCII (7 bits).  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: obtient un encodage pour la page de codes ANSI actuelle du système.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-16 à l’aide de l’ordre d’octet avec primauté des octets de poids faible (Little-endian).  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-32 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-7.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: obtient un encodage pour le format UTF-8.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Comment : convertir des chaînes en tableau d’octets dans Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
