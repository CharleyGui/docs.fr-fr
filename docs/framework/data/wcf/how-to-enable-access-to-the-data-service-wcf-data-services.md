---
title: "Procédure : activer l'accès au service de données (WCF Data Services)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 62622a5788a735497a6869c114c572e947067449
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155417"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="15310-102">Procédure : activer l'accès au service de données (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="15310-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>

<span data-ttu-id="15310-103">Dans WCF Data Services, vous devez accorder explicitement l’accès aux ressources exposées par un service de données.</span><span class="sxs-lookup"><span data-stu-id="15310-103">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="15310-104">Cela signifie qu'après avoir créé un service de données, vous devez encore fournir explicitement l'accès à des ressources individuelles comme les jeux d'entités.</span><span class="sxs-lookup"><span data-stu-id="15310-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="15310-105">Cette rubrique montre comment activer l’accès en lecture et en écriture à cinq des jeux d’entités dans le service de données Northwind créé lorsque vous effectuez le [démarrage rapide](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="15310-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="15310-106">Puisque l'énumération <xref:System.Data.Services.EntitySetRights> est définie à l'aide de l'objet <xref:System.FlagsAttribute>, vous pouvez utiliser un opérateur OR logique pour spécifier plusieurs autorisations pour un jeu d'entités unique.</span><span class="sxs-lookup"><span data-stu-id="15310-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15310-107">Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données.</span><span class="sxs-lookup"><span data-stu-id="15310-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="15310-108">Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même.</span><span class="sxs-lookup"><span data-stu-id="15310-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="15310-109">Pour plus d’informations, consultez [sécurisation des sites Web ASP.net](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="15310-109">For more information, see [Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="15310-110">Pour activer l'accès au service de données</span><span class="sxs-lookup"><span data-stu-id="15310-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="15310-111">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="15310-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="15310-112">Cela permet aux clients de disposer d'un accès en lecture et en écriture aux jeux d'entités `Orders` et `Order_Details` et d'un accès en lecture seule aux jeux d'entités `Customers`.</span><span class="sxs-lookup"><span data-stu-id="15310-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15310-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15310-113">See also</span></span>

- [<span data-ttu-id="15310-114">Procédure : Développer un WCF Data Service qui fonctionne sur IIS</span><span class="sxs-lookup"><span data-stu-id="15310-114">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="15310-115">Configuration du service de données</span><span class="sxs-lookup"><span data-stu-id="15310-115">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
