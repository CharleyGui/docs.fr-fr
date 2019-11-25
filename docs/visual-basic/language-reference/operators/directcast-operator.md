---
title: DirectCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 8ea29b80cf27bbb2c21a8cebbfaa0a294e05f11d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331305"
---
# <a name="directcast-operator-visual-basic"></a>Opérateur DirectCast (Visual Basic)
Introduces a type conversion operation based on inheritance or implementation.  
  
## <a name="remarks"></a>Notes  
 `DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.  
  
 You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword. You supply an expression as the first argument and a type to convert it to as the second argument. `DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments. This means that one type must inherit from or implement the other.  
  
## <a name="errors-and-failures"></a>Errors and Failures  
 `DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists. But the lack of a compiler error does not guarantee a successful conversion. If the desired conversion is narrowing, it could fail at run time. If this happens, the runtime throws an <xref:System.InvalidCastException> error.  
  
## <a name="conversion-keywords"></a>Mots clés de conversion  
 A comparison of the type conversion keywords is as follows.  
  
|Mot clé|Types de données|Argument relationship|Run-time failure|  
|---|---|---|---|  
|[CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)|Any data types|Widening or narrowing conversion must be defined between the two data types|Throws <xref:System.InvalidCastException>|  
|`DirectCast`|Any data types|One type must inherit from or implement the other type|Throws <xref:System.InvalidCastException>|  
|[TryCast (opérateur)](../../../visual-basic/language-reference/operators/trycast-operator.md)|Reference types only|One type must inherit from or implement the other type|Returns [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemple  
 The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 In the preceding example, the run-time type of `q` is `Double`. `CType` succeeds because `Double` can be converted to `Integer`. However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists. The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
