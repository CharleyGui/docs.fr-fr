---
title: Publication de points de terminaison de métadonnées
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5be27a72c87d95e36a5b283e7930ba0a5191a5a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249759"
---
# <a name="publishing-metadata-endpoints"></a>Publication de points de terminaison de métadonnées

Les services Windows Communication Foundation (WCF) publient les métadonnées en publiant un ou plusieurs points de terminaison de métadonnées. La publication de métadonnées de service permet d'accéder à celles-ci à l'aide de protocoles standardisés, tels que WS-MetadataExchange (MEX) et les requêtes HTTP/GET. Les points de terminaison de métadonnées sont semblables aux autres points de terminaison de service dans le sens où ils ont une adresse, une liaison et un contrat, et qu’ils peuvent être ajoutés à un hôte de service via la configuration ou dans du code. Pour activer la publication de points de terminaison de métadonnées, vous devez ajouter le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior> au service.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Procédure : publier des métadonnées pour un service à l’aide d’un fichier de configuration](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Montre comment configurer un service WCF pour publier des métadonnées afin que les clients puissent récupérer les métadonnées à l’aide d’une WS-MetadataExchange ou d’une requête HTTP/obtenir à l’aide de la `?wsdl` chaîne de requête.  
  
 [Procédure : publier des métadonnées pour un service à l’aide de code](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Montre comment activer la publication des métadonnées pour un service WCF dans le code afin que les clients puissent récupérer les métadonnées à l’aide d’une WS-MetadataExchange ou d’une requête HTTP/obtenir à l’aide de la `?wsdl` chaîne de requête.  
  
## <a name="see-also"></a>Voir aussi

- [Publication de métadonnées](./feature-details/publishing-metadata.md)
