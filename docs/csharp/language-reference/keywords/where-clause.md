---
title: where, clause - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: aceda6cfd33a53388a5afb046359c4dcfddfd1f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602024"
---
# <a name="where-clause-c-reference"></a>where, clause (Référence C#)

La clause `where` est utilisée dans une expression de requête pour spécifier les éléments de la source de données qui seront retournés dans l’expression de requête. Elle applique une condition booléenne (un *prédicat*) à chaque élément source (référencé par la variable de portée) et retourne ceux pour lesquels la condition spécifiée est remplie. Une expression de requête unique peut contenir plusieurs clauses `where` et une clause unique peut contenir plusieurs sous-expressions de prédicat.

## <a name="example"></a>Exemples

Dans l’exemple suivant, la clause `where` élimine par filtrage tous les nombres excepté ceux inférieurs à cinq. Si vous supprimez la clause `where`, tous les nombres de la source de données seront retournés. L’expression `num < 5` est le prédicat qui est appliqué à chaque élément.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Exemples

Dans une clause `where` unique, vous pouvez spécifier autant de prédicats que nécessaire à l’aide des opérateurs [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) et [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-). Dans l’exemple suivant, la requête spécifie deux prédicats pour sélectionner uniquement les nombres pairs inférieurs à cinq.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Exemples

Une clause `where` peut contenir une ou plusieurs méthodes qui retournent des valeurs booléennes. Dans l’exemple suivant, la clause `where` utilise une méthode pour déterminer si la valeur actuelle de la variable de portée est paire ou impaire.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Remarques

La clause `where` est un mécanisme de filtrage. Elle peut être placée à presque n’importe quel endroit d’une expression de requête, sauf qu’elle ne peut pas être la première ni la dernière clause. Une clause `where` peut apparaître avant ou après une clause [group](group-clause.md) selon que vous devez filtrer les éléments sources avant ou après leur regroupement.

Si un prédicat spécifié n’est pas valide pour les éléments de la source de données, une erreur de compilation est générée. C’est l’un des avantages de la vérification de type fort fourni par [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].

Au moment de la compilation, le mot clé `where` est converti en appel à la méthode d’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A>.

## <a name="see-also"></a>Voir aussi

- [Mots clés de requête (LINQ)](query-keywords.md)
- [from, clause](from-clause.md)
- [select, clause](select-clause.md)
- [Filtrage des données](../../programming-guide/concepts/linq/filtering-data.md)
- [Expressions de requête LINQ](../../programming-guide/linq-query-expressions/index.md)
- [Bien démarrer avec LINQ en C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
