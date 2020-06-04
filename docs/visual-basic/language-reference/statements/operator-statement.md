---
title: Operator Statement
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404393"
---
# <a name="operator-statement"></a>Operator Statement

Déclare le symbole d’opérateur, les opérandes et le code qui définissent une procédure d’opérateur sur une classe ou une structure.

## <a name="syntax"></a>Syntaxe

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a>Éléments

`attrlist`  
Facultatif. Consultez la [liste des attributs](attribute-list.md).

`Public`  
Obligatoire. Indique que cette procédure d’opérateur a un accès [public](../modifiers/public.md) .

`Overloads`  
Facultatif. Consultez [Overloads](../modifiers/overloads.md).

`Shared`  
Obligatoire. Indique que la procédure d’opérateur est une procédure [partagée](../modifiers/shared.md) .

`Shadows`  
Facultatif. Consultez [Shadows](../modifiers/shadows.md).

`Widening`  
Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Narrowing` . Indique que cette procédure d’opérateur définit une conversion [étendue](../modifiers/widening.md) . Pour plus d’informations, consultez « Conversions étendues et restrictives » dans cette page d’aide.

`Narrowing`  
Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Widening` . Indique que cette procédure d’opérateur définit une conversion [restrictive](../modifiers/narrowing.md) . Pour plus d’informations, consultez « Conversions étendues et restrictives » dans cette page d’aide.

`operatorsymbol`  
Obligatoire. Symbole ou identificateur de l’opérateur défini par cette procédure d’opérateur.

`operand1`  
Obligatoire. Nom et type de l’opérande unique d’un opérateur unaire (y compris un opérateur de conversion) ou de l’opérande gauche d’un opérateur binaire.

`operand2`  
Requis pour les opérateurs binaires. Nom et type de l’opérande droit d’un opérateur binaire.

`operand1`et `operand2` ont la syntaxe et les éléments suivants :

`[ ByVal ] operandname [ As operandtype ]`

|Élément|Description|
|----------|-----------------|
|`ByVal`|Facultatif, mais le mécanisme de passage doit être [ByVal](../modifiers/byval.md).|
|`operandname`|Obligatoire. Nom de la variable représentant cet opérande. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|Facultatif, sauf si `Option Strict` est `On` . Type de données de cet opérande.|

`type`  
Facultatif, sauf si `Option Strict` est `On` . Type de données de la valeur retournée par la procédure d’opérateur.

`statements`  
Facultatif. Bloc d’instructions exécutées par la procédure d’opérateur.

`returnvalue`  
Obligatoire. Valeur que la procédure d’opérateur retourne au code appelant.

`End` `Operator`  
Obligatoire. Met fin à la définition de cette procédure d’opérateur.

## <a name="remarks"></a>Notes

Vous pouvez utiliser `Operator` uniquement dans une classe ou une structure. Cela signifie que le *contexte de déclaration* pour un opérateur ne peut pas être un fichier source, un espace de noms, un module, une interface, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Tous les opérateurs doivent être `Public Shared` . Vous ne pouvez pas spécifier `ByRef` , `Optional` ou `ParamArray` pour l’un des opérandes.

Vous ne pouvez pas utiliser le symbole ou l’identificateur d’opérateur pour contenir une valeur de retour. Vous devez utiliser l' `Return` instruction et vous devez spécifier une valeur. N’importe quel nombre d' `Return` instructions peut apparaître n’importe où dans la procédure.

La définition d’un opérateur de cette manière est appelée *surcharge d’opérateur*, que vous utilisiez ou non le `Overloads` mot clé. Le tableau suivant présente les opérateurs que vous pouvez définir.

|Type|Opérateurs|
|----------|---------------|
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|Binaire|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|Conversion (unaire)|`CType`|

Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.

Lorsque vous définissez `CType` , vous devez spécifier `Widening` ou `Narrowing` .

## <a name="matched-pairs"></a>Paires correspondantes

Vous devez définir certains opérateurs comme paires correspondantes. Si vous définissez l’un des opérateurs d’une telle paire, vous devez également définir l’autre opérateur. Les paires correspondantes sont les suivantes :

