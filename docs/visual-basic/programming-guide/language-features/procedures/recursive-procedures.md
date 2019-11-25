---
title: Procédures récursives
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 646d4e29ed7a0b6367d4b35a7f8641bcf659e616
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352554"
---
# <a name="recursive-procedures-visual-basic"></a>Procédures récursives (Visual Basic)

A *recursive* procedure is one that calls itself. In general, this is not the most effective way to write Visual Basic code.  
  
 The following procedure uses recursion to calculate the factorial of its original argument.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considerations with Recursive Procedures

 **Limiting Conditions**. You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls. Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.

 **Utilisation de la mémoire**. Your application has a limited amount of space for local variables. Each time a procedure calls itself, it uses more of that space for additional copies of its local variables. If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.

 **Efficiency**. You can almost always substitute a loop for recursion. A loop does not have the overhead of passing arguments, initializing additional storage, and returning values. Your performance can be much better without recursive calls.

 **Mutual Recursion**. You might observe very poor performance, or even an infinite loop, if two procedures call each other. Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.

 **Calling with Parentheses**. When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list. Otherwise, the function name is taken as representing the return value of the function.

 **Testing**. If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition. You should also ensure that you cannot run out of memory due to having too many recursive calls.

## <a name="see-also"></a>Voir aussi

- <xref:System.StackOverflowException>
- [Procédures](index.md)
- [Procédures Sub](sub-procedures.md)
- [Procédures Function](function-procedures.md)
- [Procédures de propriété](property-procedures.md)
- [Procédures d’opérateur](operator-procedures.md)
- [Paramètres et arguments d’une procédure](procedure-parameters-and-arguments.md)
- [Surcharge de procédure](procedure-overloading.md)
- [Procédures de dépannage](troubleshooting-procedures.md)
- [Structures de boucle](../control-flow/loop-structures.md)
