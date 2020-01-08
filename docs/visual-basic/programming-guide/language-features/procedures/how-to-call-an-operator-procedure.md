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
ms.openlocfilehash: a977b17d4b2c797bbe38d289a57f3d9d31fa64fa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345965"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Comment : appeler une procédure d'opérateur (Visual Basic)
Vous appelez une procédure d’opérateur en utilisant le symbole d’opérateur dans une expression. Dans le cas d’un opérateur de conversion, vous appelez la [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pour convertir une valeur d’un type de données en un autre.  
  
 Vous n’appelez pas explicitement des procédures d’opérateur. Vous utilisez simplement l’opérateur, ou la fonction `CType`, dans une instruction d’assignation ou une expression, de la même façon que vous utilisez habituellement un opérateur. Visual Basic effectue l’appel à la procédure d’opérateur.  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
### <a name="to-call-an-operator-procedure"></a>Pour appeler une procédure d’opérateur  
  
1. Utilisez le symbole d’opérateur dans une expression de manière ordinaire.  
  
2. Assurez-vous que les types de données des opérandes sont appropriés pour l’opérateur et dans le bon ordre.  
  
3. L’opérateur contribue à la valeur de l’expression comme prévu.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Pour appeler une procédure d’opérateur de conversion  
  
1. Utilisez `CType` à l’intérieur d’une expression.  
  
2. Assurez-vous que les types de données des opérandes sont appropriés pour la conversion et dans le bon ordre.  
  
3. `CType` appelle la procédure d’opérateur de conversion et retourne la valeur convertie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée deux structures <xref:System.TimeSpan>, les ajoute et stocke le résultat dans une troisième <xref:System.TimeSpan> structure. La structure <xref:System.TimeSpan> définit des procédures d’opérateur pour surcharger plusieurs opérateurs standard.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Étant donné que <xref:System.TimeSpan> surcharge l’opérateur `+` standard, l’exemple précédent appelle une procédure d’opérateur lorsqu’il calcule la valeur de `combinedSpan`.  
  
 Pour obtenir un exemple d’appel d’une procédure d’opérateur de conversation, consultez [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compile-the-code"></a>Compiler le code  
 Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)
- [Operator (instruction)](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Guide pratique : déclarer une structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
