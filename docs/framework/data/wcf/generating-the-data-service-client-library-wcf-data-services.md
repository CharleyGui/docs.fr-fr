---
title: Génération de la bibliothèque client service de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: bf0a74bd010a188f38cf1a2088a449d97405fa0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626383"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Génération de la bibliothèque client service de données (services de données WCF)
Un service de données qui implémente le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux. Pour plus d’informations, consultez [OData : Document de métadonnées de service](https://go.microsoft.com/fwlink/?LinkId=186070). Vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-en fonction de service. Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par une [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de flux dans un projet client, il effectue les actions suivantes :  
  
- Demande le document de métadonnées du service de données et interprète les métadonnées retournées.  
  
    > [!NOTE]
    >  Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx. Ce fichier .edmx ne peut pas s’ouvrir à l’aide d’Entity Data Model Designer parce qu’il n’a pas le même format que les fichiers .edmx utilisés par Entity Framework. Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte. Pour plus d’informations, consultez le [ \[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) spécification  
  
- Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>. Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model. Pour plus d’informations, consultez [Vue d’ensemble d’Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.  
  
- Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.  
  
 Pour plus d'informations, voir [Procédure : Ajouter une référence de Service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Les classes de service de données client peuvent également être générées à l’aide de la [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) outil à l’invite de commandes. Pour plus d'informations, voir [Procédure : Générer manuellement les Classes de Service de données Client](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mappage de type de données client  
 Lorsque vous utilisez le **ajouter une référence de Service** boîte de dialogue dans Visual Studio ou le `DataSvcUtil.exe` outil pour générer des classes de données client qui sont basés sur un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux, les types de données .NET Framework sont mappés aux types primitifs à partir de la le modèle de données comme suit :  
  
|Type de modèle de données|Types de données .NET Framework|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 Pour plus d’informations, consultez [OData : Types de données primitifs](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
