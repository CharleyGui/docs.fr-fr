---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854994"
---
# \<servicePrincipalName>
Spécifie l'identité d'un service par son nom de principal du service (SPN).  
  
Pour plus d’informations sur la définition du SPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|value|Nom par lequel un client identifie de manière unique une instance d'un service. Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN. Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## <a name="remarks"></a>Remarques  
 Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise le SPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
