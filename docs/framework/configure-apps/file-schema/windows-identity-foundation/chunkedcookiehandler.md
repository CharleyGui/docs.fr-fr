---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: a321c10e04eca2c1a5204929966a1725e918cbdf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158524"
---
# \<chunkedCookieHandler>

Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Cet élément ne peut être présent que si l' `mode` attribut de l' `<cookieHandler>` élément est « default » ou « chunked ».  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|chunkSize|Taille maximale, en caractères, des données de cookie HTTP pour un cookie HTTP. Vous devez être prudent lors de l’ajustement de la taille de segment. Les navigateurs Web ont des limites différentes quant à la taille des cookies et au nombre autorisé par domaine. Par exemple, la spécification Netscape d’origine a stipulé les limites suivantes : 300 cookies au total, 4096 octets par en-tête de cookie (y compris les métadonnées, pas seulement la valeur du cookie) et 20 cookies par domaine. La valeur par défaut est 2000. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Configure le <xref:System.IdentityModel.Services.CookieHandler> que le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) utilise pour lire et écrire des cookies.|  
  
## <a name="remarks"></a>Notes  

 Lorsque vous spécifiez un <xref:System.IdentityModel.Services.ChunkedCookieHandler> en affectant `mode` à l’attribut de l’élément la valeur `<cookieHandler>` « default » ou « chunked », vous pouvez spécifier la taille de segment que le gestionnaire de cookies utilise pour lire et écrire des cookies en incluant un `<chunkedCookieHandler>` élément enfant et en définissant son `chunkSize` attribut. Si l' `<chunkedCookieHandler>` élément n’est pas présent, la taille de segment par défaut de 2000 octets est utilisée. Cet élément ne peut pas être spécifié lorsque l' `mode` attribut a la valeur « Custom ».  
  
 L' `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant configure un gestionnaire de cookies mémorisé en bloc qui écrit des cookies dans des segments de 3000 octets.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
