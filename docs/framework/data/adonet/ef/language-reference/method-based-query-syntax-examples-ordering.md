---
title: 'Exemples de syntaxe de requête fondée sur une méthode : Classement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: e10101e2a3534d981b2126884a2a61b411254477
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397328"
---
# <a name="method-based-query-syntax-examples-ordering"></a>Exemples de syntaxe de requête fondée sur une méthode : Classement
Les exemples de cette rubrique montrent comment utiliser la méthode <xref:System.Linq.Enumerable.ThenBy%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode. Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Exemple  
 L'exemple ci-dessous de syntaxe de requête fondée sur une méthode utilise <xref:System.Linq.Queryable.OrderBy%2A> et <xref:System.Linq.Queryable.ThenBy%2A> pour retourner une liste de contacts classés par nom, puis par prénom.  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>Exemple  
 L'exemple ci-dessous utilise les méthodes <xref:System.Linq.Queryable.OrderBy%2A> et <xref:System.Linq.Queryable.ThenByDescending%2A> pour effectuer un premier tri par prix courant, puis un tri décroissant des noms de produits.  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
