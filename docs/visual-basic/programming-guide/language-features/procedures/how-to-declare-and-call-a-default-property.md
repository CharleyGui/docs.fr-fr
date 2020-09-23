---
title: 'Guide pratique : déclarer et appeler une propriété par défaut'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 21aa6e6a9bba23d767b9d1fac610eaac3265550d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087451"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Comment : déclarer et appeler une propriété par défaut en Visual Basic

Une *propriété par défaut* est une propriété de classe ou de structure à laquelle votre code peut accéder sans la spécifier. Quand le code appelant nomme une classe ou une structure, mais pas une propriété, et que le contexte autorise l’accès à une propriété, Visual Basic résout l’accès à la propriété par défaut de cette classe ou de cette structure, le cas échéant.  
  
 Une classe ou une structure peut avoir au plus une propriété par défaut. Toutefois, vous pouvez surcharger une propriété par défaut et avoir plusieurs versions de celle-ci.  
  
 Pour plus d’informations, consultez [default](../../../language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Pour déclarer une propriété par défaut  
  
1. Déclarez la propriété de manière normale. Ne spécifiez pas `Shared` le `Private` mot clé ou.  
  
2. Incluez le `Default` mot clé dans la déclaration de propriété.  
  
3. Spécifiez au moins un paramètre pour la propriété. Vous ne pouvez pas définir une propriété par défaut qui ne prend pas au moins un argument.  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>Pour appeler une propriété par défaut  
  
1. Déclarez une variable du type de la classe ou de la structure conteneur.  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. Utilisez le nom de variable seul dans une expression où vous incluiez normalement le nom de la propriété.  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. Faites suivre le nom de la variable d’une liste d’arguments entre parenthèses. Une propriété par défaut doit accepter au moins un argument.  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. Pour récupérer la valeur de propriété par défaut, utilisez le nom de la variable, avec une liste d’arguments, dans une expression ou après le signe égal ( `=` ) dans une instruction d’assignation.  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. Pour définir la valeur de la propriété par défaut, utilisez le nom de la variable, avec une liste d’arguments, sur le côté gauche d’une instruction d’assignation.  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. Vous pouvez toujours spécifier le nom de la propriété par défaut avec le nom de la variable, comme vous le feriez pour accéder à une autre propriété.  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant déclare une propriété par défaut sur une classe.  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment appeler la propriété default `myProperty` sur la classe `class1` . Les trois instructions d’assignation stockent des valeurs dans `myProperty` , et l' <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> appel lit les valeurs.  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 L’utilisation la plus courante d’une propriété par défaut est la <xref:Microsoft.VisualBasic.Collection.Item%2A> propriété sur différentes classes de collection.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les propriétés par défaut peuvent entraîner une petite réduction des caractères de code source, mais elles peuvent rendre votre code plus difficile à lire. Si le code appelant n’est pas familiarisé avec votre classe ou structure, lorsqu’il fait référence au nom de la classe ou de la structure, il ne peut pas être certain que cette référence accède à la classe ou à la structure elle-même, ou à une propriété par défaut. Cela peut entraîner des erreurs de compilation ou des erreurs de logique d’exécution subtiles.  
  
 Vous pouvez réduire légèrement les risques d’erreurs de propriété par défaut en utilisant toujours l' [instruction Option Strict](../../../language-reference/statements/option-strict-statement.md) pour définir la vérification du type de compilateur sur `On` .  
  
 Si vous envisagez d’utiliser une classe ou une structure prédéfinie dans votre code, vous devez déterminer si elle a une propriété par défaut et, dans ce cas, son nom.  
  
 En raison de ces inconvénients, vous devez envisager de ne pas définir de propriétés par défaut. Pour une meilleure lisibilité du code, vous devez également penser à toujours faire référence à toutes les propriétés explicitement, même les propriétés par défaut.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Par défaut](../../../language-reference/modifiers/default.md)
- [Différences entre les propriétés et les variables en Visual Basic](./differences-between-properties-and-variables.md)
- [Comment : créer une propriété](./how-to-create-a-property.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Comment : obtenir une valeur d'une propriété](./how-to-get-a-value-from-a-property.md)
