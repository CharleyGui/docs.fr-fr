---
title: Génération de la bibliothèque client service de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 050a791736e90b5daf46fd272197ca21a220afb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172617"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Génération de la bibliothèque client service de données (services de données WCF)

Un service de données qui implémente le Open Data Protocol (OData) peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le flux OData. Pour plus d’informations, consultez la section document de métadonnées de service dans l’article [OData : Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) . Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service OData. Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par un flux OData dans un projet client, il effectue les actions suivantes :  
  
- Demande le document de métadonnées du service de données et interprète les métadonnées retournées.  
  
    > [!NOTE]
    > Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx. Ce fichier .edmx ne peut pas s’ouvrir à l’aide d’Entity Data Model Designer parce qu’il n’a pas le même format que les fichiers .edmx utilisés par Entity Framework. Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte. Pour plus d’informations, consultez [ \[ MC-EDMX \] : Entity Data Model pour le format d’empaquetage Data Services](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).
  
- Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>. Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model. Pour plus d’informations, consultez [Vue d’ensemble d’Object Services (Entity Framework)](/previous-versions/bb386871(v=vs.100)).  
  
- Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.  
  
- Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.  
  
 Pour plus d’informations, consultez [Comment : ajouter une référence de service de données](how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Les classes de service de données client peuvent également être générées à l’aide de l’outil [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) à partir de l’invite de commandes. Pour plus d’informations, consultez [Comment : générer manuellement des classes de service de données client](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mappage de type de données client  

 Quand vous utilisez la boîte de dialogue **Ajouter une référence de service** dans Visual Studio ou l' `DataSvcUtil.exe` outil pour générer des classes de données clientes basées sur un flux OData, les types de données .NET Framework sont mappés aux types primitifs à partir du modèle de données comme suit :  
  
|Type de modèle de données|Type de données .NET Framework.|  
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
  
 Pour plus d’informations, consultez la section types de données primitifs de l’article [OData : vue d’ensemble](https://www.odata.org/documentation/odata-version-2-0/overview/) .
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
- [Démarrage rapide](quickstart-wcf-data-services.md)
