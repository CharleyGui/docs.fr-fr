---
title: <windows>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940310"
---
# <a name="windows-of-clientcredentials-element"></a>\<> Windows de \<l’élément ClientCredentials >
Spécifie les paramètres pour des informations d'identification Windows à utiliser pour représenter le client.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<> de comportement  
\<clientCredentials>  
\<windows>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Définit la préférence d'emprunt d'identité que le client communique au serveur. Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur. Les valeurs valides sont les suivantes :<br /><br /> Détermination Le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.<br />Emprunt d’identité Le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.<br />Délégation Le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.<br />Façon Le serveur ne peut pas emprunter l’identité ou identifier le client.<br />None Un niveau d’emprunt d’identité n’est pas assigné.<br /><br /> La valeur par défaut est Identification. Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|L'affectation de la valeur `true` à cette propriété permet de rétrograder l'authentification à NTLM si Kerberos n'est pas disponible.<br /><br /> Si vous affectez `false` la valeur à cette propriété, Windows Communication Foundation (WCF) est le meilleur effort pour lever une exception si NTLM est utilisé. Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
