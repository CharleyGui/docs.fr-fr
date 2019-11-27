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
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344899"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Comment : définir un opérateur de conversion (Visual Basic)
Si vous avez défini une classe ou une structure, vous pouvez définir un opérateur de conversion de type entre le type de votre classe ou structure et un autre type de données (tel que `Integer`, `Double`ou `String`).  
  
 Définissez la conversion de type comme une procédure de [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md) dans la classe ou la structure. Toutes les procédures de conversion doivent être `Public Shared`, et chacune d’elles doit spécifier l' [élargissement](../../../../visual-basic/language-reference/modifiers/widening.md) ou la [réduction](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit des opérateurs de conversion entre une structure appelée `digit` et un `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Vous pouvez tester la structure `digit` avec le code suivant.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique : appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md)
- [Guide pratique : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Guide pratique : déclarer une structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
