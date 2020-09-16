---
title: "Procédure : activer l'accès au service de données (WCF Data Services)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 377b031c48ed831cfa5e270426283ed03a55f886
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542305"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Procédure : activer l'accès au service de données (WCF Data Services)
Dans WCF Data Services, vous devez accorder explicitement l’accès aux ressources exposées par un service de données. Cela signifie qu'après avoir créé un service de données, vous devez encore fournir explicitement l'accès à des ressources individuelles comme les jeux d'entités. Cette rubrique montre comment activer l’accès en lecture et en écriture à cinq des jeux d’entités dans le service de données Northwind créé lorsque vous effectuez le [démarrage rapide](quickstart-wcf-data-services.md). Puisque l'énumération <xref:System.Data.Services.EntitySetRights> est définie à l'aide de l'objet <xref:System.FlagsAttribute>, vous pouvez utiliser un opérateur OR logique pour spécifier plusieurs autorisations pour un jeu d'entités unique.  
  
> [!NOTE]
> Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données. Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même. Pour plus d’informations, consultez [sécurisation des sites Web ASP.net](/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Pour activer l'accès au service de données  
  
- Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Cela permet aux clients de disposer d'un accès en lecture et en écriture aux jeux d'entités `Orders` et `Order_Details` et d'un accès en lecture seule aux jeux d'entités `Customers`.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Développer un WCF Data Service qui fonctionne sur IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Configuration du service de données](configuring-the-data-service-wcf-data-services.md)
