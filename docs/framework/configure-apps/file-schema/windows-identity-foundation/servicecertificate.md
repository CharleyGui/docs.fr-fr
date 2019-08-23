---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942411"
---
# <a name="servicecertificate"></a>\<serviceCertificate>
Configure le certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<serviceCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).|  
  
## <a name="example"></a>Exemples  
 Le code XML suivant montre l’utilisation de \<l’élément serviceCertificate >. Le code XML est extrait de `CustomToken` l’exemple.  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
