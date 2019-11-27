---
title: 'Comment : appeler une procédure de propriété'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340552"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Comment : appeler une procédure de propriété (Visual Basic)
Vous appelez une procédure de propriété en stockant une valeur dans la propriété ou en récupérant sa valeur. Vous accédez à une propriété de la même façon que vous accédez à une variable.  
  
 La procédure `Set` de la propriété stocke une valeur, et sa procédure `Get` récupère la valeur. Toutefois, vous n’appelez pas explicitement ces procédures par nom. Vous utilisez la propriété dans une instruction d’assignation ou une expression, de la même façon que vous stockez ou récupérez la valeur d’une variable. Visual Basic effectue les appels aux procédures de la propriété.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Pour appeler la procédure d’extraction d’une propriété  
  
1. Utilisez le nom de la propriété dans une expression de la même façon que vous utilisez un nom de variable. Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.  
  
     -ou-  
  
     Utilisez le nom de propriété après le signe égal (`=`) dans une instruction d’assignation.  
  
     L’exemple suivant lit la valeur de la propriété <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>, en appelant implicitement sa procédure `Get`.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.  
  
 La valeur de la propriété participe à l’expression de la même manière qu’une variable ou une constante, ou elle est stockée dans la variable ou la propriété à gauche de l’instruction d’assignation.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Pour appeler la procédure Set d’une propriété  
  
1. Utilisez le nom de la propriété sur le côté gauche d’une instruction d’assignation.  
  
     L’exemple suivant définit la valeur de la propriété <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>, en appelant implicitement la procédure `Set`.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.  
  
 La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures de propriété](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Différences entre les propriétés et les variables dans Visual Basic](./differences-between-properties-and-variables.md)
- [Guide pratique : créer une propriété](./how-to-create-a-property.md)
- [Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
- [Get (instruction)](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set (instruction)](../../../../visual-basic/language-reference/statements/set-statement.md)
