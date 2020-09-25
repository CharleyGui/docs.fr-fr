---
title: "Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 96d393a34af69935e75582ef1954ddd661a355f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192046"
---
# <a name="method-based-query-syntax-examples-element-operators"></a>Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément

Les exemples de cette rubrique montrent comment utiliser la <xref:System.Linq.Enumerable.First%2A> méthode pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode. Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 L’exemple de cette rubrique utilise les `using` / `Imports` instructions suivantes :  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a>Premier  
  
### <a name="example"></a>Exemple  

 L’exemple suivant utilise la <xref:System.Linq.Enumerable.First%2A> méthode pour rechercher la première adresse de messagerie qui commence par’Caroline'.  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
