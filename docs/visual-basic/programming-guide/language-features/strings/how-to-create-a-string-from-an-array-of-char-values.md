---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char"
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071155"
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
- [Data types](../data-types/index.md)
