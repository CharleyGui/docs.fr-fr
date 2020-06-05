---
title: Procédures d'opérateur
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
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364316"
---
# <a name="operator-procedures-visual-basic"></a>Procédures d'opérateur (Visual Basic)

Une procédure d’opérateur est une série d’instructions Visual Basic qui définissent le comportement d’un opérateur standard (tel que `*` , `<>` ou `And` ) sur une classe ou une structure que vous avez définie. C’est ce que l’on appelle également la *surcharge d’opérateur*.

## <a name="when-to-define-operator-procedures"></a>Quand définir des procédures d’opérateur

Lorsque vous avez défini une classe ou une structure, vous pouvez déclarer des variables comme étant du type de cette classe ou structure. Parfois, une telle variable doit participer à une opération dans le cadre d’une expression. Pour ce faire, il doit s’agir d’un opérande d’un opérateur.

Visual Basic définit des opérateurs uniquement sur ses types de données fondamentaux. Vous pouvez définir le comportement d’un opérateur quand l’un des opérandes ou les deux sont du type de votre classe ou structure.

Pour plus d’informations, consultez [Operator, instruction](../../../language-reference/statements/operator-statement.md).

## <a name="types-of-operator-procedure"></a>Types de procédure d’opérateur

Une procédure d’opérateur peut être de l’un des types suivants :

- Définition d’un opérateur unaire dans lequel l’argument est du type de votre classe ou structure.

- Définition d’un opérateur binaire où au moins l’un des arguments est du type de votre classe ou structure.

- Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.

- Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.

 Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme opérateur que vous définissez.

## <a name="declaration-syntax"></a>Syntaxe de déclaration

La syntaxe de la déclaration d’une procédure d’opérateur est la suivante :

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

Vous utilisez le `Widening` `Narrowing` mot clé ou uniquement sur un opérateur de conversion de type. Le symbole d’opérateur est toujours la [fonction CType](../../../language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.

Vous pouvez déclarer deux opérandes pour définir un opérateur binaire et déclarer un opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type. Tous les opérandes doivent être déclarés `ByVal` .

Vous déclarez chaque opérande de la même façon que vous déclarez des paramètres pour les [procédures Sub](./sub-procedures.md).

### <a name="data-type"></a>Type de données

Étant donné que vous définissez un opérateur sur une classe ou une structure que vous avez définie, au moins l’un des opérandes doit être du type de données de cette classe ou structure. Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou de la structure.

Pour plus d’informations, consultez [Operator, instruction](../../../language-reference/statements/operator-statement.md).

## <a name="calling-syntax"></a>Syntaxe d’appel

Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression. Vous fournissez les opérandes de la même façon que pour les opérateurs prédéfinis.

La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :

`Dim testStruct As`  *structurename*

`Dim testNewStruct As`  *structurename* `= testStruct` *operatorsymbol*      `10`

### <a name="illustration-of-declaration-and-call"></a>Illustration de la déclaration et de l’appel

La structure suivante stocke une valeur d’entier 128 bits signée comme parties de poids fort et de poids faible constituantes. Il définit l' `+` opérateur pour ajouter deux `veryLong` valeurs et générer une valeur résultante `veryLong` .

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

L’exemple suivant montre un appel typique à l' `+` opérateur défini sur `veryLong` .

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Sub, procédures](./sub-procedures.md)
- [Function, procédures](./function-procedures.md)
- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Operator Statement](../../../language-reference/statements/operator-statement.md)
- [Comment : définir un opérateur](./how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)
- [Comment : appeler une procédure d'opérateur](./how-to-call-an-operator-procedure.md)
- [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
