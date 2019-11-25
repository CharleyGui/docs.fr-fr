---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351477"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Converting with the Narrowing Keyword  
 The conversion procedure must specify `Public Shared` in addition to `Narrowing`.  
  
 Narrowing conversions do not always succeed at run time, and can fail or incur data loss. Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type. This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.  
  
 If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.  
  
 The `Narrowing` keyword can be used in this context:  
  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Guide pratique : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
