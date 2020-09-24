---
title: Expressions dans les requêtes LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f65759d37661271588d56965eadcccbe997623f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166649"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Expressions dans les requêtes LINQ to Entities

Une expression est un fragment de code qui peut correspondre à une valeur, un objet, une méthode ou un espace de noms. Elle peut contenir une valeur littérale, un appel de méthode, un opérateur et ses opérandes ou un nom simple. Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type. Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme des paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode. Par conséquent, les expressions peuvent être simples ou très complexes.  
  
 Dans LINQ to Entities requêtes, les expressions peuvent contenir tout ce qui est autorisé par les types dans l' <xref:System.Linq.Expressions> espace de noms, y compris les expressions lambda. Les expressions qui peuvent être utilisées dans les requêtes LINQ to Entities sont un sur-ensemble des expressions qui peuvent être utilisées pour interroger le Entity Framework. les expressions qui font partie des requêtes sur les Entity Framework sont limitées aux opérations prises en charge par `ObjectQuery<T>` et la source de données sous-jacente.  
  
 Dans l'exemple suivant, la comparaison dans la clause `Where` est une expression :  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Les constructions de langage spécifiques, telles que C# `unchecked` , n’ont aucune signification dans LINQ to Entities.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Expressions constantes](constant-expressions.md)  
  
 [Expressions de comparaison](comparison-expressions.md)  
  
 [Comparaisons null](null-comparisons.md)  
  
 [Expressions d’initialisation](initialization-expressions.md)  
  
 [Relations, propriétés de navigation et clés étrangères](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../index.md)
