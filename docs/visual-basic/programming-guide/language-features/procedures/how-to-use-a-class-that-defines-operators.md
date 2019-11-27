---
title: 'Comment : utiliser une classe qui définit des opérateurs'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 9ec4b4c07910100dd02cc86e882b44aa7dbd2ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346039"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Comment : utiliser une classe qui définit des opérateurs (Visual Basic)
Si vous utilisez une classe ou une structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs à partir de Visual Basic.  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString>, qui définit les opérateurs de conversion ([fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) dans les deux directions entre une chaîne SQL et une chaîne Visual Basic. Utilisez `CType(`*expression de chaîne SQL*, `String)` pour convertir une chaîne SQL en une chaîne Visual Basic et `CType(`*Visual Basic expression de chaîne*, <xref:System.Data.SqlTypes.SqlString>`)` pour la convertir dans l’autre sens.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 La structure <xref:System.Data.SqlTypes.SqlString> définit un opérateur de conversion ([fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` à <xref:System.Data.SqlTypes.SqlString> et une autre <xref:System.Data.SqlTypes.SqlString> à `String`. L’instruction qui assigne `title` à `jobTitle` utilise le premier opérateur, et l’appel de fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> utilise la seconde.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser. Ne partez pas du principe que la classe ou la structure a défini chaque opérateur disponible pour la surcharge. Pour obtenir la liste des opérateurs disponibles, consultez [instruction Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Incluez l’instruction de `Imports` appropriée pour la chaîne SQL au début de votre fichier source (dans ce cas <xref:System.Data.SqlTypes>).  
  
 Votre projet doit avoir des références à System. Data et System. XML.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)
- [Guide pratique : appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Guide pratique : déclarer une structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
