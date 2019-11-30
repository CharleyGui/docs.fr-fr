---
title: 'Comment : activer la pagination des résultats de services de données (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 6b7cea2475a5c11091a04ef3044bbc958e55fc5d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569091"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="a0178-102">Comment : activer la pagination des résultats de services de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="a0178-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
<span data-ttu-id="a0178-103">WCF Data Services vous permet de limiter le nombre d’entités retournées par une requête de service de données.</span><span class="sxs-lookup"><span data-stu-id="a0178-103">WCF Data Services enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="a0178-104">Les limites de page sont définies dans la méthode appelée lorsque le service est initialisé et peuvent être définies séparément pour chaque jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="a0178-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="a0178-105">Lorsque la pagination est activée, la dernière entrée dans le flux contient un lien vers la page suivante de données.</span><span class="sxs-lookup"><span data-stu-id="a0178-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="a0178-106">Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a0178-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a0178-107">Cette rubrique indique comment modifier un service de données pour permettre la pagination de `Customers` retournés et de jeux d'entités `Orders`.</span><span class="sxs-lookup"><span data-stu-id="a0178-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="a0178-108">L'exemple de cette rubrique utilise l'exemple du service de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="a0178-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="a0178-109">Ce service est créé lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a0178-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="a0178-110">Comment permettre la pagination de clients retournés et de jeux d'entités de commandes</span><span class="sxs-lookup"><span data-stu-id="a0178-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="a0178-111">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a0178-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="a0178-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0178-112">See also</span></span>

- [<span data-ttu-id="a0178-113">Chargement de contenu différé</span><span class="sxs-lookup"><span data-stu-id="a0178-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="a0178-114">Guide pratique pour charger les résultats paginés</span><span class="sxs-lookup"><span data-stu-id="a0178-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
