---
title: Fonction CType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592097"
---
# <a name="ctype-function-visual-basic"></a>Fonction CType (Visual Basic)

Retourne le résultat de la conversion explicite d’une expression en un type de données, un objet, une structure, une classe ou une interface spécifiés.

## <a name="syntax"></a>Syntaxe

```vb
CType(expression, typename)
```

## <a name="parts"></a>Composants

`expression` toute expression valide. Si la valeur de `expression` est en dehors de la plage autorisée par `typename`, Visual Basic lève une exception.

`typename` toute expression légale dans une clause `As` dans une instruction `Dim`, autrement dit, le nom d’un type de données, d’un objet, d’une structure, d’une classe ou d’une interface.

## <a name="remarks"></a>Notes

> [!TIP]
> Vous pouvez également utiliser les fonctions suivantes pour effectuer une conversion de type :
>
> - Les fonctions de conversion de type, telles que `CByte`, `CDbl` et `CInt` qui effectuent une conversion vers un type de données spécifique. Pour plus d’informations, consultez [fonctions de conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).
> - Opérateur [DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md). Ces opérateurs requièrent qu’un type hérite de ou implémente l’autre type. Ils peuvent fournir des performances légèrement meilleures que `CType` lors de la conversion vers et à partir du type de données `Object`.

`CType` est compilé en ligne, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression. Dans certains cas, le code s’exécute plus rapidement, car aucune procédure n’est appelée pour effectuer la conversion.

Si aucune conversion n’est définie de `expression` à `typename` (par exemple, de `Integer` à `Date`), Visual Basic affiche un message d’erreur au moment de la compilation.

Si une conversion échoue au moment de l’exécution, l’exception appropriée est levée. En cas d’échec d’une conversion restrictive, un <xref:System.OverflowException> est le résultat le plus courant. Si la conversion n’est pas définie, un <xref:System.InvalidCastException> dans est levé. Par exemple, cela peut se produire si `expression` est de type `Object` et que son type au moment de l’exécution n’est pas converti en `typename`.

Si le type de données de `expression` ou `typename` est une classe ou une structure que vous avez définie, vous pouvez définir `CType` sur cette classe ou structure comme opérateur de conversion. Cela rend `CType` agir comme *opérateur surchargé*. Si vous procédez ainsi, vous pouvez contrôler le comportement des conversions vers et à partir de votre classe ou structure, y compris les exceptions qui peuvent être levées.

## <a name="overloading"></a>Surcharge

L’opérateur `CType` peut également être surchargé sur une classe ou une structure définie à l’extérieur de votre code. Si votre code convertit vers ou à partir de ce type de classe ou de structure, assurez-vous de bien comprendre le comportement de son opérateur `CType`. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Conversion d’objets dynamiques

Les conversions de type des objets dynamiques sont effectuées par les conversions dynamiques définies par l’utilisateur qui utilisent les méthodes <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>. Si vous utilisez des objets dynamiques, utilisez la méthode <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> pour convertir l’objet dynamique.

## <a name="example"></a>Exemple

L’exemple suivant utilise la fonction `CType` pour convertir une expression en type de données `Single`.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Pour obtenir des exemples supplémentaires, consultez [conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Fonctions de conversion](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Guide pratique pour Définir un opérateur de conversion @ no__t-0
- [Conversion de type dans le .NET Framework](../../../standard/base-types/type-conversion.md)
