---
title: 'Procédure : utiliser MetadataExchangeClient pour récupérer des métadonnées'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 412e695036f29886310099cc5a55b940247b0c72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280830"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Procédure : utiliser MetadataExchangeClient pour récupérer des métadonnées

Utilisez la classe <xref:System.ServiceModel.Description.MetadataExchangeClient> pour télécharger les métadonnées à l'aide du protocole WS-MetadataExchange (MEX). Les fichiers de métadonnées récupérés sont retournés sous forme d'objet <xref:System.ServiceModel.Description.MetadataSet>. L'objet <xref:System.ServiceModel.Description.MetadataSet> retourné contient une collection d'objets <xref:System.ServiceModel.Description.MetadataSection>, chacun d'eux contenant un dialecte de métadonnées spécifique ainsi qu'un identificateur. Vous pouvez inscrire les métadonnées retournées dans des fichiers. Si ces métadonnées contiennent des documents WSDL (Web Services Description Language), vous pouvez également les importer à l'aide de <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 Les constructeurs <xref:System.ServiceModel.Description.MetadataExchangeClient> qui acceptent une adresse utilisent la liaison de la classe statique <xref:System.ServiceModel.Description.MetadataExchangeBindings> correspondant au modèle URI de cette adresse. Vous pouvez également utiliser le constructeur <xref:System.ServiceModel.Description.MetadataExchangeClient> permettant de spécifier de manière explicite la liaison à utiliser. La liaison spécifiée est utilisée pour résoudre toutes les références de métadonnées.  
  
 Comme tout autre client Windows Communication Foundation (WCF), le <xref:System.ServiceModel.Description.MetadataExchangeClient> type fournit un constructeur pour le chargement des configurations de point de terminaison client à l’aide du nom de configuration du point de terminaison. La configuration de point de terminaison indiquée doit spécifier le contrat <xref:System.ServiceModel.Description.IMetadataExchange>. L'adresse de la configuration de point de terminaison n'est pas chargée, vous devez donc utiliser l'une des surcharges <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> acceptant une adresse. Lorsque vous spécifiez l'adresse des métadonnées à l'aide d'une instance <xref:System.ServiceModel.EndpointAddress>, le client <xref:System.ServiceModel.Description.MetadataExchangeClient> part du principe que cette adresse renvoie à un point de terminaison MEX. Si vous utilisez une adresse URL pour définir l'adresse des métadonnées, vous devez également spécifié le client <xref:System.ServiceModel.Description.MetadataExchangeClientMode> à utiliser, à savoir MEX ou HTTP GET.  
  
> [!IMPORTANT]
> Par défaut, le client <xref:System.ServiceModel.Description.MetadataExchangeClient> résout toutes les références, notamment les inclusions et importations de schémas WSDL et XML. Vous pouvez désactiver cette fonctionnalité en affectant à la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `false`. Vous pouvez contrôler le nombre maximal de références à résoudre à l'aide de la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A>. Vous pouvez utiliser cette propriété en parallèle avec la propriété `MaxReceivedMessageSize` sur la liaison pour contrôler la quantité de métadonnées à récupérer.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Pour utiliser MetadataExchangeClient afin de récupérer des métadonnées  
  
1. Créez un objet <xref:System.ServiceModel.Description.MetadataExchangeClient> en spécifiant explicitement une liaison, le nom de la configuration du point de terminaison ou l’adresse des métadonnées.  
  
2. Configurez le client <xref:System.ServiceModel.Description.MetadataExchangeClient> en fonction de vos besoins. Par exemple, vous pouvez spécifier les informations d'identification à utiliser lors de la demande de métadonnées, les modalités de résolution des références de métadonnées ainsi que la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> pour définir le délai au terme duquel la demande de métadonnées expire.  
  
3. Récupérez l'objet <xref:System.ServiceModel.Description.MetadataSet> qui contient les métadonnées récupérées en appelant l'une des méthodes <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Remarque : vous pouvez utiliser uniquement la surcharge <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> n’acceptant pas d’arguments si vous avez spécifié une adresse de manière explicite pendant la construction de <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a> Exemple  

 L'exemple de code suivant indique comment utiliser <xref:System.ServiceModel.Description.MetadataExchangeClient> pour télécharger et énumérer des fichiers de métadonnées.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Compilation du code  

 Pour compiler cet exemple de code, vous devez référencer l'assembly System.ServiceModel.dll et importer l'espace de noms <xref:System.ServiceModel.Description>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
