---
title: <applicationPool>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152852"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool >, élément (paramètres Web)
Spécifie les paramètres de configuration qui sont utilisés par ASP.NET pour gérer le comportement à l’échelle du processus lorsqu’une application ASP.NET est en mode intégré sur IIS 7.0 ou une version ultérieure.  
  
> [!IMPORTANT]
> Cet élément et la fonctionnalité qu’il prend en charge ne fonctionnent que si votre application ASP.NET est hébergée sur les versions IIS 7.0 ou ultérieures.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|Précise le nombre de demandes simultanées ASP.NET permet par processeur.|  
|`maxConcurrentThreadsPerCPU`|Précise le nombre de threads simultanés qui peuvent être en cours d’exécution pour un pool d’applications pour chaque processeur. Cela fournit un autre moyen de contrôler ASP.NET concurrence, car vous pouvez limiter le nombre de threads gérés qui peuvent être utilisés par processeur pour servir les demandes. Par défaut, ce paramètre est de 0, ce qui signifie que ASP.NET ne limite pas le nombre de threads qui peuvent être créés par processeur, bien que le pool de thread CLR limite également le nombre de threads qui peuvent être créés.|  
|`requestQueueLimit`|Spécifie le nombre maximum de demandes qui peuvent être en file d’attente pour ASP.NET en un seul processus. Lorsque deux demandes de ASP.NET s’exécutent dans un seul pool d’applications, l’ensemble cumulatif de demandes adressées à toute demande dans le pool de demandes est soumis à ce paramètre.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Contient des informations sur la façon dont ASP.NET interagit avec une application hôte.|  
  
## <a name="remarks"></a>Notes   

Lorsque vous exécutez IIS 7.0 ou une version ultérieure en mode intégré, cette combinaison d’éléments vous permet de configurer la façon dont ASP.NET gère les demandes de threads et de files d’attente lorsque l’application est hébergée dans un pool d’applications IIS. Si vous exécutez IIS 6 ou si vous exécutez IIS 7.0 en mode Classique ou en mode ISAPI, ces paramètres sont ignorés.  
  
Les `applicationPool` paramètres s’appliquent à tous les pools d’applications qui s’exécutent sur une version particulière du cadre .NET. Les paramètres sont contenus dans un fichier aspnet.config. Il existe une version de ce fichier pour les versions 2.0 et 4.0 du cadre .NET. (Versions 3.0 et 3.5 du cadre .NET part du fichier aspnet.config avec la version 2.0.)  
  
> [!IMPORTANT]
> Si vous exécutez IIS 7.0 sur Windows 7, vous pouvez configurer un fichier aspnet.config séparé pour chaque pool d’applications. Cela vous permet d’adapter les performances des threads pour chaque pool d’applications.  
  
Pour `maxConcurrentRequestsPerCPU` le paramètre, le paramètre par défaut de "5000" dans le cadre .NET 4 éteint effectivement la limitation de demande qui est contrôlée par ASP.NET, sauf si vous avez réellement 5000 demandes ou plus par processeur. Le paramètre par défaut dépend plutôt du thread-pool CLR pour gérer automatiquement la concurrence par processeur. Les applications qui font un usage intensif du traitement des demandes asynchrones, ou qui ont de nombreuses demandes de longue durée bloquées sur le réseau I / O, bénéficieront de la limite accrue par défaut dans le cadre .NET 4. Le `maxConcurrentRequestsPerCPU` réglage à zéro éteint l’utilisation de threads gérés pour le traitement des demandes ASP.NET. Lorsqu’une application s’exécute dans un pool d’applications IIS, demande de rester sur le thread IIS I/O et donc la concurrence est étranglée par les paramètres de thread IIS.  
  
Le `requestQueueLimit` paramètre fonctionne de `requestQueueLimit` la même manière que l’attribut de l’élément [processModel,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) qui est défini dans les fichiers Web.config pour ASP.NET applications. Cependant, `requestQueueLimit` le paramètre dans un fichier aspnet.config remplace le `requestQueueLimit` paramètre dans un fichier Web.config. En d’autres termes, si les deux attributs sont `requestQueueLimit` définis (par défaut, c’est vrai), le paramètre dans le fichier aspnet.config prime.  
  
## <a name="example"></a> Exemple  

L’exemple suivant montre comment configurer ASP.NET comportement à l’échelle du processus dans le fichier aspnet.config dans les circonstances suivantes :  
  
- L’application est hébergée dans un pool d’applications IIS 7.0.  
  
- L’IIS 7.0 fonctionne en mode intégré.  
  
- L’application utilise le .NET Framework 3.5 SP1 ou une version ultérieure.  
  
Les valeurs dans l’exemple sont les valeurs par défaut.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms||  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi

- [\<system.web> Element (Paramètres Web)](system-web-element-web-settings.md)
