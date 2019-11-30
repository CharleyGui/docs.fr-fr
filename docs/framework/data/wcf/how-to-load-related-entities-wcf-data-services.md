---
title: 'Comment : charger les entités connexes (Services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 84c2448f317e813a95688feaaac1c97436de1b16
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569017"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Comment : charger les entités connexes (Services de données WCF)
Lorsque vous devez charger des entités associées dans WCF Data Services, vous pouvez utiliser la méthode <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> sur la classe <xref:System.Data.Services.Client.DataServiceContext>. Vous pouvez également utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> sur le <xref:System.Data.Services.Client.DataServiceQuery%601> pour exiger que les entités associées soient chargées de façon dynamique dans la même réponse de requête.  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment charger explicitement le `Customer` associé à chaque instance `Orders` retournée.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous montre comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> pour retourner `Order Details` qui appartient au `Orders` retourné par la requête.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)
