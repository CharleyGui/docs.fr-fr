---
title: where, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173482"
---
# <a name="where-clause-c-reference"></a>where, clause (Référence C#)

La clause `where` est utilisée dans une expression de requête pour spécifier les éléments de la source de données qui seront retournés dans l’expression de requête. Elle applique une condition booléenne (un *prédicat*) à chaque élément source (référencé par la variable de portée) et retourne ceux pour lesquels la condition spécifiée est remplie. Une expression de requête unique peut contenir plusieurs clauses `where` et une clause unique peut contenir plusieurs sous-expressions de prédicat.

## <a name="example"></a> Exemple

Dans l’exemple suivant, la clause `where` élimine par filtrage tous les nombres excepté ceux inférieurs à cinq. Si vous supprimez la clause `where`, tous les nombres de la source de données seront retournés. L’expression `num < 5` est le prédicat qui est appliqué à chaque élément.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a> Exemple

Dans une `where` seule clause, vous pouvez spécifier [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) autant de prédicats que nécessaire en utilisant les opérateurs et [&#124;&#124;.](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) Dans l’exemple suivant, la requête spécifie deux prédicats pour sélectionner uniquement les nombres pairs inférieurs à cinq.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a> Exemple

Une clause `where` peut contenir une ou plusieurs méthodes qui retournent des valeurs booléennes. Dans l’exemple suivant, la clause `where` utilise une méthode pour déterminer si la valeur actuelle de la variable de portée est paire ou impaire.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Notes 

La clause `where` est un mécanisme de filtrage. Elle peut être placée à presque n’importe quel endroit d’une expression de requête, sauf qu’elle ne peut pas être la première ni la dernière clause. Une clause `where` peut apparaître avant ou après une clause [group](group-clause.md) selon que vous devez filtrer les éléments sources avant ou après leur regroupement.

Si un prédicat spécifié n’est pas valide pour les éléments de la source de données, une erreur de compilation est générée. Il s’agit d’un des avantages de la forte vérification de type fournie par LINQ.

Au moment de la compilation, le mot clé `where` est converti en appel à la méthode d’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A>.

## <a name="see-also"></a>Voir aussi

- [Mots-clés de requête (LINQ)](query-keywords.md)
- [de la clause](from-clause.md)
- [clause de sélection](select-clause.md)
- [Filtrage des données](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ en C#](../../linq/index.md)
- [Requête intégrée linguistique (LINQ)](../../programming-guide/concepts/linq/index.md)
