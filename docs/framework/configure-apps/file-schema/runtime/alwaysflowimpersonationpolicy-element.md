---
title: Élément <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 9316f026a807b6ad36014157061f67bdbd7d3d18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149437"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>Élément \<alwaysFlowImpersonationPolicy>

Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si l’identité Windows circule entre des points asynchrones.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|L’identité Windows ne passe pas entre des points asynchrones, sauf si l’emprunt d’identité est effectué via des méthodes managées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> . Il s’agit de la valeur par défaut.|  
|`true`|L’identité Windows est toujours transgérée entre les points asynchrones, indépendamment de la façon dont l’emprunt d’identité a été effectué.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  

 Dans les versions 1,0 et 1,1 de .NET Framework, l’identité Windows ne passe pas entre les points asynchrones. Dans la .NET Framework version 2,0, il existe un <xref:System.Threading.ExecutionContext> objet qui contient des informations sur le thread en cours d’exécution et le transmet entre des points asynchrones au sein d’un domaine d’application. Le <xref:System.Security.Principal.WindowsIdentity> flux est également inclus dans les informations qui circulent entre les points asynchrones, à condition que l’emprunt d’identité ait été obtenu à l’aide de méthodes managées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> et non par d’autres moyens tels que l’appel de code non managé aux méthodes natives. Cet élément est utilisé pour spécifier que l’identité Windows circule entre des points asynchrones, quelle que soit la façon dont l’emprunt d’identité a été atteint.  
  
 Vous pouvez modifier ce comportement par défaut de deux manières :  
  
1. En code managé pour chaque thread.  
  
     Vous pouvez supprimer le workflow pour chaque thread en modifiant les <xref:System.Threading.ExecutionContext> paramètres et à <xref:System.Security.SecurityContext> l’aide de la <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> méthode, ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .  
  
2. Dans l’appel à l’interface d’hébergement non managée pour charger le common language runtime (CLR).  
  
     Si une interface d’hébergement non managée (au lieu d’un simple exécutable managé) est utilisée pour charger le CLR, vous pouvez spécifier un indicateur spécial dans l’appel à la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Pour activer le mode de compatibilité pour l’ensemble du processus, définissez le `flags` paramètre de la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) sur `STARTUP_ALWAYSFLOW_IMPERSONATION` .  
  
## <a name="configuration-file"></a>Fichier de configuration  

 Dans une application .NET Framework, cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.  
  
 Pour une application ASP.NET, le workflow d’emprunt d’identité peut être configuré dans le fichier aspnet.config qui se trouve dans le \<Windows Folder> répertoire \Microsoft.NET\Framework\vx.x.xxxx  
  
 Par défaut, ASP.NET désactive le workflow d’emprunt d’identité dans le fichier aspnet.config à l’aide des paramètres de configuration suivants :  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Dans ASP.NET, si vous souhaitez autoriser le workflow d’emprunt d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment spécifier que l’identité Windows passe d’un point asynchrone à un autre, même lorsque l’emprunt d’identité est réalisé à l’aide d’autres moyens que les méthodes managées.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
- [\<legacyImpersonationPolicy> Appartient](legacyimpersonationpolicy-element.md)
