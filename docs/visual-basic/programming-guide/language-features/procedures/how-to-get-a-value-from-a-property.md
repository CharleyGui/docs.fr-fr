---
title: "Comment : obtenir une valeur d'une propriété"
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 983e2fd22badf4296004404d885df0a07ab2dc74
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071558"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Comment : obtenir une valeur d'une propriété (Visual Basic)

Vous récupérez la valeur d’une propriété en incluant le nom de la propriété dans une expression.  
  
 La procédure de la propriété `Get` récupère la valeur, mais vous ne l’appelez pas explicitement par nom. Vous utilisez la propriété de la même façon que vous utilisez une variable. Visual Basic effectue les appels aux procédures de la propriété.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Pour récupérer une valeur d’une propriété  
  
1. Utilisez le nom de la propriété dans une expression de la même façon que vous utilisez un nom de variable. Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.  
  
     - ou -  
  
     Utilisez le nom de propriété après le signe égal ( `=` ) dans une instruction d’assignation.  
  
     L’exemple suivant lit la valeur de la `Now` propriété Visual Basic, en appelant implicitement sa `Get` procédure.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3. Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules. Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.  
  
 La valeur de la propriété participe à l’expression de la même manière qu’une variable ou une constante, ou elle est stockée dans la variable ou la propriété à gauche de l’instruction d’assignation.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Différences entre les propriétés et les variables en Visual Basic](./differences-between-properties-and-variables.md)
- [Comment : créer une propriété](./how-to-create-a-property.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
