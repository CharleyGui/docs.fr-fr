---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char"
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344384"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)
This example creates the string "abcd" from individual characters.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 This method has no special requirements.  
  
 The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string. The null character will be included with the string, but characters following the null character will not be displayed in some situations.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String>
- [Char (type de données)](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
