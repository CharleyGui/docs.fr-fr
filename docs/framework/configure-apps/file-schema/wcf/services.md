---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854979"
---
# <a name="services"></a>\<services>
Les services sont définis dans la section `services` du fichier de configuration. Chacun dispose de sa propre section de configuration de `service`.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<services >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<service>](service.md)|Définissez le contrat de service, le comportement et les points de terminaison du service particulier.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServicesSection>
