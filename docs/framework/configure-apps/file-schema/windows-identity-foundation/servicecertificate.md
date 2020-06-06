---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251854"
---
# \<serviceCertificate>
Configure le certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
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
 Aucune  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).|  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre l’utilisation de l' \<serviceCertificate> élément. Le code XML est extrait de l' `CustomToken` exemple.  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
