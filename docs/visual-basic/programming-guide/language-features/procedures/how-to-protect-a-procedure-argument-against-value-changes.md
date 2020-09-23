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
ms.openlocfilehash: 84eadf3d364b69120221d80e464b1175b1602e13
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071480"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)

Si une procédure déclare un paramètre comme [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic donne au code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant. Cela permet à la procédure de modifier la valeur sous-jacente de l’argument dans le code appelant. Dans certains cas, le code appelant peut souhaiter se protéger contre une telle modification.  
  
 Vous pouvez toujours protéger un argument de la modification en déclarant le paramètre correspondant [ByVal](../../../language-reference/modifiers/byval.md) dans la procédure. Si vous souhaitez être en mesure de modifier un argument donné dans certains cas, mais pas dans d’autres, vous pouvez `ByRef` le déclarer et laisser le code appelant déterminer le mécanisme de passage dans chaque appel. Pour ce faire, elle met l’argument correspondant entre parenthèses pour la passer par valeur, ou ne l’englobe pas entre parenthèses pour la passer par référence. Pour plus d’informations, consultez [Comment : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre deux procédures qui prennent une variable tableau et opèrent sur ses éléments. La `increase` procédure ajoute simplement une à chaque élément. La `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis ajoute un à chaque élément. Toutefois, la réassignation n’affecte pas la variable de tableau sous-jacente dans le code appelant.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Le premier `MsgBox` appel affiche « après l’augmentation (n) : 11, 21, 31, 41 ». Étant donné que le tableau `n` est un type référence, `increase` peut modifier ses membres, même si le mécanisme de passage est `ByVal` .  
  
 Le deuxième `MsgBox` appel affiche « after Replace (n) : 11, 21, 31, 41 ». Étant donné que `n` est passé `ByVal` , `replace` ne peut pas modifier la variable `n` dans le code appelant en lui assignant un nouveau tableau. Lorsque `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a` , elle perd la référence à `n` passée par le code appelant. Lorsqu’il modifie les membres de `a` , seul le tableau local `k` est affecté. Par conséquent, `replace` n’incrémente pas les valeurs d’un tableau `n` dans le code appelant.  
  
## <a name="compile-the-code"></a>Compiler le code  

 La valeur par défaut de Visual Basic consiste à passer des arguments par valeur. Toutefois, il est recommandé d’inclure le mot clé [ByVal](../../../language-reference/modifiers/byval.md) ou [ByRef](../../../language-reference/modifiers/byref.md) avec chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Différences entre le passage d'un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Comment : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Comment : forcer le passage d'un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
