---
title: "Comment : retourner une valeur d'une procédure"
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346025"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Comment : retourner une valeur d'une procédure (Visual Basic)
A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>To return a value using the Return statement  
  
1. Put a `Return` statement at the point where the procedure's task is completed.  
  
2. Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.  
  
3. Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.  
  
     The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     The following example shows a typical call to `hypotenuse`, which stores the returned value.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>To return a value using Exit Function or End Function  
  
1. In at least one place in the `Function` procedure, assign a value to the procedure's name.  
  
2. When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.  
  
3. Vous pouvez utiliser plusieurs instructions `Exit Function` dans la même procédure et combiner des instructions `Return` et `Exit Function` dans la même procédure.  
  
4. You can have only one `End Function` statement in a `Function` procedure.  
  
     For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return (instruction)](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Guide pratique : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)
- [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
