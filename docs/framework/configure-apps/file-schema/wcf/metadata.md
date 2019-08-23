---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 4555dc9c2e0b783de2fb57e47c9aada0d69462e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931302"
---
# <a name="metadata"></a>\<metadata>
Indique la façon dont les métadonnées peuvent être traitées.  
  
 \<system.ServiceModel>  
\<client>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons. Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.|  
|[\<wsdlImporters >](wsdlimporters.md)|Indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy. Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison. Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion. Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<client>](client.md)|La section client définit la liste de points de terminaison auxquels un client peut se connecter.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Configuration du client WCF](../../../wcf/feature-details/client-configuration.md)
- [Clients](../../../wcf/feature-details/clients.md)
