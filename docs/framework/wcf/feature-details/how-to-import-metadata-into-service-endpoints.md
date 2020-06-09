---
title: 'Comment : importer des métadonnées dans des points de terminaison de service'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597057"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Comment : importer des métadonnées dans des points de terminaison de service
Cette rubrique explique comment importer des métadonnées dans une collection de points de terminaison de service et comment utiliser le service défini dans la [prise en main](../samples/getting-started-sample.md). Cette rubrique montre comment créer une application cliente qui importe les métadonnées à partir du service, puis appelle la méthode `Add` sur le service.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Pour importer des métadonnées dans des points de terminaison de service  
  
1. Déclarez un objet <xref:System.ServiceModel.EndpointAddress> et initialisez-le avec l'URI (Uniform Resource Identifier) de l'adresse d'échange de métadonnées (MEX) du service.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Créez un <xref:System.ServiceModel.Description.MetadataExchangeClient> en passant l'adresse MEX, puis appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Cette opération récupère les métadonnées du service.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Créez un <xref:System.ServiceModel.Description.WsdlImporter> en passant les métadonnées précédemment récupérées, puis appelez <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Cette opération génère une collection d’objets <xref:System.ServiceModel.Description.ContractDescription>. Vous pouvez aussi appeler <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> ou <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, selon vos besoins.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Après avoir importé les métadonnées, vous ne pourrez pas créer un canal client ou exporter les métadonnées. En effet, aucune information de type n'est disponible à ce stade. Les informations de type sont requises pour interagir concrètement avec le service ou exporter les métadonnées. Pour générer les informations de type, vous devez générer le code (comme indiqué aux étapes 4 et 5). Vous pouvez également utiliser la classe d'assistance <xref:System.ServiceModel.Description.MetadataResolver>. Pour plus d’informations, consultez [Comment : utiliser MetadataResolver pour obtenir dynamiquement des métadonnées de liaison](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4. Générez des informations de type pour chaque contrat.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Vous pouvez désormais utiliser ces informations. L'exemple suivant génère un code source C#.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Métadonnées](metadata.md)
- [Prise en main](../samples/getting-started-sample.md)
