---
title: Return, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957671"
---
# <a name="return-statement-visual-basic"></a>Return, instruction (Visual Basic)
Retourne le contrôle au code qui a appelé `Function`une `Sub`procédure `Get`, `Set`,, `Operator` ou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Élément  
 `expression`  
 Obligatoire dans une `Function`procédure `Get`, ou `Operator` . Expression qui représente la valeur à retourner au code appelant.  
  
## <a name="remarks"></a>Notes  
 Dans une `Sub` procédure `Set` ou, l' `Return` instruction est équivalente à `Exit Sub` une `Exit Property` instruction ou, `expression` et ne doit pas être fournie.  
  
 Dans une `Function`procédure `Get`, ou `Operator` , l' `Return` instruction doit inclure `expression`, et `expression` doit correspondre à un type de données convertible en type de retour de la procédure. Dans une `Function` procédure `Get` ou, vous avez également la possibilité d’attribuer une expression au nom de la procédure pour servir de valeur de retour, puis d’exécuter une `Exit Function` instruction ou `Exit Property` . Dans une `Operator` procédure, vous devez utiliser `Return expression`.  
  
 Vous pouvez inclure `Return` autant d’instructions que nécessaire dans la même procédure.  
  
> [!NOTE]
> Le code d’un `Finally` bloc s’exécute après `Return` l’exécution d' `Try` une `Catch` instruction dans un bloc ou, mais `Return` avant l’exécution de cette instruction. Une `Return` instruction ne peut pas être incluse `Finally` dans un bloc.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise plusieurs `Return` fois l’instruction pour retourner au code appelant lorsque la procédure n’a pas à faire autre chose.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Voir aussi

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
