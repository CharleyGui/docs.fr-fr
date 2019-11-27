---
title: "Comment : retourner une valeur d'une procédure"
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346025"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Comment : retourner une valeur d'une procédure (Visual Basic)
Une procédure `Function` retourne une valeur au code appelant en exécutant une instruction `Return` ou en rencontrant une instruction `Exit Function` ou `End Function`.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Pour retourner une valeur à l’aide de l’instruction return  
  
1. Placez une `Return` instruction au point où la tâche de la procédure est terminée.  
  
2. Suivez le mot clé `Return` avec une expression qui génère la valeur que vous souhaitez retourner au code appelant.  
  
3. Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.  
  
     La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, puis le retourne au code appelant.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse`, qui stocke la valeur retournée.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Pour retourner une valeur à l’aide de la fonction EXIT ou end  
  
1. Dans au moins un emplacement de la procédure `Function`, assignez une valeur au nom de la procédure.  
  
2. Lorsque vous exécutez une instruction `Exit Function` ou `End Function`, Visual Basic retourne la valeur la plus récemment affectée au nom de la procédure.  
  
3. Vous pouvez utiliser plusieurs instructions `Exit Function` dans la même procédure et combiner des instructions `Return` et `Exit Function` dans la même procédure.  
  
4. Vous ne pouvez avoir qu’une seule instruction `End Function` dans une procédure `Function`.  
  
     Pour plus d’informations et pour obtenir un exemple, consultez « valeur de retour » dans l' [instruction de fonction](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return (instruction)](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Guide pratique : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)
- [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
