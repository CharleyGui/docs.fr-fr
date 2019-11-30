---
title: 'Comment : exécuter les requêtes dans un lot (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: 0ddf5b4f68ca08fca0c55cfcdfcd5431bcec6de2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569054"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Comment : exécuter les requêtes dans un lot (services de données WCF)
À l’aide de la bibliothèque cliente WCF Data Services, vous pouvez exécuter plusieurs requêtes sur le service de données en un seul lot. Pour plus d’informations, consultez [traitement par lot des opérations](batching-operations-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> pour exécuter un tableau d'objets <xref:System.Data.Services.Client.DataServiceRequest%601> qui contient des requêtes qui retournent des objets `Customers` et `Products` du service de données Northwind. La collection d’objets <xref:System.Data.Services.Client.QueryOperationResponse%601> dans le <xref:System.Data.Services.Client.DataServiceResponse> retourné est énumérée, et la collection d’objets contenue dans chaque <xref:System.Data.Services.Client.QueryOperationResponse%601> est également énumérée.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
