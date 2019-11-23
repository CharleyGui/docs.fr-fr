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
ms.openlocfilehash: 18b2d5a28cd6ef885ba8d237da6764dbbd108b59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348094"
---
# <a name="ctype-function-visual-basic"></a>Fonction CType (Visual Basic)

Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.

## <a name="syntax"></a>Syntaxe

```vb
CType(expression, typename)
```

## <a name="parts"></a>Composants

`expression` Any valid expression. If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.

`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.

## <a name="remarks"></a>Notes

> [!TIP]
> You can also use the following functions to perform a type conversion:
>
> - Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type. For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).
> - [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md). These operators require that one type inherit from or implement the other type. They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.

`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression. In some cases, the code runs faster because no procedures are called to perform the conversion.

If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.

If a conversion fails at run time, the appropriate exception is thrown. If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result. If the conversion is undefined, an <xref:System.InvalidCastException> in thrown. For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.

If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator. This makes `CType` act as an *overloaded operator*. If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.

## <a name="overloading"></a>Surcharge

The `CType` operator can also be overloaded on a class or structure defined outside your code. If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Converting Dynamic Objects

Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods. If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.

## <a name="example"></a>Exemple

The following example uses the `CType` function to convert an expression to the `Single` data type.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Fonctions de conversion](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Guide pratique : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Conversion de type dans le .NET Framework](../../../standard/base-types/type-conversion.md)
