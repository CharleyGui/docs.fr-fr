---
title: <socket>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: b8df32745007b2a145d35b8cfcc4cbd2bd17eb33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201731"
---
# <a name="socket-element-network-settings"></a>\<socket>, élément (paramètres réseau)

Spécifie si les opérations de socket utilisent des ports de terminaison.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Accept. La valeur par défaut est `false`.|  
|`alwaysUseCompletionPortsForConnect`|Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Connect. La valeur par défaut est `false`.|  
|`ipProtectionLevel`|Spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un Socket. La valeur par défaut dépend de la version de Windows.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  

 Les `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` attributs et sont utilisés pour spécifier le comportement par défaut en ce qui concerne l’utilisation des ports de terminaison par les classes dans l' <xref:System.Net.Sockets?displayProperty=nameWithType> espace de noms. Les ports de terminaison sont recommandés pour les applications serveur hautes performances.  
  
 La valeur par défaut pour `alwaysUseCompletionPortsForAccept` les `alwaysUseCompletionPortsForConnect` attributs et est **false**.  
  
 Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisé pour récupérer la valeur actuelle de l' `alwaysUseCompletionPortsForAccept` attribut à partir des fichiers de configuration applicables. Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisé pour récupérer la valeur actuelle de l' `alwaysUseCompletionPortsForConnect` attribut à partir des fichiers de configuration applicables.  
  
 L' `ipProtectionLevel` attribut spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un Socket. La <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriété permet la configuration d’une restriction pour un socket IPv6 vers une étendue spécifiée, telle que les adresses avec le même préfixe de lien local ou de site local. Cette option permet aux applications de placer des restrictions d’accès sur les sockets IPv6. Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes. Cette option élargit ou limite la portée d’un socket d’écoute, en permettant l’accès illimité des utilisateurs publics et privés, le cas échéant, ou en restreignant uniquement l’accès au même site, selon les besoins.  
  
 Ce `ipProtectionLevel` paramètre d’attribut affecte uniquement le trafic entrant initial :  
  
- Un serveur TCP qui écoute les connexions entrantes sur un Socket.  
  
- Application UDP recevant un paquet sur un Socket.  
  
 Ce paramètre de configuration n’affecte pas les connexions TCP déjà établies (le trafic n’est pas restreint dans les deux sens) et n’affecte pas une application qui envoie des paquets UDP.  
  
 Les valeurs possibles pour le `ipProtectionLevel` paramètre d’attribut correspondent aux niveaux de protection définis spécifiés dans l' <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> énumération comme suit :  
  
|**Valeur d'attribut**|**Description**|  
|-|-|  
|EdgeRestricted|Le niveau de protection IP est limité à un périmètre donné. Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet. Ce paramètre n'autorise pas la traversée du traducteur d'adresses réseau (NAT) à l'aide de l'implémentation de Windows Teredo. Ces applications peuvent contourner les pare-feux IPv4 ; elles doivent donc être renforcées contre les attaques Internet dirigées sur le port ouvert. Sous Windows Server 2003 et Windows XP, la valeur par défaut pour le niveau de protection IP sur un socket est Périmètre limité.|  
|Restreint|Le niveau de protection IP est limité. Cette valeur peut être utilisée par les applications intranet qui n'implémentent pas de scénarios Internet. Ces applications ne sont généralement pas testées ou renforcées contre les attaques Internet. Ce paramètre limitera uniquement le trafic reçu aux liens locaux.|  
|Non restreint|Le niveau de protection IP est illimité. Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet, notamment les applications qui tirent parti des fonctions de traversée NAT IPv6 intégrées à Windows (Teredo, par exemple). Ces applications peuvent contourner les pare-feux IPv4 ; elles doivent donc être renforcées contre les attaques Internet dirigées sur le port ouvert. Sous Windows Server 2008 R2 et Windows Vista, la valeur par défaut pour le niveau de protection IP sur un socket est illimitée.|  
|Non spécifié|Le niveau de protection IP n'est pas spécifié. Sous Windows 7 et Windows Server 2008 R2, la valeur par défaut pour le niveau de protection IP sur un socket n'est pas spécifiée.|  
  
 La valeur par défaut de l' `ipProtectionLevel` attribut n’est pas **spécifiée**.  
  
 La <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriété peut être utilisée pour récupérer la valeur actuelle de l' `ipProtectionLevel` attribut à partir des fichiers de configuration applicables.  
  
## <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment spécifier que les ports de terminaison doivent être utilisés et que la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> doit être illimitée.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
