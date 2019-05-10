---
title: Exportation de métadonnées personnalisées pour une extension WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: ecca7e311e113e2aade360e4718d1bed4ea7feef
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627111"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Exportation de métadonnées personnalisées pour une extension WCF
Dans Windows Communication Foundation (WCF), exportation de métadonnées est le processus de décrire des points de terminaison de service et les projeter dans une représentation parallèle standardisée qui les clients peuvent utiliser pour comprendre comment utiliser le service. Les métadonnées personnalisées sont composées d'éléments XML que les exportateurs de métadonnées fournis par le système ne peuvent pas exporter. En général, cela inclut les éléments WSDL personnalisés des comportements définis par l'utilisateur ainsi que les éléments de liaison et les assertions de stratégie relatives aux fonctions et spécifications des liaisons et contrats.  
  
 Cette section décrit l'exportation des éléments WSDL personnalisés ou des assertions de stratégie, mais ne traite pas du processus d'exportation lui-même. Pour plus d’informations sur la façon d’utiliser les types qui exportent et importent des métadonnées, que celles-ci soient personnalisées ou générées par le système, consultez [exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Vue d'ensemble  
 Lorsque les métadonnées sont publiées à l’aide de la <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, le <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> est examiné et XSD et WSDL, y compris les assertions de stratégie--sont générés pour tous les contrats et les liaisons WCF peut prendre en charge à l’aide de liaisons et des attributs fournis par le système. Toutefois, les éléments de liaison ou les attributs de comportement personnalisés requièrent une prise en charge pour pouvoir être exportés correctement.  
  
 Cette section décrit :  
  
1. Comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>, laquelle vous expose les données de génération WSDL avant de publier le WSDL.  
  
2. Comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>, laquelle vous expose les données de stratégie avant d'exporter les assertions de stratégie dans les données WSDL.  
  
 Pour plus d’informations sur l’importation WSDL personnalisée et les assertions de stratégie, consultez [l’importation de métadonnées personnalisées pour une Extension WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Exportation d'éléments WSDL personnalisés  
 Implémentez <xref:System.ServiceModel.Description.IWsdlExportExtension> sur un comportement d'opération, comportement de contrat, comportement de point de terminaison ou élément de liaison (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior> ou <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> respectivement) et insérez les comportements ou éléments de liaison dans la description du service que vous tentez d'exporter. (Pour plus d’informations sur l’insertion de comportements, consultez [configuration et extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> est appelé pour chaque point de terminaison et chaque point de terminaison exporte en premier le contrat si cela n'a pas été déjà fait. Selon vos besoins, vous pouvez participer à l'un ou à l'autre processus d'exportation :  
  
- <xref:System.ServiceModel.Description.WsdlContractConversionContext> permet de modifier les métadonnées exportées dans la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>.  
  
- <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> permet de modifier les métadonnées exportées pour le point de terminaison dans la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>.  
  
 La méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> est appelée sur toutes les implémentations <xref:System.ServiceModel.Description.IWsdlExportExtension> dans l'instance <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> exportée.  La méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> est appelée sur toutes les implémentations <xref:System.ServiceModel.Description.IWsdlExportExtension> avec l'instance <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> exportée.  
  
 Pour plus d'informations, voir [Procédure : Exportation personnalisée WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) et l’exemple [personnalisé WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Exportation d'assertions de stratégie personnalisées  
 Implémentez <xref:System.ServiceModel.Description.IPolicyExportExtension> sur un <xref:System.ServiceModel.Channels.BindingElement> et ajoutez l'élément de liaison à la liaison pour écrire des assertions de stratégie personnalisées concernant la prise en charge de la liaison et les fonctions de contrat dans le WSDL. <xref:System.ServiceModel.Description.IPolicyExportExtension> est appelé une fois lors de l’exportation de l’élément de liaison implémenté dans une liaison, et passe <xref:System.ServiceModel.Description.PolicyConversionContext> à la méthode <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>. Vous pouvez utiliser les méthodes sur l'instance <xref:System.ServiceModel.Description.PolicyConversionContext> à ajouter aux assertions de stratégie jointe à la liaison WSDL au niveau des objets de message, d'opération ou de point de terminaison.  
  
 Pour plus d'informations, voir [Procédure : Exporter des Assertions de stratégie personnalisées](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Exporter le fichier WSDL personnalisé](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Guide pratique pour Exporter des Assertions de stratégie personnalisées](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)
- [Importation de métadonnées personnalisées pour une extension WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
