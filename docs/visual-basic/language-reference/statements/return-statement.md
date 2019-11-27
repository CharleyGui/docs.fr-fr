---
title: Return, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: efc85a3a844898345aa2d16926ba0e35d7346d1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333013"
---
# <a name="return-statement-visual-basic"></a>Return, instruction (Visual Basic)
Retourne le contrôle au code qui a appelé une procédure `Function`, `Sub`, `Get`, `Set`ou `Operator`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Élément  
 `expression`  
 Obligatoire dans une procédure `Function`, `Get`ou `Operator`. Expression qui représente la valeur à retourner au code appelant.  
  
## <a name="remarks"></a>Notes  
 Dans une procédure `Sub` ou `Set`, l’instruction `Return` est équivalente à une instruction `Exit Sub` ou `Exit Property`, et `expression` ne doit pas être fourni.  
  
 Dans une procédure `Function`, `Get`ou `Operator`, l’instruction `Return` doit inclure `expression`, et `expression` doit correspondre à un type de données convertible en type de retour de la procédure. Dans une procédure `Function` ou `Get`, vous avez également la possibilité d’affecter une expression au nom de la procédure pour servir de valeur de retour, puis d’exécuter une instruction `Exit Function` ou `Exit Property`. Dans une procédure `Operator`, vous devez utiliser `Return expression`.  
  
 Vous pouvez inclure autant d’instructions `Return` que nécessaire dans la même procédure.  
  
> [!NOTE]
> Le code d’un bloc `Finally` s’exécute après la détection d’une instruction `Return` dans un bloc `Try` ou `Catch`, mais avant l’exécution de cette `Return` instruction. Une instruction `Return` ne peut pas être incluse dans un bloc `Finally`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise plusieurs fois l’instruction `Return` pour retourner au code appelant lorsque la procédure n’a pas à faire autre chose.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Voir aussi

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
