---
title: 'Comment : créer une procédure qui retourne une valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 3d28162d2a2103477a20b08fc03c937de8b5a475
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071870"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Comment : créer une procédure qui retourne une valeur (Visual Basic)

Vous utilisez une `Function` procédure pour retourner une valeur au code appelant.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Pour créer une procédure qui retourne une valeur  
  
1. En dehors de toute autre procédure, utilisez une `Function` instruction, suivie d’une `End Function` instruction.  
  
2. Dans l' `Function` instruction, suivez le `Function` mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.  
  
3. Suivez les parenthèses avec une `As` clause pour spécifier le type de données de la valeur retournée.  
  
4. Placez les instructions de code de la procédure entre les `Function` `End Function` instructions et.  
  
5. Utilisez une `Return` instruction pour retourner la valeur au code appelant.  
  
     La `Function` procédure suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse` .  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Sub, procédures](./sub-procedures.md)
- [Procédures Property](./property-procedures.md)
- [Procédures d'opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../language-reference/statements/function-statement.md)
- [Comment : retourner une valeur d'une procédure](./how-to-return-a-value-from-a-procedure.md)
- [Comment : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
