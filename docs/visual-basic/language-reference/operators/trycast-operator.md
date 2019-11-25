---
title: TryCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 53306575cfc385039be3939fd87cf993b4509af4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348212"
---
# <a name="trycast-operator-visual-basic"></a>Opérateur TryCast (Visual Basic)
Introduces a type conversion operation that does not throw an exception.  
  
## <a name="remarks"></a>Notes  
 If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error. This can adversely affect the performance of your application. `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.  
  
 You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword. You supply an expression as the first argument and a type to convert it to as the second argument. `TryCast` operates only on reference types, such as classes and interfaces. It requires an inheritance or implementation relationship between the two types. This means that one type must inherit from or implement the other.  
  
## <a name="errors-and-failures"></a>Errors and Failures  
 `TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists. But the lack of a compiler error does not guarantee a successful conversion. If the desired conversion is narrowing, it could fail at run time. If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Mots clés de conversion  
 A comparison of the type conversion keywords is as follows.  
  
|Mot clé|Types de données|Argument relationship|Run-time failure|  
|---|---|---|---|  
|[CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)|Any data types|Widening or narrowing conversion must be defined between the two data types|Throws <xref:System.InvalidCastException>|  
|[DirectCast (opérateur)](../../../visual-basic/language-reference/operators/directcast-operator.md)|Any data types|One type must inherit from or implement the other type|Throws <xref:System.InvalidCastException>|  
|`TryCast`|Reference types only|One type must inherit from or implement the other type|Returns [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
