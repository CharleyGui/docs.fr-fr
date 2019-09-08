---
title: Génération de la bibliothèque client service de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: d53f2d209d6fb0a6f3cadb96245338060ece87db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780292"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Génération de la bibliothèque client service de données (services de données WCF)
Un service de données qui implémente [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] le peut retourner un document de métadonnées de service qui décrit le modèle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de données exposé par le flux. Pour plus d’informations, [consultez OData : Document](https://go.microsoft.com/fwlink/?LinkId=186070)de métadonnées du service. Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]à un service basé sur. Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] par un flux dans un projet client, il effectue les actions suivantes :  
  
- Demande le document de métadonnées du service de données et interprète les métadonnées retournées.  
  
    > [!NOTE]
    > Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx. Ce fichier .edmx ne peut pas s’ouvrir à l’aide d’Entity Data Model Designer parce qu’il n’a pas le même format que les fichiers .edmx utilisés par Entity Framework. Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte. Pour plus d’informations, voir [ \[MC-edmx\]: Entity Data Model pour la spécification de](https://go.microsoft.com/fwlink/?LinkID=178833) format d’empaquetage Data Services  
  
- Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>. Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model. Pour plus d’informations, consultez [Vue d’ensemble d’Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.  
  
- Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.  
  
 Pour plus d’informations, consultez [Guide pratique pour Ajoutez une référence](how-to-add-a-data-service-reference-wcf-data-services.md)de service de données.  
  
 Les classes de service de données client peuvent également être générées à l’aide de l’outil [outil DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) à l’invite de commandes. Pour plus d’informations, consultez [Guide pratique pour Générez manuellement des classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)de service de données client.  
  
## <a name="client-data-type-mapping"></a>Mappage de type de données client  
 Quand vous utilisez la boîte de dialogue **Ajouter une référence de service** dans Visual Studio `DataSvcUtil.exe` ou l’outil pour générer des classes de données clientes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] basées sur un flux, les types de données .NET Framework sont mappés aux types primitifs à partir du modèle de données comme suit :  
  
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
  
 Pour plus d’informations, [consultez OData : Types](https://go.microsoft.com/fwlink/?LinkId=186072)de données primitifs.  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
- [Démarrage rapide](quickstart-wcf-data-services.md)
