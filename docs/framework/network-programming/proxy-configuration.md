---
title: Configuration du proxy
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047358"
---
# <a name="proxy-configuration"></a>Configuration du proxy
Un serveur proxy gère les demandes du client pour les ressources. Un proxy peut retourner une ressource demandée à partir de son cache ou transférer la demande au serveur sur lequel réside la ressource. Les proxies peuvent améliorer les performances réseau en réduisant le nombre de demandes envoyées aux serveurs distants. Les proxies peuvent également être utilisés pour restreindre l'accès aux ressources.  
  
## <a name="adaptive-proxies"></a>Proxies adaptatifs  
 Dans le .NET Framework, les proxies sont fournis sous deux formes : adaptatifs et statiques. Les proxies adaptatifs ajustent leurs paramètres lorsque la configuration du réseau change. Par exemple, si l'utilisateur d'un ordinateur portable démarre une connexion réseau d'accès à distance, un proxy adaptatif identifie cette modification, détecte et exécute son nouveau script de configuration, et ajuste ses paramètres de façon appropriée.  
  
 Les proxys adaptatifs sont configurés par un script de configuration (voir [Détection automatique de proxy](automatic-proxy-detection.md)). Le script génère un ensemble de protocoles d'application et un proxy pour chaque protocole.  
  
 Les modifications apportées à l'environnement réseau peuvent nécessiter que le système utilise un nouvel ensemble de proxies. En cas de défaillance d'une connexion réseau ou d'initialisation d'une nouvelle connexion réseau, le système doit détecter la source appropriée du script de configuration dans le nouvel environnement et exécuter le nouveau script.  
  
 Vous pouvez `usesystemdefault` utiliser l’attribut de l’élément [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) dans votre fichier de configuration. L’attribut `usesystemdefault` détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus à partir des paramètres de proxy Internet Explorer de l’utilisateur. S’il a la valeur `true`, les paramètres de proxy statiques Internet Explorer sont utilisés. S’il a la valeur `false` ou s’il n’est pas défini, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer. En outre, cet attribut doit avoir la valeur `false` ou ne pas être défini pour que les proxys adaptatifs soient activés.  
  
 L'exemple suivant illustre une configuration de proxy adaptatif classique.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Proxies statiques  
 Les proxies statiques sont généralement configurés explicitement par une application, ou lorsqu'un fichier de configuration est appelé par une application ou le système. Les proxies statiques sont utiles dans les réseaux dans lesquels la topologie change rarement, par exemple dans le cas d'un ordinateur de bureau connecté à un réseau d'entreprise.  
  
 Plusieurs options déterminent le fonctionnement d'un proxy statique. Spécifiez les informations suivantes :  
  
- l'adresse du proxy ;  
  
- si le proxy doit être ignoré pour les adresses locales ;  
  
- si le proxy doit être ignoré pour un ensemble d'adresses donné.  
  
 Le tableau suivant présente les options de configuration d'un proxy statique.  
  
|Attribut, propriété ou paramètre de fichier de configuration|Description|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` ou <xref:System.Net.WebProxy.Address>|L'adresse du proxy à utiliser.|  
|`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal>|Détermine si le proxy est ignoré pour les adresses locales.|  
|`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList>|Décrit, avec des expressions régulières, un ensemble d'adresses qui ignorent le proxy.|  
|`usesystemdefault`|Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur. Si cet attribut à la valeur `true`, les paramètres de proxy statiques Internet Explorer sont utilisés. Dans .NET Framework 2.0, quand cet attribut à la valeur `true`, les paramètres de proxy Internet Explorer ne sont pas remplacés par d’autres paramètres de proxy figurant dans le fichier de configuration. Sur .NET Framework 1.1, les paramètres de proxy Internet Explorer peuvent être substituées par d'autres paramètres de proxy figurant dans le fichier de configuration.<br /><br /> Si cet attribut à la valeur `false` ou s’il n’est pas défini, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer. En outre, cet attribut doit avoir la valeur `false` ou ne pas être défini pour que les proxys adaptatifs soient activés.|  
  
 L'exemple suivant illustre une configuration de proxy statique classique.  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Détection automatique de proxy](automatic-proxy-detection.md)
