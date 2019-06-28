---
title: Publication de métadonnées
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 54ab05f32320f3084fc609d8107f2892ffe6efbd
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424579"
---
# <a name="publishing-metadata"></a>Publication de métadonnées
Services Windows Communication Foundation (WCF) publient les métadonnées en publiant un ou plusieurs points de terminaison de métadonnées. La publication de métadonnées de service permet d'accéder à celles-ci à l'aide de protocoles standardisés, tels que WS-MetadataExchange (MEX) et les requêtes HTTP/GET. Les points de terminaison de métadonnées sont semblables aux autres points de terminaison de service dans le sens où ils ont une adresse, une liaison et un contrat, et qu’ils peuvent être ajoutés à un hôte de service via la configuration ou du code impératif.  
  
## <a name="publishing-metadata-endpoints"></a>Publication de points de terminaison de métadonnées  
 Pour publier des points de terminaison de métadonnées pour un service WCF, vous devez d’abord ajouter le <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportement au service de service. L'ajout d'une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> permet à votre service d'exposer des points de terminaison de métadonnées. Après avoir ajouté le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, vous pouvez ensuite exposer les points de terminaison de métadonnées qui prennent en charge le protocole MEX ou qui répondent aux requêtes HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> utilise <xref:System.ServiceModel.Description.WsdlExporter> pour exporter les métadonnées de tous les points de terminaison de service de votre service. Pour plus d’informations sur l’exportation des métadonnées à partir d’un service, consultez [exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> ajoute une instance <xref:System.ServiceModel.Description.ServiceMetadataExtension> comme extension à votre hôte de service. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> fournit l'implémentation pour les protocoles de publication de métadonnées. Vous pouvez également utiliser <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> pour obtenir les métadonnées de service au moment de l'exécution en accédant à la propriété <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType>.  
  
### <a name="mex-metadata-endpoints"></a>Points de terminaison de métadonnées MEX  
 Pour ajouter des points de terminaison de métadonnées qui utilisent le protocole MEX, ajoutez des points de terminaison de service à votre hôte de service qui utilisent le contrat de service nommé `IMetadataExchange`. WCF inclut un <xref:System.ServiceModel.Description.IMetadataExchange> interface portant ce nom de contrat de service que vous pouvez utiliser en tant que partie du modèle de programmation WCF. Points de terminaison WS-MetadataExchange ou de points de terminaison MEX, peuvent utiliser une des liaisons par défaut de quatre qui les méthodes de fabrique statiques exposent sur la <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe pour faire correspondre les liaisons par défaut utilisés par les outils WCF tels que Svcutil.exe. Vous pouvez également configurer des points de terminaison de métadonnées MEX à l’aide de votre propre liaison personnalisée.  
  
### <a name="http-get-metadata-endpoints"></a>Points de terminaison de métadonnées HTTP GET  
 Pour ajouter un point de terminaison de métadonnées à votre service qui répond aux requêtes HTTP/GET, affectez <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> sur `true`. Vous pouvez également configurer un point de terminaison de métadonnées qui utilise HTTPS en affectant <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> sur `true`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Publier les métadonnées d’un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Montre comment configurer un service WCF pour publier les métadonnées afin que les clients peuvent récupérer les métadonnées à l’aide d’un échange WS-MetadataExchange ou une requête HTTP/GET en utilisant le `?wsdl` chaîne de requête.  
  
 [Guide pratique pour Publier les métadonnées d’un Service à l’aide de Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Montre comment activer la publication de métadonnées pour un service WCF dans le code afin que les clients peuvent récupérer les métadonnées à l’aide d’un échange WS-MetadataExchange ou une requête HTTP/GET en utilisant le `?wsdl` chaîne de requête.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Voir aussi

- [Exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
