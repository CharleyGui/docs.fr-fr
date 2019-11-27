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
ms.openlocfilehash: 0267eed7c145988d61de715fd661bd4906d8d57d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344843"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Comment : passer des arguments à une procédure (Visual Basic)
Lorsque vous appelez une procédure, vous devez suivre le nom de la procédure avec une liste d’arguments entre parenthèses. Vous fournissez un argument correspondant à chaque paramètre requis que la procédure définit et vous pouvez éventuellement fournir des arguments aux paramètres de `Optional`. Si vous ne fournissez pas de paramètre `Optional` dans l’appel, vous devez inclure une virgule pour marquer son emplacement dans la liste d’arguments si vous fournissez des arguments suivants.  
  
 Si vous envisagez de passer un argument d’un type de données différent de celui de son paramètre correspondant, par exemple `Byte` à `String`, vous pouvez définir le commutateur de vérification de type ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) sur `Off`. Si `Option Strict` est `On`, vous devez utiliser des conversions étendues ou des mots clés de conversion explicite. Pour plus d’informations, consultez [conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [fonctions de conversion de type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pour plus d’informations, consultez [paramètres et arguments](./procedure-parameters-and-arguments.md)d’une procédure.  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Pour passer un ou plusieurs arguments à une procédure  
  
1. Dans l’instruction appelante, suivez le nom de la procédure avec des parenthèses.  
  
2. À l’intérieur des parenthèses, placez une liste d’arguments. Incluez un argument pour chaque paramètre requis que la procédure définit et séparez les arguments par des virgules.  
  
3. Vérifiez que chaque argument est une expression valide qui prend la valeur d’un type de données convertible en type défini par la procédure pour le paramètre correspondant.  
  
4. Si un paramètre est défini comme [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md), vous pouvez l’inclure dans la liste d’arguments ou l’omettre. Si vous l’omettez, la procédure utilise la valeur par défaut définie pour ce paramètre.  
  
5. Si vous omettez un argument pour un paramètre `Optional` et qu’il existe un autre paramètre après celui-ci dans la liste des paramètres, vous pouvez marquer la place de l’argument omis par une virgule supplémentaire dans la liste d’arguments.  
  
     L’exemple suivant appelle la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> Visual Basic.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     L’exemple précédent fournit le premier argument requis, qui est la chaîne de message à afficher. Il omet un argument pour le deuxième paramètre facultatif, qui spécifie les boutons à afficher dans la boîte de message. Étant donné que l’appel ne fournit pas de valeur, `MsgBox` utilise la valeur par défaut, `MsgBoxStyle.OKOnly`, qui n’affiche que le bouton **OK** .  
  
     La deuxième virgule de la liste d’arguments marque l’emplacement du deuxième argument omis et la dernière chaîne est passée au troisième paramètre facultatif de `MsgBox`, qui est le texte à afficher dans la barre de titre.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures Sub](./sub-procedures.md)
- [Procédures Function](./function-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Procédures récursives](./recursive-procedures.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
