---
title: Return (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 3ca705409bc8233bc2562c64b8e7704f08dd7641
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871806"
---
# <a name="return-statement-visual-basic"></a>Return, instruction (Visual Basic)

Retourne le contrôle au code qui a appelé une `Function` procédure,,, `Sub` `Get` `Set` ou `Operator` .  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Élément  

 `expression`  
 Obligatoire dans une `Function` `Get` procédure, ou `Operator` . Expression qui représente la valeur à retourner au code appelant.  
  
## <a name="remarks"></a>Notes  

 Dans une `Sub` `Set` procédure ou, l' `Return` instruction est équivalente à `Exit Sub` une `Exit Property` instruction ou, et `expression` ne doit pas être fournie.  
  
 Dans une `Function` `Get` procédure, ou `Operator` , l' `Return` instruction doit inclure `expression` , et `expression` doit correspondre à un type de données convertible en type de retour de la procédure. Dans une `Function` `Get` procédure ou, vous avez également la possibilité d’attribuer une expression au nom de la procédure pour servir de valeur de retour, puis d’exécuter une `Exit Function` instruction ou `Exit Property` . Dans une `Operator` procédure, vous devez utiliser `Return expression` .  
  
 Vous pouvez inclure autant `Return` d’instructions que nécessaire dans la même procédure.  
  
> [!NOTE]
> Le code d’un `Finally` bloc s’exécute après l’exécution d’une `Return` instruction dans un `Try` `Catch` bloc ou, mais avant l’exécution de cette `Return` instruction. Une `Return` instruction ne peut pas être incluse dans un `Finally` bloc.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise `Return` plusieurs fois l’instruction pour retourner au code appelant lorsque la procédure n’a pas à faire autre chose.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Voir aussi

- [Function (instruction)](function-statement.md)
- [Sub (instruction)](sub-statement.md)
- [Get, instruction](get-statement.md)
- [Instruction Set](set-statement.md)
- [Operator Statement](operator-statement.md)
- [Property Statement](property-statement.md)
- [Exit (instruction)](exit-statement.md)
- [Try...Catch...Finally (instruction)](try-catch-finally-statement.md)
