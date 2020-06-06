---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855063"
---
# \<policyImporter>
Indique un importateur de stratégie qui contrôle l’importation d’assertions de stratégie personnalisées concernant les liaisons.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`type`|Type de cet élément.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.|  
  
## <a name="remarks"></a>Remarques  
 Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [Configuration client WCF](../../../wcf/feature-details/client-configuration.md)
- [Clients](../../../wcf/feature-details/clients.md)
