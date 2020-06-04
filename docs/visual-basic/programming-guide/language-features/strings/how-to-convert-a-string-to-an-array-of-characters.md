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
ms.openlocfilehash: eca8cd7be8da1f6149dadf1e9edeab5e5225ab9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360668"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Comment : convertir une chaîne en tableau de caractères en Visual Basic
Il est parfois utile d’avoir des données sur les caractères de votre chaîne et les positions de ces caractères dans votre chaîne, par exemple lorsque vous analysez une chaîne. Cet exemple montre comment obtenir un tableau de caractères dans une chaîne en appelant la méthode de la chaîne <xref:System.String.ToCharArray%2A> .  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment fractionner une chaîne en `Char` tableau et comment fractionner une chaîne en un `String` tableau de ses caractères de texte Unicode. Cette distinction est due au fait que les caractères de texte Unicode peuvent être composés d’au moins deux `Char` caractères (par exemple une paire de substitution ou une séquence de caractères d’association). Pour plus d’informations, consultez <xref:System.Globalization.TextElementEnumerator> et [la norme Unicode](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Exemple  
 Il est plus difficile de fractionner une chaîne en ses caractères de texte Unicode, mais cela est nécessaire si vous avez besoin d’informations sur la représentation visuelle d’une chaîne. Cet exemple utilise la <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> méthode pour obtenir des informations sur les caractères de texte Unicode qui composent une chaîne.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Comment : accéder aux caractères dans les chaînes](how-to-access-characters-in-strings.md)
- [Conversion entre chaînes et d'autres types de données en Visual Basic](converting-between-strings-and-other-data-types.md)
- [Chaînes](index.md)
