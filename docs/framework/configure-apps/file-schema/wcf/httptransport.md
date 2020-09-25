---
title: <httpTransport>
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 14d774ba7711c9ce60fb1db5a2b050c310550ec1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203889"
---
# \<httpTransport>

Spécifie un transport HTTP pour la transmission des messages SOAP d’une liaison personnalisée.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpTransport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpTransport allowCookies="Boolean"
               authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
               bypassProxyOnLocal="Boolean"
               hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
               keepAliveEnabled="Boolean"
               maxBufferSize="Integer"
               proxyAddress="Uri"
               proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
               realm="String"
               transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
               unsafeConnectionNtlmAuthentication="Boolean"
               useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|allowCookies|Valeur booléenne qui spécifie si le client accepte les cookies et les propage dans de futures demandes. La valeur par défaut est `false`.<br /><br /> Vous pouvez utiliser cet attribut lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies. De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.|  
|authenticationScheme|Spécifie le protocole utilisé pour authentifier des demandes du client qui sont traitées par un écouteur HTTP. Les valeurs valides sont les suivantes :<br /><br /> -Digest : spécifie l’authentification Digest.<br />-Negotiate : négocie avec le client pour déterminer le schéma d’authentification. Si le client et le serveur prennent tous les deux en charge Kerberos, ce protocole est utilisé ; sinon, NTLM est utilisé.<br />-NTLM : spécifie l’authentification NTLM.<br />-Basic : spécifie l’authentification de base.<br />-Anonymous : spécifie l’authentification anonyme.<br /><br /> La valeur par défaut est Anonymous. Cet attribut est de type <xref:System.Net.AuthenticationSchemes>. Cet attribut ne peut être défini qu'une fois.|  
|bypassProxyOnLocal|Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales. La valeur par défaut est `false`.<br /><br /> Une adresse locale est une adresse sur le réseau local ou l'intranet.<br /><br /> Windows Communication Foundation (WCF) ignore toujours le proxy si l’adresse de service commence par `http://localhost` .<br /><br /> Utilisez le nom d'hôte plutôt que localhost si vous souhaitez que les clients passent par un proxy lorsqu'ils communiquent avec des services sur le même ordinateur.|  
|hostnameComparisonMode|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI. Les valeurs valides sont :<br /><br /> -StrongWildcard : ("+") correspond à tous les noms d’hôtes possibles dans le contexte du schéma, du port et de l’URI relatif spécifiés.<br />-Exact : aucun caractère générique<br />-WeakWildcard : (" \* ") correspond à tous les noms d’hôte possibles dans le contexte du schéma spécifié, du port et des URI relatifs qui n’ont pas été mis en correspondance explicitement ni par le biais du mécanisme à caractères génériques forts.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>. Par défaut, il s’agit de <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>.|  
|KeepAliveEnabled|Valeur booléenne qui spécifie si une connexion persistante doit être établie avec la ressource Internet.|  
|maxBufferSize|Entier positif qui spécifie la taille maximale de la mémoire tampon. La valeur par défaut est 524 288.|  
|proxyAddress|URI qui spécifie l'adresse du proxy HTTP. Si `useSystemWebProxy` est `true`, ce paramètre doit avoir la valeur `null`. Par défaut, il s’agit de `null`.|  
|proxyAuthenticationScheme|Spécifie le protocole utilisé pour l'authentification des demandes du client qui sont traitées par un proxy HTTP. Les valeurs valides sont les suivantes :<br /><br /> -None : aucune authentification n’est effectuée.<br />-Digest : spécifie l’authentification Digest.<br />-Negotiate : négocie avec le client pour déterminer le schéma d’authentification. Si le client et le serveur prennent tous les deux en charge Kerberos, ce protocole est utilisé ; sinon, NTLM est utilisé.<br />-NTLM : spécifie l’authentification NTLM.<br />-Basic : spécifie l’authentification de base.<br />-Anonymous : spécifie l’authentification anonyme.<br /><br /> La valeur par défaut est Anonymous. Cet attribut est de type <xref:System.Net.AuthenticationSchemes>. Notez que <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> n’est pas pris en charge.|  
|realm|Chaîne qui spécifie le domaine à utiliser sur le proxy/serveur. La valeur par défaut est une chaîne vide.<br /><br /> Les serveurs utilisent des domaines pour partitionner des ressources protégées. Chaque partition peut posséder son propre schéma d'authentification et/ou sa base de données d'autorisation. Les domaines sont utilisés uniquement pour les authentifications Digest et de base. Lorsqu'un client est correctement authentifié, l'authentification est valide pour toutes les ressources contenues dans un domaine donné. Pour obtenir une description détaillée des domaines, consultez la RFC 2617 sur le [site Web IETF](https://www.ietf.org).|  
|transferMode|Spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse. Les valeurs valides sont les suivantes :<br /><br /> -Buffered : les messages de demande et de réponse sont mis en mémoire tampon.<br />-Streaming : les messages de demande et de réponse sont diffusés en continu.<br />-StreamedRequest : le message de demande est transmis en continu et le message de réponse est mis en mémoire tampon.<br />-StreamedResponse : le message de demande est mis en mémoire tampon et le message de réponse est transmis en continu.<br /><br /> La valeur par défaut est Buffered. Cet attribut est de type <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Valeur booléenne qui spécifie si le partage de connexion potentiellement dangereux est activé sur le serveur. La valeur par défaut est `false`. S'il est activé, l'authentification NTLM est exécutée une fois sur chaque connexion TCP.|  
|useDefaultWebProxy|Valeur booléenne qui spécifie si les paramètres proxy à l'échelle de l'ordinateur sont utilisés plutôt que ceux spécifiques à l'utilisateur. Par défaut, il s’agit de `true`.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  

 L'élément `httpTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport HTTP. HTTP est le principal transport utilisé à des fins d'interopérabilité. Ce transport est pris en charge par le Windows Communication Foundation (WCF) pour garantir l’interopérabilité avec d’autres piles de services Web non-WCF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.HttpTransportElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transports](../../../wcf/feature-details/transports.md)
- [Choix d'un transport](../../../wcf/feature-details/choosing-a-transport.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
