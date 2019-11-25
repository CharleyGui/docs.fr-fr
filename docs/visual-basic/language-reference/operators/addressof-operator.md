---
title: AddressOf, opérateur
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350282"
---
# <a name="addressof-operator-visual-basic"></a>Opérateur AddressOf (Visual Basic)
Creates a delegate instance that references the specific procedure.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Composants  
 `procedurename`  
 Requis. Specifies the procedure to be referenced by the newly created delegate.  
  
## <a name="remarks"></a>Notes  
 The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`. When the specified procedure is an instance method then the delegate refers to both the instance and the method. Then, when the  delegate is invoked the specified method of the specified instance is called.  
  
 The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.  
  
## <a name="example"></a>Exemple  
 This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemple  
 The following example uses the `AddressOf` operator to designate the startup function for a thread.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)
