---
title: 'Comment : activer la pagination des résultats de services de données (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 1c8bb8fe757c35f6096b139da6ca939b1ce1c283
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150620"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Comment : activer la pagination des résultats de services de données (services de données WCF)

WCF Data Services vous permet de limiter le nombre d’entités retournées par une requête de service de données. Les limites de page sont définies dans la méthode appelée lorsque le service est initialisé et peuvent être définies séparément pour chaque jeu d'entités.  
  
 Lorsque la pagination est activée, la dernière entrée dans le flux contient un lien vers la page suivante de données. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).  
  
 Cette rubrique indique comment modifier un service de données pour permettre la pagination de `Customers` retournés et de jeux d'entités `Orders`. L'exemple de cette rubrique utilise l'exemple du service de données Northwind. Ce service est créé lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Comment permettre la pagination de clients retournés et de jeux d'entités de commandes  
  
- Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Voir aussi

- [Chargement de contenu différé](loading-deferred-content-wcf-data-services.md)
- [Procédure : Charger des résultats paginés](how-to-load-paged-results-wcf-data-services.md)
