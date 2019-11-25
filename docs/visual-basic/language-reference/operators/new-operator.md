---
title: New, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348315"
---
# <a name="new-operator-visual-basic"></a>New, opérateur (Visual Basic)

Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.

## <a name="remarks"></a>Notes

In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created. This means that the class must expose one or more constructors that the calling code can access.

You can use a `New` clause in a declaration statement or an assignment statement. When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied. The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Since arrays are classes, `New` can create a new array instance, as shown in the following example:

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.

> [!NOTE]
> The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor. For more information about type parameters and constraints, see [Type List](../statements/type-list.md).

To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword. For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

Le mot clé `New` peut être utilisé dans les contextes suivants :

- [Dim (instruction)](../statements/dim-statement.md)
- [Of](../statements/of-clause.md)
- [Sub (instruction)](../statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.OutOfMemoryException>
- [Mots clés](../keywords/index.md)
- [Liste de types](../statements/type-list.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Durée de vie d’un objet : création et destruction des objets](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
