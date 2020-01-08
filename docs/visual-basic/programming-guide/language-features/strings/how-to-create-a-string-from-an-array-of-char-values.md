---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char"
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: bf37ceba901e712df10ad4b39f9ad74194843136
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346771"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)
Cet exemple crée la chaîne « ABCD » à partir de caractères individuels.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cette méthode n’a pas d’exigences particulières.  
  
 La syntaxe `"a"c`, où un seul `c` suit un caractère unique entre guillemets, est utilisé pour créer un littéral de caractère.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les caractères null (équivalents à `Chr(0)`) dans la chaîne entraînent des résultats inattendus lors de l’utilisation de la chaîne. Le caractère null sera inclus avec la chaîne, mais les caractères qui suivent le caractère NULL ne seront pas affichés dans certaines situations.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String>
- [Char (type de données)](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
