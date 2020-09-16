---
title: Effectuer des jointures groupées (LINQ en C#)
description: Découvrez comment effectuer des jointures groupées à l’aide de LINQ en C#.
ms.date: 04/22/2020
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 6411479c5fe6cb0ee79a0cd3df6de2f4d42c26a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542807"
---
# <a name="perform-grouped-joins"></a>Effectuer des jointures groupées

La jointure groupée est utile pour produire des structures de données hiérarchiques. Elle associe chaque élément de la première collection à un jeu d’éléments corrélés de la deuxième collection.

Par exemple, une classe ou une table de base de données relationnelle nommée `Student` peut contenir deux champs : `Id` et `Name`. Une deuxième classe ou table de base de données relationnelle nommée `Course` peut contenir deux champs : `StudentId` et `CourseTitle`. Une jointure groupée de ces deux sources de données, basée sur les champs `Student.Id` et `Course.StudentId` correspondants, regroupe chaque `Student` avec une collection d’objets `Course` (qui peut être vide).

> [!NOTE]
> Chaque élément de la première collection apparaît dans le jeu de résultats d’une jointure groupée, même si des éléments corrélés sont trouvés dans la deuxième collection. Si aucun élément corrélé n’est trouvé, la séquence d’éléments corrélés pour cet élément est vide. Le sélecteur de résultats a donc accès à chaque élément de la première collection. Cela n’est pas le cas du sélecteur de résultats dans une jointure non groupée, qui ne peut pas accéder à des éléments de la première collection qui n’ont aucune correspondance dans la deuxième collection.

> [!WARNING]
> <xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType> n’a aucun équivalent direct dans les termes de base de données relationnelle traditionnels. Toutefois, cette méthode implémente un sur-ensemble de jointures internes et de jointures externes gauches. Ces deux opérations peuvent être écrites en termes de jointure groupée. Pour plus d’informations, consultez [join, opérations](../programming-guide/concepts/linq/join-operations.md) et [Entity Framework Core, GroupJoin](/ef/core/querying/complex-query-operators#groupjoin).

Le premier exemple de cet article montre comment effectuer une jointure groupée. Le deuxième exemple montre comment utiliser une jointure groupée pour créer des éléments XML.

## <a name="example---group-join"></a>Exemple – Jointure groupée

L’exemple suivant effectue une jointure groupée d’objets de types `Person` et `Pet` où `Person` correspond à la propriété `Pet.Owner`. Contrairement à une jointure non groupée qui produirait une paire d’éléments pour chaque correspondance, la jointure groupée produit un seul objet résultant pour chaque élément de la première collection, qui est un objet `Person` dans cet exemple. Les éléments correspondants de la deuxième collection, qui sont des objets `Pet` dans cet exemple, sont regroupés dans une collection. Enfin, le sélecteur de résultats crée un type anonyme pour chaque correspondance qui se compose de `Person.FirstName` et d’une collection d’objets `Pet`.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Exemple – Jointure groupée pour créer des éléments XLM

Les jointures groupées sont appropriées pour créer des éléments XML à l’aide de LINQ to XML. L’exemple suivant est similaire à l’exemple précédent, sauf qu’au lieu de créer des types anonymes, le sélecteur de résultats crée des éléments XML qui représentent les objets joints.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Effectuer des jointures internes](perform-inner-joins.md)
- [Effectuer des jointures externes gauches](perform-left-outer-joins.md)
- [Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md)
