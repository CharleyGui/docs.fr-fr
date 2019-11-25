---
title: 'Comment : passer des arguments à une procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 0267eed7c145988d61de715fd661bd4906d8d57d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344843"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Comment : passer des arguments à une procédure (Visual Basic)
When you call a procedure, you follow the procedure name with an argument list in parentheses. You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters. If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.  
  
 If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`. If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords. For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>To pass one or more arguments to a procedure  
  
1. In the calling statement, follow the procedure name with parentheses.  
  
2. Inside the parentheses, put an argument list. Include an argument for each required parameter the procedure defines, and separate the arguments with commas.  
  
3. Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.  
  
4. If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it. If you omit it, the procedure uses the default value defined for that parameter.  
  
5. If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.  
  
     The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     The preceding example supplies the required first argument, which is the message string to be displayed. It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box. Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.  
  
     The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures Sub](./sub-procedures.md)
- [Procédures Function](./function-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Procédures récursives](./recursive-procedures.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
