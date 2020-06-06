---
title: Élément <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 328411a429cd42927a190c6805a1f5e2b3555ea1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448450"
---
# <a name="httpdigest-element"></a>Élément \<httpDigest>
Spécifie une information d'identification de type condensé utilisée lors de l'authentification du client à un service.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`impersonationLevel`|Définit la préférence d'emprunt d'identité que le client communique au serveur. Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur. Les valeurs valides sont les suivantes :<br /><br /> -Identification : le serveur peut accéder à l’identité et aux privilèges du client, mais ne peut pas emprunter l’identité du client.<br />-Emprunt d’identité : le serveur peut emprunter l’identité du contexte de sécurité du client sur le système local.<br />-Delegation : le serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants.<br />-Anonymous : le serveur ne peut pas emprunter l’identité ou identifier le client.<br />-None : aucun niveau d’emprunt d’identité n’est assigné.<br /><br /> La valeur par défaut est Identification. Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## <a name="remarks"></a>Remarques  
 Un condensat est un hachage déterminé à l’aide d’un algorithme et d’un jeu d’entrées. L'authentificateur et l'authentifié acceptent un algorithme et échangent les données utilisées comme entrées. Le client peut calculer le hachage et l'envoyer au service. Le service calcule également le hachage et compare les valeurs. Une correspondance valide le client.  
  
 Cette fonction doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services). Pour plus d’informations, consultez [authentification Digest dans IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
