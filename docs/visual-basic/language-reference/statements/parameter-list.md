---
title: Liste de paramètres
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: ec4ce0f12b540478d889832fb18f1ef008613f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346479"
---
# <a name="parameter-list-visual-basic"></a>Liste de paramètres (Visual Basic)

Specifies the parameters a procedure expects when it is called. Multiple parameters are separated by commas. The following is the syntax for one parameter.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>Composants

`attributelist`  
Optionnel. List of attributes that apply to this parameter. You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").

`Optional`  
Optionnel. Specifies that this parameter is not required when the procedure is called.

`ByVal`  
Optionnel. Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.

`ByRef`  
Optionnel. Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.

`ParamArray`  
Optionnel. Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type. This lets the calling code pass an arbitrary number of arguments to the procedure.

`parametername`  
Requis. Name of the local variable representing the parameter.

`parametertype`  
Required if `Option Strict` is `On`. Data type of the local variable representing the parameter.

`defaultvalue`  
Required for `Optional` parameters. Any constant or constant expression that evaluates to the data type of the parameter. If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.

## <a name="remarks"></a>Notes

Parameters are surrounded by parentheses and separated by commas. A parameter can be declared with any data type. If you do not specify `parametertype`, it defaults to `Object`.

When the calling code calls the procedure, it passes an *argument* to each required parameter. For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code. If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it. If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it. For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

If a variable element is passed `ByRef`, the procedure can change it as well. For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Règles

- **Parentheses.** If you specify a parameter list, you must enclose it in parentheses. If there are no parameters, you can still use parentheses enclosing an empty list. This improves the readability of your code by clarifying that the element is a procedure.

- **Optional Parameters.** If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.

     Every optional parameter declaration must supply the `defaultvalue` clause.

     For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).

- **Parameter Arrays.** You must specify `ByVal` for a `ParamArray` parameter.

     You cannot use both `Optional` and `ParamArray` in the same parameter list.

     For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).

- **Passing Mechanism.** The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element. However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.

- **Parameter Names.** If the parameter's data type is an array, follow `parametername` immediately by parentheses. For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Exemple

The following example shows a `Function` procedure that defines two parameters.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
