---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 853dc9817d080e59ac7a792576eda862bd0b1f1d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252023"
---
# \<cookieHandler>
Configure le <xref:System.IdentityModel.Services.CookieHandler> que le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) utilise pour lire et écrire des cookies.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Spécifie le nom de base pour les cookies écrits. La valeur par défaut est « FedAuth ».|  
|path|Spécifie la valeur de chemin d’accès pour tous les cookies écrits. La valeur par défaut est « HttpRuntime. AppDomainAppVirtualPath ».|  
|mode|L’une des <xref:System.IdentityModel.Services.CookieHandlerMode> valeurs qui spécifie le type de gestionnaire de cookies utilisé par le Sam. Les valeurs suivantes peuvent être utilisées :<br /><br /> -« Default », identique à « chunked ».<br />-« Segmentée » : utilise une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Ce gestionnaire de cookies garantit que les cookies individuels ne dépassent pas une taille maximale définie. Pour ce faire, il « segmente » potentiellement un cookie logique en un certain nombre de cookies sur le réseau.<br />-« Custom » : utilise une instance d’une classe personnalisée dérivée de <xref:System.IdentityModel.Services.CookieHandler> . La classe dérivée est référencée par l' `<customCookieHandler>` élément enfant.<br /><br /> La valeur par défaut est « default ».|  
|persistentSessionLifetime|Spécifie la durée de vie des sessions persistantes. Si la valeur est zéro, les sessions transitoires sont toujours utilisées. La valeur par défaut est « 0:0:0 », qui spécifie une session temporaire. La valeur maximale est « 365:0:0 », qui spécifie une session de 365 jours. La valeur doit être spécifiée selon la restriction suivante : `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` , où la valeur la plus à gauche spécifie les jours, la valeur centrale (si elle est présente) spécifie les heures et la valeur la plus à droite (le cas échéant) spécifie les minutes.|  
|requireSsl|Spécifie si l’indicateur « Secure » est émis pour tous les cookies écrits. Si cette valeur est définie, les cookies de session de connexion sont uniquement disponibles via HTTPs. La valeur par défaut est "true".|  
|hideFromScript|Contrôle si l’indicateur « HttpOnly » est émis pour tous les cookies écrits. Certains navigateurs Web honorent cet indicateur en empêchant le script côté client d’accéder à la valeur du cookie. La valeur par défaut est "true".|  
|domaine|Valeur de domaine pour les cookies écrits. La valeur par défaut est "".|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Cet élément ne peut être présent que si l' `mode` attribut de l' `<cookieHandler>` élément est « default » ou « chunked ».|  
|[\<customCookieHandler>](customcookiehandler.md)|Définit le type de gestionnaire de cookies personnalisé. Cet élément doit être présent si l' `mode` attribut de l' `<cookieHandler>` élément est « Custom ». Elle ne peut pas être présente pour d’autres valeurs de l' `mode` attribut. Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).|  
  
## <a name="remarks"></a>Remarques  
 Le <xref:System.IdentityModel.Services.CookieHandler> est responsable de la lecture et de l’écriture des cookies bruts au niveau du protocole http. Vous pouvez configurer un <xref:System.IdentityModel.Services.ChunkedCookieHandler> ou un gestionnaire de cookies personnalisé dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 Pour configurer un gestionnaire de cookies mémorisé en bloc, affectez à l’attribut mode la valeur « segmentée » ou « par défaut ». La taille de segment par défaut est de 2000 octets, mais vous pouvez éventuellement spécifier une taille de segment différente en incluant un `<chunkedCookieHandler>` élément enfant.  
  
 Pour configurer un gestionnaire de cookies personnalisé, affectez à l’attribut mode la valeur « Custom ». Vous devez également spécifier un `<customCookieHandler>` élément enfant qui fait référence au type de votre gestionnaire personnalisé.  
  
 L' `<cookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.CookieHandlerElement> classe. Le gestionnaire de cookies qui a été spécifié dans la configuration est disponible à partir de la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> propriété de l' <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet défini sur la <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre un `<cookieHandler>` élément. Dans cet exemple, étant donné que l' `mode` attribut n’est pas spécifié, le gestionnaire de cookies par défaut sera utilisé par le Sam. Il s’agit d’une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Étant donné que l' `<chunkedCookieHandler>` élément enfant n’est pas spécifié, la taille de segment par défaut sera utilisée. HTTPs n’est pas nécessaire, car l' `requireSsl` attribut est défini `false` .  
  
> [!WARNING]
> Dans cet exemple, le protocole HTTPs n’est pas requis pour écrire des cookies de session. Cela est dû au fait que l' `requireSsl` attribut sur l' `<cookieHandler>` élément a la valeur `false` . Ce paramètre n’est pas recommandé pour la plupart des environnements de production, car il peut présenter un risque pour la sécurité.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
