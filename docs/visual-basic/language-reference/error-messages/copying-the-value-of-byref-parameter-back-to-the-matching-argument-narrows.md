---
title: La copie de la valeur du paramètre 'ByRef' '<parametername>' dans l'argument correspondant passe du type '<typename1>' au type '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: b9a38d3eb4e25d5c9ac765adf47df72e45fd082a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160930"
---
# <a name="bc32053-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>BC32053 : la copie de la valeur du paramètre’ByRef' ' \<parametername> 'dans l’argument correspondant passe du type' \<typename1> 'au type' \<typename2> '

Une procédure est appelée avec un argument qui s’étend au type de paramètre correspondant, et la conversion du paramètre en argument est restrictive.

 Quand vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir le type de la classe ou de la structure en d’autres types. Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types vers le type de votre classe ou de votre structure. Quand vous utilisez votre type de classe ou de structure dans un appel de procédure, Visual Basic pouvez utiliser ces opérateurs de conversion pour convertir le type d’un argument vers le type de son paramètre correspondant.

 Si vous passez l’argument [ByRef](../modifiers/byref.md), Visual Basic copie parfois la valeur de l’argument dans une variable locale de la procédure au lieu de passer une référence. Dans ce cas, quand la procédure est retournée, Visual Basic doit ensuite copier la valeur de la variable locale dans l’argument du code appelant.

 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Toutefois, si les types sont différents, Visual Basic doit effectuer une conversion dans les deux directions. Si l’un des types est votre type de classe ou de structure, Visual Basic devez le convertir vers et à partir de l’autre type. Si l’une de ces conversions est étendue, la conversion inverse peut être restrictive.

 **ID d’erreur :** BC32053

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, afin Visual Basic n’a pas besoin d’effectuer de conversion.

- Si vous devez appeler la procédure avec un type d’argument différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre sur [ByVal](../modifiers/byval.md) au lieu de `ByRef`.

- Si vous devez retourner une valeur dans l’argument d’appel, définissez l’opérateur de conversion inverse comme [Widening](../modifiers/widening.md), si possible.

## <a name="see-also"></a>Voir aussi

- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Paramètres et arguments d’une procédure](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Passage des arguments par valeur et par référence](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Procédures d'opérateur](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Operator Statement](../statements/operator-statement.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Conversions de type en Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
