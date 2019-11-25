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
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089088"
---
# <a name="socket-element-network-settings"></a>Élément \<> Socket (paramètres réseau)
Spécifie si les opérations de socket utilisent des ports de terminaison.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >

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
|`ipProtectionLevel`|Spécifie le <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> par défaut à utiliser pour un Socket. La valeur par défaut dépend de la version de Windows.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Paramètres](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  
 Les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` sont utilisés pour spécifier le comportement par défaut en ce qui concerne l’utilisation des ports de terminaison par les classes de l’espace de noms <xref:System.Net.Sockets?displayProperty=nameWithType>. Les ports de terminaison sont recommandés pour les applications serveur hautes performances.  
  
 La valeur par défaut pour les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` est **false**.  
  
 Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisé pour récupérer la valeur actuelle de l’attribut `alwaysUseCompletionPortsForAccept` à partir des fichiers de configuration applicables. Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisé pour récupérer la valeur actuelle de l’attribut `alwaysUseCompletionPortsForConnect` à partir des fichiers de configuration applicables.  
  
 L’attribut `ipProtectionLevel` spécifie la <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> par défaut à utiliser pour un Socket. La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> permet la configuration d’une restriction pour un socket IPv6 à une étendue spécifiée, telle que les adresses avec le même préfixe de lien local ou de site local. Cette option permet aux applications de placer des restrictions d’accès sur les sockets IPv6. Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes. Cette option élargit ou limite la portée d’un socket d’écoute, en permettant l’accès illimité des utilisateurs publics et privés, le cas échéant, ou en restreignant uniquement l’accès au même site, selon les besoins.  
  
 Ce paramètre d’attribut `ipProtectionLevel` affecte uniquement le trafic entrant initial :  
  
- Un serveur TCP qui écoute les connexions entrantes sur un Socket.  
  
- Application UDP recevant un paquet sur un Socket.  
  
 Ce paramètre de configuration n’affecte pas les connexions TCP déjà établies (le trafic n’est pas restreint dans les deux sens) et n’affecte pas une application qui envoie des paquets UDP.  
  
 Les valeurs possibles pour le paramètre d’attribut `ipProtectionLevel` correspondent aux niveaux de protection définis dans l’énumération <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> comme suit :  
  
|**Valeur de l’attribut**|**Description**|  
|-|-|  
|EdgeRestricted|Le niveau de protection IP est limité à l’arête. Cette valeur est utilisée par les applications conçues pour fonctionner sur Internet. Ce paramètre n’autorise pas la traversée de traduction d’adresses réseau (NAT) à l’aide de l’implémentation Windows Teredo. Ces applications peuvent contourner les pare-feu IPv4, de sorte que les applications doivent être renforcées contre les attaques Internet dirigées vers le port ouvert. Sur Windows Server 2003 et Windows XP, la valeur par défaut du niveau de protection IP sur un socket est limitée à la périphérie.|  
|Sensible|Le niveau de protection IP est limité. Cette valeur est utilisée par les applications intranet qui n’implémentent pas de scénarios Internet. Ces applications ne sont généralement pas testées ou renforcées contre les attaques de type Internet. Ce paramètre limite le trafic reçu à la liaison locale uniquement.|  
|Non restreint|Le niveau de protection IP est illimité. Cette valeur est utilisée par les applications conçues pour fonctionner sur Internet, y compris les applications tirant parti des fonctionnalités de traversée NAT IPv6 intégrées à Windows (Teredo, par exemple). Ces applications peuvent contourner les pare-feu IPv4, de sorte que les applications doivent être renforcées contre les attaques Internet dirigées vers le port ouvert. Sur Windows Server 2008 R2 et Windows Vista, la valeur par défaut du niveau de protection IP sur un socket est illimitée.|  
|Non spécifié|Le niveau de protection IP n’est pas spécifié. Sur Windows 7 et Windows Server 2008 R2, la valeur par défaut du niveau de protection IP sur un socket n’est pas spécifiée.|  
  
 La valeur par défaut de l’attribut `ipProtectionLevel` n’est pas **spécifiée**.  
  
 La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut `ipProtectionLevel` à partir des fichiers de configuration applicables.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que les ports de terminaison doivent être utilisés et que la <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> par défaut doit être illimitée.  
  
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