- `=` et `<>`

- `>` et `<`

- `>=` et `<=`

- `IsTrue` et `IsFalse`

## <a name="data-type-restrictions"></a>Restrictions relatives aux types de données

Chaque opérateur que vous définissez doit impliquer la classe ou la structure sur laquelle vous le définissez. Cela signifie que la classe ou la structure doit apparaître comme type de données des éléments suivants :

- Opérande d’un opérateur unaire.

- Au moins l’un des opérandes d’un opérateur binaire.

- L’opérande ou le type de retour d’un opérateur de conversion.

 Certains opérateurs ont des restrictions de type de données supplémentaires, comme suit :

- Si vous définissez les `IsTrue` `IsFalse` opérateurs et, ils doivent tous les deux retourner le `Boolean` type.

- Si vous définissez les `<<` `>>` opérateurs et, ils doivent spécifier le `Integer` type du `operandtype` de `operand2` .

Le type de retour ne doit pas nécessairement correspondre au type de l’un des opérandes. Par exemple, un opérateur de comparaison tel que `=` ou `<>` peut retourner `Boolean` même si aucun des opérandes n’est `Boolean` .

## <a name="logical-and-bitwise-operators"></a>Opérateurs de bits et opérateurs logiques

Les `And` opérateurs,, `Or` `Not` et `Xor` peuvent effectuer des opérations logiques ou au niveau du bit dans Visual Basic. Toutefois, si vous définissez l’un de ces opérateurs sur une classe ou une structure, vous pouvez définir uniquement son opération au niveau du bit.

Vous ne pouvez pas définir l' `AndAlso` opérateur directement avec une `Operator` instruction. Toutefois, vous pouvez utiliser `AndAlso` si vous avez rempli les conditions suivantes :

- Vous avez défini `And` sur les mêmes types d’opérande que pour `AndAlso` .

- Votre définition de `And` retourne le même type que la classe ou la structure sur laquelle vous l’avez défini.

- Vous avez défini l' `IsFalse` opérateur sur la classe ou la structure sur laquelle vous avez défini `And` .

De même, vous pouvez utiliser `OrElse` si vous avez défini `Or` sur les mêmes opérandes, avec le type de retour de la classe ou de la structure, et que vous avez défini `IsTrue` sur la classe ou la structure.

## <a name="widening-and-narrowing-conversions"></a>Widening and Narrowing Conversions

Une *conversion étendue* réussit toujours au moment de l’exécution, tandis qu’une *conversion restrictive* peut échouer au moment de l’exécution. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

Si vous déclarez une procédure de conversion comme étant `Widening` , votre code de procédure ne doit pas générer d’échec. Cela signifie :

- Elle doit toujours retourner une valeur valide de type `type` .

- Elle doit gérer toutes les exceptions possibles et d’autres conditions d’erreur.

- Il doit gérer toutes les erreurs renvoyées par les procédures qu’il appelle.

S’il est possible qu’une procédure de conversion échoue ou qu’elle provoque une exception non gérée, vous devez la déclarer comme étant `Narrowing` .

## <a name="example"></a>Exemple

L’exemple de code suivant utilise l' `Operator` instruction pour définir le plan d’une structure qui comprend des procédures d’opérateur pour les `And` `Or` opérateurs,, `IsFalse` et `IsTrue` . `And`et `Or` chacune prennent deux opérandes de type `abc` et de type de retour `abc` . `IsFalse`et, `IsTrue` chacun prennent un opérande unique de type `abc` et retourne `Boolean` . Ces définitions permettent au code appelant d’utiliser `And` , `AndAlso` , `Or` et `OrElse` avec des opérandes de type `abc` .

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Voir aussi

- [IsFalse, opérateur](../operators/isfalse-operator.md)
- [IsTrue, opérateur](../operators/istrue-operator.md)
- [Widening](../modifiers/widening.md)
- [Narrowing](../modifiers/narrowing.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Procédures d'opérateur](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Comment : appeler une procédure d'opérateur](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Comment : utiliser une classe qui définit des opérateurs](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
