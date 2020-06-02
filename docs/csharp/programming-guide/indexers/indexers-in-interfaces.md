---
title: Indexeurs dans les interfaces - Guide de programmation C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 9ce6e4f0e0533c2880c6241f44409435248a336a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287478"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexeurs dans les interfaces (Guide de programmation C#)

Des indexeurs peuvent être déclarés dans une [interface](../../language-reference/keywords/interface.md). Les accesseurs d’indexeurs d’interface se distinguent sur plusieurs plans des accesseurs d’indexeurs de [classe](../../language-reference/keywords/class.md), à savoir :

- Les accesseurs d’interface n’utilisent pas de modificateurs.
- Un accesseur d’interface n’a généralement pas de corps.

L’objectif de l’accesseur est d’indiquer si l’indexeur est en lecture-écriture, en lecture seule ou en écriture seule. Vous pouvez fournir une implémentation pour un indexeur défini dans une interface, mais cela est rare. Les indexeurs définissent généralement une API pour accéder aux champs de données, et les champs de données ne peuvent pas être définis dans une interface.

L’exemple ci-dessous porte sur un accesseur d’indexeur d’interface :

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

La signature d’un indexeur doit se distinguer de tous les autres indexeurs déclarés dans la même interface.

## <a name="example"></a>Exemple

L’exemple suivant montre comment implémenter des indexeurs d’interface.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

Dans l’exemple précédent, vous pouvez utiliser l’implémentation de membre d’interface explicite en utilisant le nom qualifié complet du membre d’interface. Par exemple :

```csharp
string IIndexInterface.this[int index]
{
}
```

Cependant, le nom qualifié complet est seulement nécessaire pour éviter toute ambiguïté quand la classe implémente plusieurs interfaces avec la même signature d’indexeur. Par exemple, si une classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même signature d’indexeur, l’implémentation de membre d’interface explicite est nécessaire. Autrement dit, la déclaration d’indexeur suivante :

```csharp
string IEmployee.this[int index]
{
}
```

implémente l’indexeur dans l’interface `IEmployee`, alors que la déclaration suivante :

```csharp
string ICitizen.this[int index]
{
}
```

implémente l’interface dans l’interface `ICitizen`.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Indexeurs](./index.md)
- [Propriétés](../classes-and-structs/properties.md)
- [Interfaces](../interfaces/index.md)
