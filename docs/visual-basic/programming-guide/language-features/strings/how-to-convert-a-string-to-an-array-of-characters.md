---
title: 'Comment : convertir une chaîne en tableau de caractères'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352448"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Comment : convertir une chaîne en tableau de caractères en Visual Basic
Il est parfois utile d’avoir des données sur les caractères de votre chaîne et les positions de ces caractères dans votre chaîne, par exemple lorsque vous analysez une chaîne. Cet exemple montre comment obtenir un tableau de caractères dans une chaîne en appelant la méthode <xref:System.String.ToCharArray%2A> de la chaîne.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment fractionner une chaîne en tableau `Char` et comment fractionner une chaîne en un tableau `String` de ses caractères de texte Unicode. Cette distinction est due au fait que les caractères de texte Unicode peuvent être composés d’au moins deux caractères `Char` (par exemple, une paire de substitution ou une séquence de caractères d’association). Pour plus d’informations, consultez <xref:System.Globalization.TextElementEnumerator> et [la norme Unicode](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Exemple  
 Il est plus difficile de fractionner une chaîne en ses caractères de texte Unicode, mais cela est nécessaire si vous avez besoin d’informations sur la représentation visuelle d’une chaîne. Cet exemple utilise la méthode <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> pour obtenir des informations sur les caractères de texte Unicode qui composent une chaîne.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Guide pratique : accéder aux caractères dans les chaînes](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Conversion entre chaînes et d’autres types de données en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Chaînes](../../../../visual-basic/programming-guide/language-features/strings/index.md)
