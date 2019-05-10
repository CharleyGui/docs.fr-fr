---
title: La copie de la valeur du paramètre 'ByRef' '<parametername>' dans l'argument correspondant passe du type '<typename1>' au type '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: 6d238e9c426b5ae7df0cde745b51eace1cae5d87
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913202"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>Copie de la valeur du paramètre 'ByRef' '\<nom_paramètre >' dans l’argument correspondant passe du type '\<NomType1 >' en type '\<nom_type2 >'
Une procédure est appelée avec un argument qui s’étend au type de paramètre correspondant, et la conversion à partir du paramètre à l’argument est restrictive.  
  
 Quand vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir le type de la classe ou de la structure en d’autres types. Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types vers le type de votre classe ou de votre structure. Lorsque vous utilisez votre type de classe ou structure dans un appel de procédure, Visual Basic peut utiliser ces opérateurs de conversion pour convertir le type d’un argument pour le type de son paramètre correspondant.  
  
 Si vous passez l’argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic copie parfois la valeur d’argument dans une variable locale dans la procédure au lieu de passer une référence. Dans ce cas, lorsque la procédure est retournée, Visual Basic doit copier la valeur de variable locale dans l’argument dans le code appelant.  
  
 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Mais si les types sont différents, Visual Basic doit convertir dans les deux sens. Si un des types est votre type de classe ou structure, Visual Basic doit le convertir à la fois vers et à partir de l’autre type. Si une de ces conversions est étendue, la conversion inverse peut être restrictive.  
  
 **ID d’erreur :** BC32053  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si possible, utilisez un argument d’appel du même type que le paramètre de procédure pour Visual Basic n’a pas besoin d’effectuer de conversion.  
  
- Si vous devez appeler la procédure avec un type d’argument différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre sur [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.  
  
- Si vous avez besoin de retourner une valeur dans l’argument d’appel, définissez l’opérateur de conversion inverse comme [Widening](../../../visual-basic/language-reference/modifiers/widening.md), si possible.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Paramètres et arguments d’une procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Passage d’un argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Guide pratique pour Définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Guide pratique pour Définir un opérateur de Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Conversions de type en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
