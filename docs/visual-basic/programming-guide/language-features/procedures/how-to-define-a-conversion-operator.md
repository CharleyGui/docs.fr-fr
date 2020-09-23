---
title: 'Comment : définir un opérateur de conversion'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085670"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Comment : définir un opérateur de conversion (Visual Basic)

Si vous avez défini une classe ou une structure, vous pouvez définir un opérateur de conversion de type entre le type de votre classe ou structure et un autre type de données (tel que `Integer` , `Double` ou `String` ).  
  
 Définissez la conversion de type comme une procédure de [fonction CType](../../../language-reference/functions/ctype-function.md) dans la classe ou la structure. Toutes les procédures de conversion doivent avoir la `Public Shared` valeur et chacune d’elles doit spécifier l' [élargissement](../../../language-reference/modifiers/widening.md) ou la [réduction](../../../language-reference/modifiers/narrowing.md).  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant définit des opérateurs de conversion entre une structure appelée `digit` et un `Byte` .  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Vous pouvez tester la structure `digit` à l’aide du code suivant.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures d'opérateur](./operator-procedures.md)
- [Comment : définir un opérateur](./how-to-define-an-operator.md)
- [Comment : appeler une procédure d'opérateur](./how-to-call-an-operator-procedure.md)
- [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../language-reference/statements/operator-statement.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
- [Procédure : Déclarer une structure](../data-types/how-to-declare-a-structure.md)
- [Conversions implicites et explicites](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
