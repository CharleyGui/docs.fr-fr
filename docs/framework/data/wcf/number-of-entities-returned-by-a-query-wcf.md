---
title: "Comment : déterminer le nombre d'entités retournées par la requête (services de données WCF)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 0513d7cdb3ab8de8cd8a73528f7e6038a0e4faed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194282"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Comment : déterminer le nombre d'entités retournées par la requête (services de données WCF)

Avec WCF Data Services, vous pouvez déterminer le nombre d’entités qui se trouvent dans le jeu d’entités spécifié par un URI de requête. Ce nombre peut être inclus avec le résultat de la requête ou comme une valeur entière. Pour plus d’informations, consultez [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  

 Cet exemple exécute une requête après avoir appelé la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A>. La propriété <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> retourne le nombre d'entités dans le jeu d'entités `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Exemple  

 Cet exemple appelle la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner uniquement une valeur entière qui correspond au nombre d'entités du jeu d'entités `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)
