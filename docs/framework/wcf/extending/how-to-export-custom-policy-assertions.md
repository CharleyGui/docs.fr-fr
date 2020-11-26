---
title: 'Procédure : exporter des assertions de stratégie personnalisées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 8bdc9948d6846631fde1d428c113682f40d15ec3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249213"
---
# <a name="how-to-export-custom-policy-assertions"></a>Procédure : exporter des assertions de stratégie personnalisées

Les assertions de stratégie décrivent les fonctions et les exigences d’un point de terminaison de service. Les applications de service peuvent utiliser des assertions de stratégie personnalisées dans les métadonnées de service pour communiquer des informations de personnalisation de point de terminaison, de liaison ou de contrat à l'application cliente. Vous pouvez utiliser Windows Communication Foundation (WCF) pour exporter des assertions dans les expressions de stratégie jointes aux liaisons WSDL au point de terminaison, à l’opération ou aux objets de message, selon les fonctionnalités ou les exigences que vous communiquez.  
  
 Les assertions de stratégie personnalisées sont exportées en implémentant l’interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> sur <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> et en insérant directement l’élément de liaison dans la liaison du point de terminaison de service ou en inscrivant l’élément de liaison dans le fichier de configuration de l’application. Votre implémentation de l'exportation de la stratégie doit ajouter votre assertion de stratégie personnalisée comme une instance <xref:System.Xml.XmlElement?displayProperty=nameWithType> au <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> approprié sur le <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> qui est passé dans la méthode <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>.  
  
 En outre, vous devez vérifier la propriété <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> de la classe <xref:System.ServiceModel.Description.WsdlExporter> et exporter les expressions de stratégie imbriquées et les attributs de l'infrastructure de stratégie dans l'espace de noms correct en fonction de la version de stratégie spécifiée.  
  
 Pour importer des assertions de stratégie personnalisées, consultez <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> et [Comment : importer des assertions de stratégie personnalisées](how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Pour exporter des assertions de stratégie personnalisées  
  
1. Implémentez l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> sur un <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. L'exemple de code ci-dessous montre l'implémentation d'une assertion de stratégie personnalisée au niveau de la liaison.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Insérez l’élément de liaison dans la liaison de point de terminaison par programme ou à l’aide d’un fichier de configuration d’application. Reportez-vous aux procédures ci-dessous.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Pour insérer un élément de liaison à l'aide d'un fichier de configuration d'application  
  
1. Implémentez <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> pour l’élément de liaison de l’assertion de stratégie personnalisée.  
  
2. Ajoutez l’extension d’élément de liaison au fichier de configuration à l’aide de l' [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) élément.  
  
3. Créez une liaison personnalisée à l’aide de <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Pour insérer un élément de liaison par programme  
  
1. Créez un nouveau <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> et ajoutez-le à un <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2. Ajoutez la liaison personnalisée de l’étape 1. à un nouveau point de terminaison et ajoutez ce nouveau point de terminaison de service au <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> en appelant la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
3. Ouvrez le fichier <xref:System.ServiceModel.ServiceHost>. L'exemple de code ci-dessous montre la création d'une liaison personnalisée et l'insertion par programme d'éléments de liaison.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Procédure : importer des assertions de stratégie personnalisées](how-to-import-custom-policy-assertions.md)
