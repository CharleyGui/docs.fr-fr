---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 583fef7eb364c39890b3f9304770b383c1ea6d2a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183505"
---
# \<certificateValidation>

Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats. Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509. La valeur par défaut est « PeerOrChainTrust ». Pour spécifier un validateur personnalisé, affectez la valeur « Custom » à cet attribut et spécifiez le validateur à l’aide de l' [\<certificateValidator>](certificatevalidator.md) élément. Optionnel.|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509. La valeur par défaut est « online ». Optionnel.|  
|trustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie le magasin de certificats X. 509. La valeur par défaut est « LocalMachine ». Optionnel.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|Spécifie un type personnalisé pour la validation du certificat. Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [\<certificateValidation>](certificatevalidation.md) élément a la valeur « Custom ».|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes  

 Un `<certificateValidation>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons de sécurité sous l' `<securityTokenHandlerConfiguration>` élément. Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service. Certains gestionnaires de jetons vous permettent de spécifier des paramètres de validation de certificat dans la configuration. Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés au niveau du service et de la collection du gestionnaire de jetons de sécurité.  
  
## <a name="example"></a>Exemple  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
