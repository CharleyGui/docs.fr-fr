---
title: 'Comment : protéger un argument de procédure contre les modifications de valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 36092eb597b5b20e1da42cd9d15ab8633636cfb1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344858"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)
Si une procédure déclare un paramètre comme [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic donne au code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant. Cela permet à la procédure de modifier la valeur sous-jacente de l’argument dans le code appelant. Dans certains cas, le code appelant peut souhaiter se protéger contre une telle modification.  
  
 Vous pouvez toujours protéger un argument de la modification en déclarant le paramètre correspondant [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la procédure. Si vous souhaitez être en mesure de modifier un argument donné dans certains cas, mais pas dans d’autres, vous pouvez le déclarer `ByRef` et laisser le code appelant déterminer le mécanisme de passage dans chaque appel. Pour ce faire, elle met l’argument correspondant entre parenthèses pour la passer par valeur, ou ne l’englobe pas entre parenthèses pour la passer par référence. Pour plus d’informations, consultez [Comment : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux procédures qui prennent une variable tableau et opèrent sur ses éléments. La procédure `increase` ajoute simplement une à chaque élément. La procédure `replace` assigne un nouveau tableau au paramètre `a()` puis en ajoute un à chaque élément. Toutefois, la réassignation n’affecte pas la variable de tableau sous-jacente dans le code appelant.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Le premier appel `MsgBox` affiche « après l’augmentation (n) : 11, 21, 31, 41 ». Étant donné que le tableau `n` est un type référence, `increase` pouvez modifier ses membres, même si le mécanisme de passage est `ByVal`.  
  
 Le deuxième `MsgBox` appel affiche « after Replace (n) : 11, 21, 31, 41 ». Étant donné que `n` est passé `ByVal`, `replace` ne peut pas modifier la variable `n` dans le code appelant en lui assignant un nouveau tableau. Lorsque `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a`, elle perd la référence à `n` passé par le code appelant. En cas de modification des membres de `a`, seul le groupe local `k` est affecté. Par conséquent, `replace` n’incrémente pas les valeurs des `n` de tableau dans le code appelant.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 La valeur par défaut de Visual Basic consiste à passer des arguments par valeur. Toutefois, il est recommandé d’inclure le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) avec chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Guide pratique : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Guide pratique : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
