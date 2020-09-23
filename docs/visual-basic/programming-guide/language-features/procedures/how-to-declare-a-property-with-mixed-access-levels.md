---
title: "Comment : déclarer une propriété avec des niveaux d'accès mixtes"
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 78363f7b2fb5b251f7409e53b2802baf83b05810
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072702"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Comment : déclarer une propriété avec des niveaux d'accès mixtes (Visual Basic)

Si vous souhaitez que `Get` les `Set` procédures et sur une propriété aient des niveaux d’accès différents, vous pouvez utiliser le niveau le plus permissif dans l' `Property` instruction et le niveau le plus restrictif dans l' `Get` `Set` instruction ou. Vous utilisez des niveaux d’accès mixtes sur une propriété lorsque vous souhaitez que certaines parties du code soient en mesure d’obtenir la valeur de la propriété, et que certaines autres parties du code soient en mesure de modifier la valeur.  
  
 Pour plus d’informations sur les niveaux d’accès, consultez [niveaux d’accès dans Visual Basic](../declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Pour déclarer une propriété avec des niveaux d’accès mixtes  
  
1. Déclarez la propriété de manière normale et spécifiez le niveau d’accès le moins restrictif (tel que `Public` ) dans l' `Property` instruction.  
  
2. Déclarez la `Get` procédure ou `Set` en spécifiant le niveau d’accès le plus restrictif (tel que `Friend` ).  
  
3. Ne spécifiez pas un niveau d’accès sur l’autre procédure de propriété. Il part du principe que le niveau d’accès est déclaré dans l' `Property` instruction. Vous pouvez restreindre l’accès à une seule des procédures de propriété.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     Dans l’exemple précédent, la `Get` procédure a le même `Protected` accès que la propriété elle-même, tandis que la `Set` procédure `Private` y a accès. Une classe dérivée de `employee` peut lire la `salary` valeur, mais seule la `employee` classe peut la définir.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Différences entre les propriétés et les variables en Visual Basic](./differences-between-properties-and-variables.md)
- [Comment : créer une propriété](./how-to-create-a-property.md)
- [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Comment : obtenir une valeur d'une propriété](./how-to-get-a-value-from-a-property.md)
