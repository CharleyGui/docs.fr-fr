---
title: interface - Référence C#
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 19ca4b8a490dc85de0d0e2be6d3ca8fa7982fc14
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713440"
---
# <a name="interface-c-reference"></a>interface (référence C#)

Une interface contient uniquement des signatures de [méthodes](../../programming-guide/classes-and-structs/methods.md), de [propriétés](../../programming-guide/classes-and-structs/properties.md), d’[événements](../../programming-guide/events/index.md) ou d’[indexeurs](../../programming-guide/indexers/index.md). Une classe ou un struct qui implémente l’interface doit implémenter les membres de l’interface qui sont spécifiés dans la définition de l’interface. Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.

Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Exemple

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Une interface peut être membre d’un espace de noms ou d’une classe, et peut contenir les signatures des membres suivants :

- [Méthodes](../../programming-guide/classes-and-structs/methods.md)

- [Propriétés](../../programming-guide/classes-and-structs/using-properties.md)

- [Indexeurs](../../programming-guide/indexers/using-indexers.md)

- [Événements](event.md)

Une interface peut hériter d’une ou de plusieurs interfaces de base.

Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.

Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface. Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.

Pour plus d’informations et plus d’exemples sur l’implémentation explicite des interfaces, consultez [Implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Exemple

L’exemple suivant montre une implémentation d’interface. Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation. Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Types référence](reference-types.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
- [Utilisation de propriétés](../../programming-guide/classes-and-structs/using-properties.md)
- [Utilisation d’indexeurs](../../programming-guide/indexers/using-indexers.md)
- [classe](class.md)
- [struct](struct.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
