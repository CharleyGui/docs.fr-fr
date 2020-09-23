---
title: 'Comment : appeler une procédure qui retourne une valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 53589f84c6675d1e7ae2a593341e5dac747132a9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083975"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Comment : appeler une procédure qui retourne une valeur (Visual Basic)

Une `Function` procédure retourne une valeur au code appelant. Vous l’appelez en incluant son nom et ses arguments sur le côté droit d’une instruction d’assignation ou dans une expression.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Pour appeler une procédure de fonction dans une expression  
  
1. Utilisez le `Function` nom de la procédure de la même façon que vous utilisez une variable. Vous pouvez utiliser un `Function` appel de procédure partout où vous pouvez utiliser une variable ou une constante dans une expression.  
  
2. Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la `Function` procédure définit les paramètres correspondants.  
  
     Vous pouvez également passer un ou plusieurs arguments par nom. Pour plus d’informations, consultez [passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md).  
  
4. La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou d’une constante.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Pour appeler une procédure de fonction dans une instruction d’assignation  
  
1. Utilisez le `Function` nom de la procédure après le `=` signe égal () dans l’instruction d’assignation.  
  
2. Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la `Function` procédure définit les paramètres correspondants, sauf si vous les passez par nom.  
  
4. La valeur retournée par la procédure est stockée dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant appelle la Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pour récupérer la valeur d’une variable d’environnement de système d’exploitation. La première ligne appelle `Environ` dans une expression, et la deuxième ligne l’appelle dans une instruction d’assignation. `Environ` prend le nom de la variable en tant qu’argument unique. Elle retourne la valeur de la variable au code appelant.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- [Function, procédures](./function-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../language-reference/statements/function-statement.md)
- [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)
- [Comment : retourner une valeur d'une procédure](./how-to-return-a-value-from-a-procedure.md)
- [Comment : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)
