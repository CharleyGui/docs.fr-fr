---
title: Fournisseurs de services de données personnalisés (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: c5f6bd001a5198f14bf05c0730f3988d54142eae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569245"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Fournisseurs de services de données personnalisés (WCF Data Services)
WCF Data Services comprend un ensemble de fournisseurs qui vous permet de définir un modèle de données basé sur des types de données à liaison tardive.  
  
|Fournisseur|Description|  
|--------------|-----------------|  
|Fournisseur de métadonnées|Il s'agit du fournisseur de services de données personnalisé principal qui vous permet de définir pendant l'exécution un modèle de données personnalisé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.|  
|Fournisseur de requête|Ce fournisseur vous permet d'exécuter des requêtes sur un modèle de données personnalisé défini à l'aide de l'interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>. Le fournisseur de requête est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceQueryProvider>.|  
|Fournisseur de mise à jour|Ce fournisseur vous permet d'effectuer des mises à jour sur les types exposés dans un fournisseur de services de données personnalisé et de gérer l'accès concurrentiel. Un fournisseur de mise à jour est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceUpdateProvider>|  
|Fournisseur de pagination|Ce fournisseur est utilisé avec le fournisseur de services de données personnalisé pour permettre la prise en charge de la pagination pilotée par le serveur. Un fournisseur de pagination pour un service de données personnalisé est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServicePagingProvider>.|  
|Fournisseur de diffusion en continu|Ce fournisseur vous permet d'exposer des types de données d'objet blob (binary large object) sous forme de flux en continu. Un fournisseur de diffusion en continu est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Le fournisseur de diffusion en continu peut également être utilisé avec Entity Framework et des fournisseurs de source de données de réflexion. Pour plus d’informations, consultez la page [fournisseur de streaming](streaming-provider-wcf-data-services.md).|  
  
 Pour plus d’informations, consultez l’article [fournisseurs de services de données personnalisés](https://go.microsoft.com/fwlink/?LinkID=186850) et la boîte à outils du fournisseur d’Open Data Protocol (OData) dans le [Kit de développement logiciel (SDK) OData](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
- [Fournisseur Entity Framework](entity-framework-provider-wcf-data-services.md)
- [Fournisseur de réflexion](reflection-provider-wcf-data-services.md)
