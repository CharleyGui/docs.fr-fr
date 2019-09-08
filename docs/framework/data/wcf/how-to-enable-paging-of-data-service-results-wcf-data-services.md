---
title: 'Procédure : Activer la pagination des résultats du service de données (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780054"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Procédure : Activer la pagination des résultats du service de données (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de limiter le nombre d'entités retourné par une requête de service des données. Les limites de page sont définies dans la méthode appelée lorsque le service est initialisé et peuvent être définies séparément pour chaque jeu d'entités.  
  
 Lorsque la pagination est activée, la dernière entrée dans le flux contient un lien vers la page suivante de données. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).  
  
 Cette rubrique indique comment modifier un service de données pour permettre la pagination de `Customers` retournés et de jeux d'entités `Orders`. L'exemple de cette rubrique utilise l'exemple du service de données Northwind. Ce service est créé lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Comment permettre la pagination de clients retournés et de jeux d'entités de commandes  
  
- Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Voir aussi

- [Chargement de contenu différé](loading-deferred-content-wcf-data-services.md)
- [Guide pratique pour Charger les résultats paginés](how-to-load-paged-results-wcf-data-services.md)
