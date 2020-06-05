---
title: "Comment : appeler une procédure d'opérateur"
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: fa2bc5417b8b917ff48502a5bd0a4daa21fab67e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388567"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Comment : appeler une procédure d'opérateur (Visual Basic)
Vous appelez une procédure d’opérateur en utilisant le symbole d’opérateur dans une expression. Dans le cas d’un opérateur de conversion, vous appelez la [fonction CType](../../../language-reference/functions/ctype-function.md) pour convertir une valeur d’un type de données en un autre.  
  
 Vous n’appelez pas explicitement des procédures d’opérateur. Vous utilisez simplement l’opérateur, ou la `CType` fonction, dans une instruction d’assignation ou une expression, de la même façon que vous utilisez habituellement un opérateur. Visual Basic effectue l’appel à la procédure d’opérateur.  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
### <a name="to-call-an-operator-procedure"></a>Pour appeler une procédure d’opérateur  
  
1. Utilisez le symbole d’opérateur dans une expression de manière ordinaire.  
  
2. Assurez-vous que les types de données des opérandes sont appropriés pour l’opérateur et dans le bon ordre.  
  
3. L’opérateur contribue à la valeur de l’expression comme prévu.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Pour appeler une procédure d’opérateur de conversion  
  
1. Utilisez `CType` dans une expression.  
  
2. Assurez-vous que les types de données des opérandes sont appropriés pour la conversion et dans le bon ordre.  
  
3. `CType`appelle la procédure d’opérateur de conversion et retourne la valeur convertie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée deux <xref:System.TimeSpan> structures, les ajoute et stocke le résultat dans une troisième <xref:System.TimeSpan> structure. La <xref:System.TimeSpan> structure définit des procédures d’opérateur pour surcharger plusieurs opérateurs standard.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Comme <xref:System.TimeSpan> surcharge de l’opérateur standard `+` , l’exemple précédent appelle une procédure d’opérateur lorsqu’il calcule la valeur de `combinedSpan` .  
  
 Pour obtenir un exemple d’appel d’une procédure d’opérateur de conversation, consultez [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compile-the-code"></a>Compiler le code  
 Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures d'opérateur](./operator-procedures.md)
- [Comment : définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)
- [Operator Statement](../../../language-reference/statements/operator-statement.md)
- [Widening](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
- [Procédure : Déclarer une structure](../data-types/how-to-declare-a-structure.md)
- [Conversions implicites et explicites](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
