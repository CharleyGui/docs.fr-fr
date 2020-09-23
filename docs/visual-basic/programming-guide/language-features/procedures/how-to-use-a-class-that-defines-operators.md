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
ms.openlocfilehash: 083916a420bf4ad182536363ea46448f6b4c1da5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071350"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Comment : utiliser une classe qui définit des opérateurs (Visual Basic)

Si vous utilisez une classe ou une structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs à partir de Visual Basic.  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString> , qui définit les opérateurs de conversion ([fonction CType](../../../language-reference/functions/ctype-function.md)) dans les deux directions entre une chaîne SQL et une chaîne de Visual Basic. Utilisez `CType(` l' *expression de chaîne SQL* `String)` pour convertir une chaîne SQL en une chaîne de Visual Basic, et `CType(` *Visual Basic expression de chaîne*, <xref:System.Data.SqlTypes.SqlString> `)` pour convertir dans l’autre direction.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 La <xref:System.Data.SqlTypes.SqlString> structure définit un opérateur de conversion ([fonction CType](../../../language-reference/functions/ctype-function.md)) de `String` à <xref:System.Data.SqlTypes.SqlString> et un autre de à <xref:System.Data.SqlTypes.SqlString> `String` . L’instruction qui assigne `title` à utilise `jobTitle` le premier opérateur, et l’appel de <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> fonction utilise la seconde.  
  
## <a name="compile-the-code"></a>Compiler le code  

 Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser. Ne partez pas du principe que la classe ou la structure a défini chaque opérateur disponible pour la surcharge. Pour obtenir la liste des opérateurs disponibles, consultez [instruction Operator](../../../language-reference/statements/operator-statement.md).  
  
 Incluez l' `Imports` instruction appropriée pour la chaîne SQL au début de votre fichier source (dans ce cas <xref:System.Data.SqlTypes> ).  
  
 Votre projet doit avoir des références à System. Data et System.XML.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures d'opérateur](./operator-procedures.md)
- [Comment : définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)
- [Comment : appeler une procédure d'opérateur](./how-to-call-an-operator-procedure.md)
- [Widening](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
- [Procédure : Déclarer une structure](../data-types/how-to-declare-a-structure.md)
- [Conversions implicites et explicites](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
