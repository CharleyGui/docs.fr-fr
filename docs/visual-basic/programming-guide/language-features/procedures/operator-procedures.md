---
title: Procédures d'opérateur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: d62c3480db56b5cbf22c1f3f6ff59ab220a48b09
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152037"
---
# <a name="operator-procedures-visual-basic"></a>Procédures d'opérateur (Visual Basic)
Une procédure d’opérateur est une série d’instructions Visual Basic qui définissent le comportement d’un opérateur standard (tel que `*`, `<>`, ou `And`) sur une classe ou structure que vous avez défini. Cela est également appelé *surcharge d’opérateur*.  
  
## <a name="when-to-define-operator-procedures"></a>Quand définir des procédures d’opérateur  
 Lorsque vous avez défini une classe ou structure, vous pouvez déclarer des variables pour être du type de cette classe ou structure. Parfois, cette variable doit participer à une opération dans le cadre d’une expression. Pour ce faire, il doit être un opérande d’un opérateur.  
  
 Visual Basic définit les opérateurs uniquement sur ses types de données essentielles. Vous pouvez définir le comportement d’un opérateur lorsqu’une ou les deux opérandes sont du type de votre classe ou structure.  
  
 Pour plus d’informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Types de procédure d’opérateur  
 Une procédure d’opérateur peut être un des types suivants :  
  
- Définition d’un opérateur unaire où l’argument est du type de votre classe ou structure.  
  
- Une définition d’un opérateur binaire, où au moins un des arguments est du type de votre classe ou structure.  
  
- Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.  
  
- Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.  
  
 Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme l’opérateur que vous définissez.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 La syntaxe de déclaration d’une procédure d’opérateur est la suivante :  
 
 ```vb 
 Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype  
  
 ' Statements of the operator procedure.
  
 End Operator
 ```
 
 Vous utilisez le `Widening` ou `Narrowing` mot clé uniquement sur un opérateur de conversion de type. Le symbole d’opérateur est toujours [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.  
  
 Vous déclarez deux opérandes pour définir un opérateur binaire, et un seul opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type. Tous les opérandes doivent être déclarées `ByVal`.  
  
 Vous déclarez chaque opérande de la même façon que vous déclarez des paramètres pour [procédures Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Type de données  
 Étant donné que vous définissez un opérateur sur une classe ou structure que vous avez défini, au moins un des opérandes doit être du type de données de cette classe ou structure. Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou structure.  
  
 Pour plus d’informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression. Vous fournissez les opérandes de la même façon que vous le feriez pour les opérateurs prédéfinis.  
  
 La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 La structure suivante stocke une valeur entière signée de 128 bits en tant que les éléments constitutifs de poids fort et de poids faible. Il définit le `+` opérateur pour ajouter deux `veryLong` valeurs et générer résultant `veryLong` valeur.  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 L’exemple suivant montre un appel standard à la `+` opérateur défini sur `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures Function](./function-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Operator (instruction)](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Guide pratique pour Définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique pour Définir un opérateur de Conversion](./how-to-define-a-conversion-operator.md)
- [Guide pratique pour Appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md)
- [Guide pratique pour Utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
