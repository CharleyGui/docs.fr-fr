---
title: 'Comment : créer une procédure qui retourne une valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349721"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Comment : créer une procédure qui retourne une valeur (Visual Basic)
Vous utilisez une procédure `Function` pour retourner une valeur au code appelant.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Pour créer une procédure qui retourne une valeur  
  
1. En dehors de toute autre procédure, utilisez une instruction `Function`, suivie d’une instruction `End Function`.  
  
2. Dans l’instruction `Function`, suivez le mot clé `Function` avec le nom de la procédure, puis la liste de paramètres entre parenthèses.  
  
3. Suivez les parenthèses avec une clause `As` pour spécifier le type de données de la valeur retournée.  
  
4. Placez les instructions de code de la procédure entre les instructions `Function` et `End Function`.  
  
5. Utilisez une instruction `Return` pour retourner la valeur au code appelant.  
  
     La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Guide pratique : retourner une valeur d’une procédure](./how-to-return-a-value-from-a-procedure.md)
- [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
