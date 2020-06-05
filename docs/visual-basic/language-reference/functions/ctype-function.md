---
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406428"
---
# <a name="ctype-function-visual-basic"></a>Fonction CType (Visual Basic)

Retourne le résultat de la conversion explicite d’une expression en un type de données, un objet, une structure, une classe ou une interface spécifiés.

## <a name="syntax"></a>Syntaxe

```vb
CType(expression, typename)
```

## <a name="parts"></a>Éléments

`expression`Toute expression valide. Si la valeur de `expression` est en dehors de la plage autorisée par `typename` , Visual Basic lève une exception.

`typename`Toute expression légale dans une `As` clause d’une `Dim` instruction, autrement dit, le nom d’un type de données, d’un objet, d’une structure, d’une classe ou d’une interface.

## <a name="remarks"></a>Notes

> [!TIP]
> Vous pouvez également utiliser les fonctions suivantes pour effectuer une conversion de type :
>
> - Les fonctions de conversion de type, telles que `CByte` , `CDbl` , et `CInt` qui effectuent une conversion vers un type de données spécifique. Pour plus d'informations, consultez [Fonctions de conversion de types de données](type-conversion-functions.md).
> - Opérateur [DirectCast](../operators/directcast-operator.md) ou [opérateur TryCast](../operators/trycast-operator.md). Ces opérateurs requièrent qu’un type hérite de ou implémente l’autre type. Elles peuvent offrir des performances légèrement supérieures à celles de `CType` la conversion vers et depuis le `Object` type de données.

`CType`est compilé en ligne, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression. Dans certains cas, le code s’exécute plus rapidement, car aucune procédure n’est appelée pour effectuer la conversion.

Si aucune conversion n’est définie à partir de `expression` à `typename` (par exemple, de `Integer` à `Date` ), Visual Basic affiche un message d’erreur au moment de la compilation.

Si une conversion échoue au moment de l’exécution, l’exception appropriée est levée. Si une conversion restrictive échoue, un <xref:System.OverflowException> est le résultat le plus courant. Si la conversion n’est pas définie, une <xref:System.InvalidCastException> exception est levée. Par exemple, cela peut se produire si `expression` est de type `Object` et que son type au moment de l’exécution n’est pas converti en `typename` .

Si le type de données de `expression` ou `typename` est une classe ou une structure que vous avez définie, vous pouvez définir `CType` sur cette classe ou structure comme opérateur de conversion. Cela fait `CType` agir en tant qu' *opérateur surchargé*. Si vous procédez ainsi, vous pouvez contrôler le comportement des conversions vers et à partir de votre classe ou structure, y compris les exceptions qui peuvent être levées.

## <a name="overloading"></a>Surcharge

L' `CType` opérateur peut également être surchargé sur une classe ou une structure définie à l’extérieur de votre code. Si votre code convertit vers ou à partir de ce type de classe ou de structure, assurez-vous de bien comprendre le comportement de son `CType` opérateur. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Conversion d’objets dynamiques

Les conversions de type des objets dynamiques sont effectuées par les conversions dynamiques définies par l’utilisateur qui utilisent les <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> méthodes ou. Si vous utilisez des objets dynamiques, utilisez la <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> méthode pour convertir l’objet dynamique.

## <a name="example"></a>Exemple

L’exemple suivant utilise la `CType` fonction pour convertir une expression en `Single` type de données.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Pour obtenir des exemples supplémentaires, consultez [conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Type Conversion Functions](type-conversion-functions.md)
- [Fonctions de conversion](conversion-functions.md)
- [Operator Statement](../statements/operator-statement.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Conversion de type dans le .NET Framework](../../../standard/base-types/type-conversion.md)
