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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349698"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Comment : déclarer une propriété avec des niveaux d'accès mixtes (Visual Basic)
Si vous souhaitez que les procédures `Get` et `Set` sur une propriété aient des niveaux d’accès différents, vous pouvez utiliser le niveau le plus permissif dans l’instruction `Property` et le niveau le plus restrictif dans l’instruction `Get` ou `Set`. Vous utilisez des niveaux d’accès mixtes sur une propriété lorsque vous souhaitez que certaines parties du code soient en mesure d’obtenir la valeur de la propriété, et que certaines autres parties du code soient en mesure de modifier la valeur.  
  
 Pour plus d’informations sur les niveaux d’accès, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Pour déclarer une propriété avec des niveaux d’accès mixtes  
  
1. Déclarez la propriété de manière normale et spécifiez le niveau d’accès le moins restrictif (par exemple `Public`) dans l’instruction `Property`.  
  
2. Déclarez l' `Get` ou la procédure `Set` spécifiant le niveau d’accès le plus restrictif (par exemple, `Friend`).  
  
3. Ne spécifiez pas un niveau d’accès sur l’autre procédure de propriété. Il part du principe que le niveau d’accès est déclaré dans l’instruction `Property`. Vous pouvez restreindre l’accès à une seule des procédures de propriété.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     Dans l’exemple précédent, la procédure `Get` a les mêmes `Protected` accès que la propriété elle-même, tandis que la procédure `Set` a `Private` accès. Une classe dérivée de `employee` peut lire la valeur `salary`, mais seule la classe `employee` peut la définir.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures de propriété](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Différences entre les propriétés et les variables dans Visual Basic](./differences-between-properties-and-variables.md)
- [Guide pratique : créer une propriété](./how-to-create-a-property.md)
- [Guide pratique : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
