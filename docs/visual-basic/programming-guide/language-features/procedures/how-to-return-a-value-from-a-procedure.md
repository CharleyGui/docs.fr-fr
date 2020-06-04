---
title: "Comment : retourner une valeur d'une procédure"
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 917e52b711645fbf94a132216a3fa90b0dfc15b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414322"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Comment : retourner une valeur d'une procédure (Visual Basic)
Une `Function` procédure retourne une valeur au code appelant en exécutant une `Return` instruction ou en rencontrant une `Exit Function` `End Function` instruction ou.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Pour retourner une valeur à l’aide de l’instruction return  
  
1. Placez une `Return` instruction au point où la tâche de la procédure est terminée.  
  
2. Suivez le `Return` mot clé avec une expression qui génère la valeur que vous souhaitez retourner au code appelant.  
  
3. Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.  
  
     La `Function` procédure suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, et le retourne au code appelant.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse` , qui stocke la valeur retournée.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Pour retourner une valeur à l’aide de la fonction EXIT ou end  
  
1. À au moins un emplacement dans la `Function` procédure, assignez une valeur au nom de la procédure.  
  
2. Quand vous exécutez une `Exit Function` `End Function` instruction ou, Visual Basic retourne la dernière valeur assignée au nom de la procédure.  
  
3. Vous pouvez utiliser plusieurs instructions `Exit Function` dans la même procédure et combiner des instructions `Return` et `Exit Function` dans la même procédure.  
  
4. Une procédure ne peut comporter qu’une seule `End Function` instruction `Function` .  
  
     Pour plus d’informations et pour obtenir un exemple, consultez « valeur de retour » dans l' [instruction de fonction](../../../language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Sub, procédures](./sub-procedures.md)
- [Procédures Property](./property-procedures.md)
- [Procédures d'opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../language-reference/statements/function-statement.md)
- [Instruction return](../../../language-reference/statements/return-statement.md)
- [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)
- [Comment : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
