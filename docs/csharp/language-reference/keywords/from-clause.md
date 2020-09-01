---
description: from, clause - Référence C#
title: from, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 474b22f5a9d8f12c8a4365159817f878761b563c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140787"
---
# <a name="from-clause-c-reference"></a>from, clause (Référence C#)

Une expression de requête doit commencer par une clause `from`. Une expression de requête peut également contenir des sous-requêtes qui commencent elles aussi par une clause `from`. La clause `from` spécifie les éléments suivants :

- La source de données sur laquelle la requête ou la sous-requête est exécutée.

- Une *variable de portée locale* qui représente chaque élément dans la séquence source.

La variable de portée et la source de données sont toutes les deux fortement typées. La source de données référencée dans la clause `from` doit avoir un type <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> ou un type dérivé comme <xref:System.Linq.IQueryable%601>.

Dans l’exemple suivant, `numbers` est la source de données tandis que `num` est la variable de portée. Notez que les deux variables sont fortement typées même si le mot clé [var](var.md) est utilisé.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Variable de portée

Le compilateur déduit le type de la variable de portée quand la source de données implémente <xref:System.Collections.Generic.IEnumerable%601>. Par exemple, si la source a un type `IEnumerable<Customer>`, la variable de portée est déduite comme étant `Customer`. Vous devez spécifier le type de façon explicite uniquement quand la source est un type `IEnumerable` non générique comme <xref:System.Collections.ArrayList>. Pour plus d’informations, consultez [Comment interroger une ArrayList avec LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

Dans l’exemple précédent, `num` est déduit comme étant de type `int`. Comme la variable de portée est fortement typée, vous pouvez appeler des méthodes sur celle-ci ou l’utiliser dans d’autres opérations. Par exemple, au lieu d’écrire `select num`, vous pouvez écrire `select num.ToString()` pour que l’expression de requête retourne une séquence de chaînes à la place d’entiers. Vous pouvez également écrire `select num + 10` pour que l’expression retourne la séquence 14, 11, 13, 12, 10. Pour plus d’informations, consultez [Select, clause](select-clause.md).

La variable de portée est semblable à une variable d’itération dans une instruction [foreach](foreach-in.md) à une différence près, très importante : une variable de portée ne stocke jamais réellement de données de la source. Il s’agit juste d’une syntaxe pratique qui permet à la requête de décrire ce qui se produira lors de son exécution. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Clauses from composées

Dans certains cas, chaque élément dans la séquence source peut être une séquence ou contenir une séquence. Par exemple, votre source de données peut être un `IEnumerable<Student>` où chaque objet Student dans la séquence contient une liste de notes d’examens. Pour accéder à la liste interne dans chaque élément `Student`, vous pouvez utiliser des clauses `from` composées. Cette technique est proche de celle consistant à utiliser des instructions [foreach](foreach-in.md) imbriquées. Vous pouvez ajouter des clauses [where](partial-method.md) ou [orderby](orderby-clause.md) à l’une et l’autre des clauses `from` pour filtrer les résultats. L’exemple suivant présente une séquence d’objets `Student` et chacun contient un `List` interne des entiers qui représentent des notes d’examens. Pour accéder à la liste interne, utilisez une clause `from` composée. Vous pouvez insérer des clauses entre les deux clauses `from` si nécessaire.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Utilisation de plusieurs clauses from pour effectuer des jointures

Une clause `from` composée est utilisée pour accéder aux collections internes dans une source de données unique. Toutefois, une requête peut également contenir plusieurs clauses `from` qui génèrent des requêtes supplémentaires de sources de données indépendantes. Cette technique vous permet d’effectuer certains types d’opérations de jointure qui ne sont pas possibles en utilisant la [clause join](join-clause.md).

L’exemple suivant montre comment utiliser deux clauses `from` pour former une jointure croisée complète de deux sources de données.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Pour plus d’informations sur les opérations de jointure qui utilisent plusieurs clauses `from`, consultez [Effectuer des jointures externes gauches](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Voir aussi

- [Mots clés de requête (LINQ)](query-keywords.md)
- [LINQ (Language-Integrated Query)](../../linq/index.md)
