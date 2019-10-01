---
title: <applicationPool>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: c88f4e5407e550047eaf0f5c8d0d2924da611e93
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699224"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool >, élément (paramètres Web)
Spécifie les paramètres de configuration utilisés par ASP.NET pour gérer le comportement au niveau du processus quand une application ASP.NET s’exécute en mode intégré sur IIS 7,0 ou une version ultérieure.  
  
> [!IMPORTANT]
> Cet élément et la fonctionnalité qu’il prend en charge fonctionnent uniquement si votre application ASP.NET est hébergée sur IIS 7,0 ou versions ultérieures.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4System. Web >** ](system-web-element-web-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<applicationPool >**  
  
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
|`maxConcurrentRequestsPerCPU`|Spécifie le nombre de requêtes simultanées que ASP.NET autorise par UC.|  
|`maxConcurrentThreadsPerCPU`|Spécifie le nombre de threads simultanés pouvant être en cours d’exécution pour un pool d’applications pour chaque UC. Cela fournit une autre façon de contrôler l’accès concurrentiel ASP.NET, car vous pouvez limiter le nombre de threads managés qui peuvent être utilisés par UC pour traiter les demandes. Par défaut, ce paramètre a la valeur 0, ce qui signifie que ASP.NET ne limite pas le nombre de threads qui peuvent être créés par UC, bien que le pool de threads CLR limite également le nombre de threads qui peuvent être créés.|  
|`requestQueueLimit`|Spécifie le nombre maximal de demandes qui peuvent être mises en file d’attente pour ASP.NET dans un même processus. Quand plusieurs applications ASP.NET s’exécutent dans un seul pool d’applications, l’ensemble cumulé des demandes adressées à une application dans le pool d’applications est soumis à ce paramètre.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Contient des informations sur la façon dont ASP.NET interagit avec une application hôte.|  
  
## <a name="remarks"></a>Notes  

Lorsque vous exécutez IIS 7,0 ou une version ultérieure en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les demandes de threads et de files d’attente lorsque l’application est hébergée dans un pool d’applications IIS. Si vous exécutez IIS 6 ou IIS 7,0 en mode classique ou en mode ISAPI, ces paramètres sont ignorés.  
  
Les paramètres `applicationPool` s’appliquent à tous les pools d’applications qui s’exécutent sur une version particulière du .NET Framework. Les paramètres sont contenus dans un fichier Aspnet. config. Il existe une version de ce fichier pour les versions 2,0 et 4,0 du .NET Framework. (Les versions 3,0 et 3,5 du .NET Framework partagent le fichier Aspnet. config avec la version 2,0.)  
  
> [!IMPORTANT]
> Si vous exécutez IIS 7,0 sur [!INCLUDE[win7](../../../../../includes/win7-md.md)], vous pouvez configurer un fichier Aspnet. config distinct pour chaque pool d’applications. Cela vous permet de personnaliser les performances des threads pour chaque pool d’applications.  
  
Pour le paramètre `maxConcurrentRequestsPerCPU`, le paramètre par défaut « 5000 » dans le .NET Framework 4 désactive efficacement la limitation des demandes qui est contrôlée par ASP.NET, sauf si vous avez au moins 5000 demandes par UC. Le paramètre par défaut dépend plutôt du pool de threads CLR pour gérer automatiquement l’accès concurrentiel par UC. Les applications qui utilisent de manière intensive le traitement des demandes asynchrones, ou qui ont de nombreuses requêtes à long terme bloquées sur les e/s réseau, tireront parti de l’augmentation de la limite par défaut dans le .NET Framework 4. La définition de `maxConcurrentRequestsPerCPU` à zéro désactive l’utilisation de threads managés pour le traitement des demandes ASP.NET. Quand une application s’exécute dans un pool d’applications IIS, les demandes sont conservées sur le thread d’e/s IIS et par conséquent, la concurrence est limitée par les paramètres de thread IIS.  
  
Le paramètre `requestQueueLimit` fonctionne de la même façon que l’attribut `requestQueueLimit` de l’élément [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) , qui est défini dans les fichiers Web. config pour les applications ASP.net. Toutefois, le paramètre `requestQueueLimit` dans un fichier Aspnet. config remplace le paramètre `requestQueueLimit` dans un fichier Web. config. En d’autres termes, si les deux attributs sont définis (par défaut, cela est vrai), le paramètre `requestQueueLimit` dans le fichier Aspnet. config est prioritaire.  
  
## <a name="example"></a>Exemple  

L’exemple suivant montre comment configurer le comportement à l’ensemble du processus ASP.NET dans le fichier Aspnet. config dans les circonstances suivantes :  
  
- L’application est hébergée dans un pool d’applications IIS 7,0.  
  
- IIS 7,0 s’exécute en mode intégré.  
  
- L’application utilise le .NET Framework 3,5 SP1 ou une version ultérieure.  
  
Les valeurs de l’exemple sont les valeurs par défaut.  
  
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

- [\<system.web>, élément (paramètres web)](system-web-element-web-settings.md)
