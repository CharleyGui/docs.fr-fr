---
title: 'Comment : placer une valeur dans une propriété'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: c0fb3e137010390097a68aea161efcff93839d94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414335"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Comment : placer une valeur dans une propriété (Visual Basic)
Vous stockez une valeur dans une propriété en plaçant le nom de la propriété sur le côté gauche d’une instruction d’assignation.  
  
 La procédure de la propriété `Set` stocke une valeur, mais vous ne l’appelez pas explicitement par nom. Vous utilisez la propriété de la même façon que vous utilisez une variable. Visual Basic effectue les appels aux procédures de la propriété.  
  
### <a name="to-store-a-value-in-a-property"></a>Pour stocker une valeur dans une propriété  
  
1. Utilisez le nom de la propriété sur le côté gauche d’une instruction d’assignation.  
  
     L’exemple suivant définit la valeur de la `TimeOfDay` propriété Visual Basic sur midi, en appelant implicitement sa `Set` procédure.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.  
  
4. La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Différences entre les propriétés et les variables en Visual Basic](./differences-between-properties-and-variables.md)
- [Comment : créer une propriété](./how-to-create-a-property.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Comment : obtenir une valeur d'une propriété](./how-to-get-a-value-from-a-property.md)
