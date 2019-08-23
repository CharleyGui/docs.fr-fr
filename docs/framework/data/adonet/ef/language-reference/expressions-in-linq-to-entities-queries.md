---
title: Expressions dans les requêtes LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 383339241194c56d0c3178f538f2ac08b2f1b437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950395"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Expressions dans les requêtes LINQ to Entities
Une expression est un fragment de code qui peut correspondre à une valeur, un objet, une méthode ou un espace de noms. Elle peut contenir une valeur littérale, un appel de méthode, un opérateur et ses opérandes ou un nom simple. Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type. Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme des paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode. Par conséquent, les expressions peuvent être simples ou très complexes.  
  
 Dans LINQ to Entities requêtes, les expressions peuvent contenir tout ce qui est autorisé par <xref:System.Linq.Expressions> les types dans l’espace de noms, y compris les expressions lambda. Les expressions qui peuvent être utilisées dans les requêtes LINQ to Entities sont un sur-ensemble des expressions qui peuvent être utilisées pour [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]interroger le.  Les expressions qui font partie des requêtes sur [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] le sont limitées aux opérations prises `ObjectQuery<T>` en charge par et la source de données sous-jacente.  
  
 Dans l'exemple suivant, la comparaison dans la clause `Where` est une expression :  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Les constructions de langage spécifiques, telles C# `unchecked`que, n’ont aucune signification dans LINQ to Entities.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Expressions de constantes](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Expressions de comparaison](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Comparaisons Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Expressions d’initialisation](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Relations, propriétés de navigation et clés étrangères](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
