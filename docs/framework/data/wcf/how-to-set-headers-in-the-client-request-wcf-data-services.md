---
title: 'Procédure : définir des en-têtes dans la demande cliente (WCF Data Services)'
description: Apprenez à gérer l’événement SendingRequest pour ajouter un nouvel en-tête au message de requête avant de l’envoyer au service de données dans WCF Data Services.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: fab1fcfdf92d275f51f433845aa0c253a00ec99d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247763"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Procédure : définir des en-têtes dans la demande cliente (WCF Data Services)
Lorsque vous utilisez la bibliothèque cliente WCF Data Services pour accéder à un service de données qui prend en charge le Open Data Protocol (OData), la bibliothèque cliente définit automatiquement les en-têtes HTTP requis dans les messages de demande envoyés au service de données. Toutefois, la bibliothèque cliente ne sait pas définir les en-têtes de message requis dans certains cas, par exemple, quand le service de données exige une authentification basée sur des revendication ou des cookies. Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication). Dans ces cas, vous devez définir manuellement les en-têtes dans le message de demande avant de le transmettre. L'exemple de cette rubrique illustre comment utiliser l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> pour ajouter un nouvel en-tête au message de demande avant qu'il ne soit envoyé au service de données.  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md). Vous pouvez également utiliser l' [exemple de service de données Northwind](https://services.odata.org/Northwind/Northwind.svc/) publié sur le site Web OData. Cet exemple de service de données est en lecture seule et toute tentative d’enregistrement des modifications retourne une erreur. Les exemples de services de données sur le site Web OData autorisent l’authentification anonyme.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant enregistre un gestionnaire pour l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, puis exécute une requête sur le service de données.  
  
> [!NOTE]
> Lorsqu'un service de données exige que vous définissiez manuellement l'en-tête de message de chaque demande, considérez d'utiliser un gestionnaire pour l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> en remplaçant la méthode `OnContextCreated` partielle dans le conteneur d'entités qui représente le service de données, dans ce cas : `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemple  
 La méthode suivante utilise l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> et ajoute un en-tête automatique à la demande.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Voir aussi

- [Securing WCF Data Services](securing-wcf-data-services.md)
- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
