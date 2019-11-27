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

Introduit une clause `New` pour créer une nouvelle instance d’objet, spécifie une contrainte de constructeur sur un paramètre de type, ou identifie une procédure `Sub` comme un constructeur de classe.

## <a name="remarks"></a>Notes

Dans une déclaration ou une instruction d’assignation, une clause `New` doit spécifier une classe définie à partir de laquelle l’instance peut être créée. Cela signifie que la classe doit exposer un ou plusieurs constructeurs auxquels le code appelant peut accéder.

Vous pouvez utiliser une clause `New` dans une instruction de déclaration ou une instruction d’assignation. Lorsque l’instruction s’exécute, elle appelle le constructeur approprié de la classe spécifiée, en passant tous les arguments que vous avez fournis. L’exemple suivant illustre cela en créant des instances d’une classe `Customer` qui a deux constructeurs, un qui n’accepte aucun paramètre et un qui accepte un paramètre de chaîne :

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Étant donné que les tableaux sont des classes, `New` pouvez créer une nouvelle instance de tableau, comme indiqué dans l’exemple suivant :

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

Le common language runtime (CLR) lève une erreur de <xref:System.OutOfMemoryException> si la mémoire est insuffisante pour créer la nouvelle instance.

> [!NOTE]
> Le mot clé `New` est également utilisé dans les listes de paramètres de type pour spécifier que le type fourni doit exposer un constructeur sans paramètre accessible. Pour plus d’informations sur les paramètres de type et les contraintes, consultez [type list](../statements/type-list.md).

Pour créer une procédure constructeur pour une classe, définissez le nom d’une `Sub` procédure sur le mot clé `New`. Pour plus d’informations, consultez durée de vie d’un [objet : comment les objets sont créés et détruits](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

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
