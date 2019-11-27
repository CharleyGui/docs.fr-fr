---
title: 'Comment : accéder aux caractères dans les chaînes'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352462"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Comment : accéder aux caractères dans les chaînes en Visual Basic
Cet exemple montre comment utiliser la propriété <xref:System.String.Chars%2A> pour accéder au caractère à l’emplacement spécifié dans une chaîne.  
  
## <a name="example"></a>Exemple  
 Il est parfois utile d’avoir des données sur les caractères de votre chaîne et les positions de ces caractères dans la chaîne. Vous pouvez considérer une chaîne comme un tableau de caractères (instances`Char`); vous pouvez récupérer un caractère particulier en référençant l’index de ce caractère via la propriété <xref:System.String.Chars%2A>.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 Le paramètre `index` de la propriété <xref:System.String.Chars%2A> est de base zéro.  
  
## <a name="robust-programming"></a>Programmation fiable  
 La propriété <xref:System.String.Chars%2A> retourne le caractère à la position spécifiée. Toutefois, certains caractères Unicode peuvent être représentés par plusieurs caractères. Pour plus d’informations sur l’utilisation des caractères Unicode, consultez [Comment : convertir une chaîne en tableau de caractères](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 La propriété <xref:System.String.Chars%2A> lève une exception <xref:System.IndexOutOfRangeException> si le paramètre `index` est supérieur ou égal à la longueur de la chaîne, ou s’il est inférieur à zéro  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String.Chars%2A>
- [Guide pratique : convertir une chaîne en tableau de caractères](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Conversion entre chaînes et d’autres types de données en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Chaînes](../../../../visual-basic/programming-guide/language-features/strings/index.md)
