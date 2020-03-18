---
title: group, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713471"
---
# <a name="group-clause-c-reference"></a>group, clause (Référence C#)

La clause `group` retourne une séquence d’objets <xref:System.Linq.IGrouping%602> qui contient zéro, un ou plusieurs éléments qui correspondent à la valeur de clé du groupe. Par exemple, vous pouvez regrouper une séquence de chaînes en fonction de la première lettre de chaque chaîne. Dans ce cas, la première lettre est la clé, elle a le type [char](../builtin-types/char.md) et elle est stockée dans la propriété `Key` de chaque objet <xref:System.Linq.IGrouping%602>. Le compilateur déduit le type de la clé.

Vous pouvez terminer une expression de requête avec une clause `group`, comme illustré dans l’exemple suivant :

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Si vous souhaitez effectuer des opérations de requête supplémentaires sur chaque groupe, vous pouvez spécifier un identificateur temporaire en utilisant le mot clé contextuel [into](into.md). Quand vous utilisez `into`, vous devez continuer la requête et finalement la terminer avec une instruction `select` ou une autre clause `group`, comme illustré dans l’extrait suivant :

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Des exemples d’utilisation plus complets de `group` avec et sans `into` sont fournis dans la section Exemple de cet article.

## <a name="enumerating-the-results-of-a-group-query"></a>Énumération des résultats d’une requête de groupe

Étant donné que les objets <xref:System.Linq.IGrouping%602> générés par une requête `group` sont essentiellement une liste de listes, vous devez utiliser une boucle [foreach](foreach-in.md) imbriquée pour accéder aux éléments dans chaque groupe. La boucle externe itère les clés de groupe, et la boucle interne itère chaque élément dans le groupe proprement dit. Un groupe peut avoir une clé mais pas d’éléments. Voici la boucle `foreach` qui exécute la requête dans les exemples de code précédents :

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Types de clés

Les clés de groupes peuvent être de tout type, comme une chaîne, un type numérique intégré, ou un type nommé ou un type anonyme défini par l’utilisateur.

### <a name="grouping-by-string"></a>Regroupement par chaîne

Les exemples de code précédents utilisaient un `char`. On aurait facilement pu spécifier une clé de chaîne à la place, par exemple le nom de famille complet :

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Regroupement par valeur booléenne

L’exemple suivant illustre l’utilisation d’une valeur booléenne pour une clé afin de répartir les résultats en deux groupes. Notez que la valeur est générée par une sous-expression dans la clause `group`.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Regroupement par plage numérique

L’exemple suivant utilise une expression pour créer des clés de groupes numériques qui représentent une plage de centiles. Notez l’utilisation de [let](let-clause.md) comme emplacement pratique pour stocker un résultat d’appel de méthode, qui vous évite d’avoir à appeler deux fois la méthode dans la clause `group`. Pour plus d’informations sur la façon d’utiliser en toute sécurité les méthodes dans les expressions de requête, voir [les exceptions De poignée dans les expressions de requête](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Regroupement par clés composites

Utilisez une clé composite quand vous souhaitez regrouper des éléments en fonction de plusieurs clés. Vous créez une clé composite en utilisant un type anonyme ou un type nommé pour contenir l’élément clé. Dans l’exemple suivant, supposons qu’une classe `Person` a été déclarée avec les membres nommés `surname` et `city`. La clause `group` provoque la création d’un groupe distinct pour chaque ensemble de personnes ayant le même nom de famille et la même ville.

```csharp
group person by new {name = person.surname, city = person.city};
```

Utilisez un type nommé si vous devez passer la variable de requête à une autre méthode. Créez une classe spéciale à l’aide de propriétés implémentées automatiquement pour les clés, puis substituez les méthodes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A>. Vous pouvez également utiliser un struct, auquel cas vous n’êtes pas obligé de substituer ces méthodes. Pour plus d’informations voir [Comment mettre en œuvre une classe légère avec des propriétés auto-mises en œuvre](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) et [Comment interroger les fichiers en double dans un arbre d’annuaire](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Ce dernier article contient un exemple de code qui montre comment utiliser une clé composite avec un type nommé.

## <a name="example"></a> Exemple

L’exemple suivant montre le modèle standard pour organiser des données sources en groupes quand aucune logique de requête supplémentaire n’est appliquée aux groupes. Il s’agit alors d’un regroupement sans continuation. Les éléments du tableau de chaînes sont regroupés en fonction de leur première lettre. Le résultat de la requête est un type <xref:System.Linq.IGrouping%602> contenant une propriété `Key` publique de type `char` et une collection <xref:System.Collections.Generic.IEnumerable%601> qui contient chaque élément du regroupement.

Le résultat d’une clause `group` est une séquence de séquences. Ainsi, pour accéder aux différents éléments de chaque groupe retourné, vous devez utiliser une boucle `foreach` imbriquée à l’intérieur de la boucle qui itère les clés de groupe, comme illustré dans l’exemple suivant.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a> Exemple

Cet exemple montre comment exécuter une logique supplémentaire sur les groupes après les avoir créés, à l’aide une *continuation* avec `into`. Pour plus d’informations, consultez [into](into.md). L’exemple suivant interroge chaque groupe pour sélectionner uniquement ceux dont la valeur de clé est une voyelle.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Notes 

Lors de la compilation, les clauses `group` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.GroupBy%2A>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [Mots clés de requête](query-keywords.md)
- [Requête intégrée linguistique (LINQ)](../../linq/index.md)
- [Créer un groupe imbriqué](../../linq/create-a-nested-group.md)
- [Regrouper les résultats d’une requête](../../linq/group-query-results.md)
- [Effectuer une sous-requête sur une opération de regroupement](../../linq/perform-a-subquery-on-a-grouping-operation.md)
