---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941156"
---
# <a name="transportconfigurationtypes"></a>\<transportConfigurationTypes>
Représente une collection d’éléments de configuration identifiant le type d’un transport particulier. Peut être utilisé pour ajouter des protocoles WAS personnalisés.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
\<transportConfigurationTypes>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Nom du transport.|  
|transportConfigurationType|Type qui implémente le transport.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|Ajoute un élément de configuration identifiant le type d'un transport particulier.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [Hébergement](../../../wcf/feature-details/hosting.md)
