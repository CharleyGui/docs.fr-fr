---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936411"
---
# <a name="serviceauthenticationmanager"></a>\<serviceAuthenticationManager>
Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un donneur d'ordre.  
  
\<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<serviceAuthenticationManager>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|serviceAuthenticationManagerType|Chaîne qui spécifie le type de la stratégie d'authentification pour le comportement actuel.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
