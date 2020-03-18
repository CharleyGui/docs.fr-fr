---
title: join, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713402"
---
# <a name="join-clause-c-reference"></a>join, clause (référence C#)

La clause `join` est utile pour associer des éléments de différentes séquences sources qui n’ont pas de relation directe dans le modèle objet. Le seul impératif est que les éléments de chaque source partagent une valeur dont l’égalité peut être comparée. Par exemple, un distributeur de produits alimentaires peut avoir une liste de fournisseurs d’un certain produit et une liste d’acheteurs. Une clause `join` peut être utilisée par exemple pour créer une liste des fournisseurs et des acheteurs de ce produit qui se trouvent tous dans la même région spécifiée.

Une clause `join` prend deux séquences sources comme entrée. Les éléments de chaque séquence doivent être ou contenir une propriété qui peut être comparée à une propriété correspondante dans l’autre séquence. La clause `join` utilise le mot clé spécial `equals` pour comparer les clés spécifiées et déterminer si elles sont égales. Toutes les jointures effectuées par la clause `join` sont des équijointures. La forme de la sortie d’une clause `join` dépend du type spécifique de jointure que vous effectuez. Les trois types de jointure les plus courants sont les suivants :

- Jointure interne

- Jointure groupée

- Jointure externe gauche

## <a name="inner-join"></a>Jointure interne

L’exemple suivant montre une équijointure interne simple. Cette requête produit une séquence plate de paires « nom de produit / catégorie ». La même chaîne de catégorie apparaît dans plusieurs éléments. Si un élément de `categories` n’a pas de `products` correspondant, cette catégorie n’apparaît pas dans les résultats.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Pour plus d’informations, consultez [Effectuer des jointures internes](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Jointure groupée

Une clause `join` avec une expression `into` est appelée une jointure groupée.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Une jointure groupée produit une séquence de résultats hiérarchique, qui associe des éléments de la séquence source de gauche à un ou plusieurs éléments correspondants de la séquence source de droite. Une jointure groupée n’a pas d’équivalent en termes relationnels ; il s’agit en fait d’une séquence de tableaux d’objets.

Si aucun élément de la séquence source de droite n’est trouvé en correspondance avec un élément de la source de gauche, la clause `join` produit un tableau vide pour cet élément. Par conséquent, la jointure groupée est fondamentalement une équijointure interne, excepté que la séquence de résultats est organisée en groupes.

Si vous sélectionnez les résultats d’une jointure groupée, vous pouvez accéder aux éléments, mais vous ne pouvez pas identifier leur clé de correspondance. Par conséquent, il est généralement plus utile de sélectionner les résultats de la jointure groupée dans un nouveau type qui a aussi le nom de clé, comme illustré dans l’exemple précédent.

Bien sûr, vous pouvez aussi utiliser le résultat d’une jointure groupée comme générateur d’une autre sous-requête :

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Pour plus d’informations, consultez [Effectuer des jointures groupées](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Jointure externe gauche

Dans une jointure externe gauche, tous les éléments de la séquence source de gauche sont retournés, même si aucun élément correspondant ne se trouve dans la séquence de droite. Pour effectuer une jointure extérieure gauche `DefaultIfEmpty` dans LINQ, utilisez la méthode en combinaison avec une jointure de groupe pour spécifier un élément latéral droit par défaut à produire si un élément du côté gauche n’a pas de correspondances. Vous pouvez utiliser `null` comme valeur par défaut pour tous les types référence ou vous pouvez spécifier un type par défaut défini par l’utilisateur. L’exemple suivant montre un type par défaut défini par l’utilisateur :

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Pour plus d’informations, consultez [Effectuer des jointures externes gauches](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Opérateur Égal

Une clause `join` effectue une équijointure. En d’autres termes, vous pouvez baser les correspondances seulement sur l’égalité de deux clés. Les autres types de comparaisons, comme « supérieur à » ou « différent de », ne sont pas pris en charge. Pour indiquer clairement que toutes les jointures sont des équijointures, la clause `join` utilise le mot clé `equals` au lieu de l’opérateur `==`. Le mot clé `equals` peut être utilisé seulement dans une clause `join` et diffère de l’opérateur `==` sur un point important. Avec `equals`, la clé gauche consomme la séquence source externe et la clé droite consomme la source interne. La source externe est seulement dans l’étendue du côté gauche de `equals` et la séquence source interne est seulement dans l’étendue du côté droit.

## <a name="non-equijoins"></a>Non-équijointures

Vous pouvez effectuer des non-équijointures, des jointures croisées et d’autres opérations de jointure personnalisées en utilisant plusieurs clauses `from` pour introduire indépendamment de nouvelles séquences dans une requête. Pour plus d’informations, consultez [Effectuer des opérations de jointure personnalisées](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Jointures sur des collections d’objets et sur des tables relationnelles

Dans une expression de requête LINQ, les opérations de jointure sont effectuées sur les collections d’objets. Les collections d’objets ne peuvent pas être « jointes » exactement de la même façon que deux tables relationnelles. Dans LINQ, `join` les clauses explicites ne sont requises que lorsque deux séquences sources ne sont liées par aucune relation. Quand vous travaillez avec [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], les tables avec des clés étrangères sont représentées dans le modèle objet en tant que propriétés de la table principale. Par exemple, dans la base de données Northwind, la table Customer a une relation de clé étrangère avec la table Orders. Quand vous mappez les tables au modèle objet, la classe Customer a une propriété Orders qui contient la collection de commandes associées à ce client. En réalité, la jointure a déjà été effectuée pour vous.

Pour plus d’informations sur l’interrogation de tables liées dans le contexte de [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], consultez [Procédure : mapper des relations de base de données](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Clés composites

Vous pouvez tester l’égalité de plusieurs valeurs en utilisant une clé composite. Pour plus d’informations, consultez [Effectuer des opérations de jointure à l’aide de clés composites](../../linq/join-by-using-composite-keys.md). Vous pouvez aussi utiliser des clés composites dans une clause `group`.

## <a name="example"></a> Exemple

L’exemple suivant compare les résultats d’une jointure interne, d’une jointure groupée et d’une jointure externe gauche sur les mêmes sources de données en utilisant les mêmes clés de correspondance. Du code supplémentaire est ajouté à ces exemples pour clarifier les résultats dans l’affichage de la console.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Notes 

Une clause `join` qui n’est pas suivie de `into` se traduit par l’appel de la méthode <xref:System.Linq.Enumerable.Join%2A>. Une clause `join` qui n’est pas suivie de `into` se traduit par l’appel de la méthode <xref:System.Linq.Enumerable.GroupJoin%2A>.

## <a name="see-also"></a>Voir aussi

- [Mots-clés de requête (LINQ)](query-keywords.md)
- [Requête intégrée linguistique (LINQ)](../../linq/index.md)
- [Rejoindre les opérations](../../programming-guide/concepts/linq/join-operations.md)
- [group, clause](group-clause.md)
- [Effectuer des jointures externes gauches](../../linq/perform-left-outer-joins.md)
- [Effectuer des jointures intérieures](../../linq/perform-inner-joins.md)
- [Effectuer des jointures groupées](../../linq/perform-grouped-joins.md)
- [Classer les résultats d’une clause join](../../linq/order-the-results-of-a-join-clause.md)
- [Effectuer des jointures à l’aide de clés composites](../../linq/join-by-using-composite-keys.md)
- [Systèmes de base de données compatibles pour Visual Studio](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
