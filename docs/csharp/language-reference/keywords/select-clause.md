---
description: select, clause - Référence C#
title: select, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89136900"
---
# <a name="select-clause-c-reference"></a>select, clause (Référence C#)

Dans une expression de requête, la clause `select` spécifie le type de valeurs qui sont générées quand la requête est exécutée. Le résultat est basé sur l’évaluation de toutes les clauses précédentes et sur toutes les expressions de la clause `select` elle-même. Une expression de requête doit se terminer par une clause `select` ou par une clause [group](group-clause.md).

L’exemple suivant présente une clause `select` simple dans une expression de requête.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Le type de la séquence générée par la clause `select` détermine le type de la variable de requête `queryHighScores`. Dans le cas le plus simple, la clause `select` spécifie uniquement la variable de portée. La séquence retournée contient alors des éléments du même type que la source de données. Pour plus d’informations, consultez [relations de types dans les opérations de requête LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Toutefois, la clause `select` fournit également un mécanisme puissant pour transformer (ou *projeter*) les données sources en nouveaux types. Pour plus d’informations, consultez [Transformations de données avec LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Exemple

L’exemple suivant affiche l’ensemble des différentes formes que peut prendre une clause `select`. Dans chaque requête, notez la relation entre la `select` clause et le type de la *variable de requête* ( `studentQuery1` , `studentQuery2` , etc.).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Comme indiqué dans `studentQuery8` dans l’exemple précédent, vous pouvez parfois souhaiter que les éléments de la séquence retournée contiennent uniquement un sous-ensemble des propriétés des éléments sources. En limitant au maximum la séquence retournée, vous pouvez réduire les besoins en ressources mémoire et augmenter la vitesse d’exécution de la requête. Pour ce faire, créez un type anonyme dans la clause `select` et utilisez un initialiseur d’objet pour l’initialiser avec les propriétés appropriées de l’élément source. Pour obtenir un exemple de la procédure à suivre, consultez [Initialiseurs d’objet et de collection](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Notes

Au moment de la compilation, la clause `select` traduite en un appel de méthode à l’opérateur de requête standard <xref:System.Linq.Enumerable.Select%2A>.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Mots clés de requête (LINQ)](query-keywords.md)
- [from, clause](from-clause.md)
- [partial, méthode (Référence C#)](partial-method.md)
- [Types anonymes](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ en C#](../../linq/index.md)
- [LINQ (Language-Integrated Query)](../../programming-guide/concepts/linq/index.md)
