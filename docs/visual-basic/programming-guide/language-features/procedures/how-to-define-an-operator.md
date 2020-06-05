---
title: 'Comment : définir un opérateur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388035"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Comment : définir un opérateur (Visual Basic)
Si vous avez défini une classe ou une structure, vous pouvez définir le comportement d’un opérateur standard (tel que `*` , `<>` ou `And` ) quand l’un des opérandes ou les deux sont du type de votre classe ou structure.  
  
 Définissez l’opérateur standard comme une procédure d’opérateur dans la classe ou la structure. Toutes les procédures d’opérateur doivent être `Public` `Shared` .  
  
 La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit l' `+` opérateur pour une structure appelée `height` . La structure utilise des hauteurs mesurées en mètres et en pouces. Un *pouce* est de 2,54 centimètres, et un *pied* est de 12 pouces. Pour garantir des valeurs normalisées (pouces < 12,0), le constructeur effectue une opération arithmétique *modulo* 12. L' `+` opérateur utilise le constructeur pour générer des valeurs normalisées.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Vous pouvez tester la structure `height` à l’aide du code suivant.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Voir aussi

- [Procédures d'opérateur](./operator-procedures.md)
- [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)
- [Comment : appeler une procédure d'opérateur](./how-to-call-an-operator-procedure.md)
- [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../language-reference/statements/operator-statement.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
- [Procédure : Déclarer une structure](../data-types/how-to-declare-a-structure.md)
- [Mod, opérateur](../../../language-reference/operators/mod-operator.md)
