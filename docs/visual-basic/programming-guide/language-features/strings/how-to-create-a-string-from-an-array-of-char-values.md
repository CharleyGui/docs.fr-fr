---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char"
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: d9ec897467f0caac0afc089a028516c0316a2bda
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410591"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)
Cet exemple crée la chaîne « ABCD » à partir de caractères individuels.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cette méthode n’a pas d’exigences particulières.  
  
 La syntaxe `"a"c` , où une seule `c` suit un caractère unique entre guillemets, est utilisée pour créer un littéral de caractère.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les caractères null (équivalents à `Chr(0)` ) dans la chaîne entraînent des résultats inattendus lors de l’utilisation de la chaîne. Le caractère null sera inclus avec la chaîne, mais les caractères qui suivent le caractère NULL ne seront pas affichés dans certaines situations.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String>
- [Caractères (type de données)](../../../language-reference/data-types/char-data-type.md)
- [Types de données](../data-types/index.md)
