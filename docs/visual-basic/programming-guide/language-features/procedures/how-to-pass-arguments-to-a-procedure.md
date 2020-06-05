---
title: 'Comment : passer des arguments à une procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387775"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Comment : passer des arguments à une procédure (Visual Basic)
Lorsque vous appelez une procédure, vous devez suivre le nom de la procédure avec une liste d’arguments entre parenthèses. Vous fournissez un argument correspondant à chaque paramètre requis que la procédure définit et vous pouvez éventuellement fournir des arguments aux `Optional` paramètres. Si vous ne fournissez pas `Optional` de paramètre dans l’appel, vous devez inclure une virgule pour marquer son emplacement dans la liste d’arguments si vous fournissez des arguments suivants.  
  
 Si vous envisagez de passer un argument d’un type de données différent de celui de son paramètre correspondant, par exemple `Byte` à `String` , vous pouvez définir le commutateur de vérification de type ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) sur `Off` . Si `Option Strict` est `On` , vous devez utiliser des conversions étendues ou des mots clés de conversion explicite. Pour plus d’informations, consultez [conversions étendues et restrictives](../data-types/widening-and-narrowing-conversions.md) et [fonctions de conversion de type](../../../language-reference/functions/type-conversion-functions.md).  
  
 Pour plus d’informations, consultez [paramètres et arguments](./procedure-parameters-and-arguments.md)d’une procédure.  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Pour passer un ou plusieurs arguments à une procédure  
  
1. Dans l’instruction appelante, suivez le nom de la procédure avec des parenthèses.  
  
2. À l’intérieur des parenthèses, placez une liste d’arguments. Incluez un argument pour chaque paramètre requis que la procédure définit et séparez les arguments par des virgules.  
  
3. Vérifiez que chaque argument est une expression valide qui prend la valeur d’un type de données convertible en type défini par la procédure pour le paramètre correspondant.  
  
4. Si un paramètre est défini comme [facultatif](../../../language-reference/modifiers/optional.md), vous pouvez l’inclure dans la liste d’arguments ou l’omettre. Si vous l’omettez, la procédure utilise la valeur par défaut définie pour ce paramètre.  
  
5. Si vous omettez un argument pour un `Optional` paramètre et qu’il existe un autre paramètre après celui-ci dans la liste de paramètres, vous pouvez marquer la place de l’argument omis par une virgule supplémentaire dans la liste d’arguments.  
  
     L’exemple suivant appelle la <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> fonction Visual Basic.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     L’exemple précédent fournit le premier argument requis, qui est la chaîne de message à afficher. Il omet un argument pour le deuxième paramètre facultatif, qui spécifie les boutons à afficher dans la boîte de message. Étant donné que l’appel ne fournit pas de valeur, `MsgBox` utilise la valeur par défaut, `MsgBoxStyle.OKOnly` , qui affiche uniquement un bouton **OK** .  
  
     La deuxième virgule de la liste d’arguments marque l’emplacement du deuxième argument omis et la dernière chaîne est passée au troisième paramètre facultatif de `MsgBox` , qui est le texte à afficher dans la barre de titre.  
  
## <a name="see-also"></a>Voir aussi

- [Sub, procédures](./sub-procedures.md)
- [Function, procédures](./function-procedures.md)
- [Procédures Property](./property-procedures.md)
- [Procédures d'opérateur](./operator-procedures.md)
- [Comment : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Procédures récursives](./recursive-procedures.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Objets et classes](../objects-and-classes/index.md)
- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
