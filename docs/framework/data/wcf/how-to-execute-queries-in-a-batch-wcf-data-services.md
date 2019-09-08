---
title: 'Procédure : Exécuter des requêtes dans un lot (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a825fe83ff62d935740fb69871ba2d1e2120e9ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790495"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Procédure : Exécuter des requêtes dans un lot (WCF Data Services)
À l’aide [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] de la bibliothèque cliente, vous pouvez exécuter plusieurs requêtes sur le service de données dans un lot unique. Pour plus d’informations, consultez [traitement par lot des opérations](batching-operations-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> pour exécuter un tableau d'objets <xref:System.Data.Services.Client.DataServiceRequest%601> qui contient des requêtes qui retournent des objets `Customers` et `Products` du service de données Northwind. La collection d’objets <xref:System.Data.Services.Client.QueryOperationResponse%601> dans le <xref:System.Data.Services.Client.DataServiceResponse> retourné est énumérée, et la collection d’objets contenue dans chaque <xref:System.Data.Services.Client.QueryOperationResponse%601> est également énumérée.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
