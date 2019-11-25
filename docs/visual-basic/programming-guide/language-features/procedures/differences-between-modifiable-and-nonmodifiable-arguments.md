---
title: Différences entre les arguments modifiables et non modifiables
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 989795ee2cdd3a78b71bad4d95cf9b384c2719bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341389"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Différences entre les arguments modifiables et non modifiables (Visual Basic)
When you call a procedure, you typically pass one or more arguments to it. Each argument corresponds to an underlying programming element. Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Modifiable and Nonmodifiable Elements  
 A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.  
  
 The following table lists modifiable and nonmodifiable programming elements.  
  
|Modifiable elements|Nonmodifiable elements|  
|-------------------------|----------------------------|  
|Local variables (declared inside procedures), including object variables, except for read-only|Read-only variables, fields, and properties|  
|Fields (member variables of modules, classes, and structures), except for read-only|Constants and literals|  
|Properties, except for read-only|Enumeration members|  
|Array elements|Expressions (even if their elements are modifiable)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Modifiable and Nonmodifiable Arguments  
 A *modifiable argument* is one with a modifiable underlying element. The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.  
  
 A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element. If it is a nonmodifiable element, the calling code itself cannot modify it.  
  
 The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Guide pratique : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Guide pratique : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Guide pratique : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
