---
title: Génération de la bibliothèque client service de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: f73ea93fe76f31c81935dbfb29183c247e41d8cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975286"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Génération de la bibliothèque client service de données (services de données WCF)
Un service de données qui implémente le Open Data Protocol (OData) peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le flux OData. Pour plus d’informations, consultez [OData : document de métadonnées du service](https://go.microsoft.com/fwlink/?LinkId=186070). Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service OData. Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par un flux OData dans un projet client, il effectue les actions suivantes :  
  
- Demande le document de métadonnées du service de données et interprète les métadonnées retournées.  
  
    > [!NOTE]
    > Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx. Ce fichier .edmx ne peut pas s’ouvrir à l’aide d’Entity Data Model Designer parce qu’il n’a pas le même format que les fichiers .edmx utilisés par Entity Framework. Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte. Pour plus d’informations, consultez la spécification [\[MC-EDMX\]: Entity Data Model pour le format d’Empaquetage Data Services](https://go.microsoft.com/fwlink/?LinkID=178833)  
  
- Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>. Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model. Pour plus d’informations, consultez [Vue d’ensemble d’Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.  
  
- Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.  
  
 Pour plus d’informations, consultez [Comment : ajouter une référence de service de données](how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Les classes de service de données client peuvent également être générées à l’aide de l’outil [outil DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) à l’invite de commandes. Pour plus d’informations, consultez [Comment : générer manuellement des classes de service de données client](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mappage de type de données client  
 Quand vous utilisez la boîte de dialogue **Ajouter une référence de service** dans Visual Studio ou l’outil `DataSvcUtil.exe` pour générer des classes de données clientes basées sur un flux OData, les types de données .NET Framework sont mappés aux types primitifs à partir du modèle de données comme suit :  
  
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
  
 Pour plus d’informations, consultez [OData : types de données primitifs](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
- [Démarrage rapide](quickstart-wcf-data-services.md)
