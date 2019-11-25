---
title: Erase, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343698"
---
# <a name="erase-statement-visual-basic"></a>Erase, instruction (Visual Basic)
Used to release array variables and deallocate the memory used for their elements.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Composants  
 `arraylist`  
 Requis. List of array variables to be erased. Les variables multiples sont séparées par des virgules.  
  
## <a name="remarks"></a>Notes  
 The `Erase` statement can appear only at procedure level. This means you can release arrays inside a procedure but not at class or module level.  
  
 The `Erase` statement is equivalent to assigning `Nothing` to each array variable.  
  
## <a name="example"></a>Exemple  
 The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively). The `ReDim` statement then assigns a new array instance to the three-dimensional array.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)
