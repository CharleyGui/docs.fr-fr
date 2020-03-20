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
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154481"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Element
Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
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
|`enabled`|Attribut requis.<br /><br /> Indique si l’identité Windows circule à travers des points asynchrones.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|L’identité Windows ne coule pas à travers les points asynchrones, sauf si l’usurpation d’identité est effectuée par des méthodes gérées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Il s’agit de la valeur par défaut.|  
|`true`|L’identité Windows circule toujours à travers des points asynchrones, indépendamment de la façon dont l’usurpation d’identité a été effectuée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Dans les versions .NET Framework 1.0 et 1.1, l’identité Windows ne circule pas à travers les points asynchrones. Dans la version cadre .NET 2.0, il existe un objet qui contient des <xref:System.Threading.ExecutionContext> informations sur le thread actuellement exécutant, et le circule à travers des points asynchrones dans un domaine d’application. L’imitation <xref:System.Security.Principal.WindowsIdentity> s’écoule également dans le cadre de l’information qui circule à travers <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> les points asynchrones, à condition que l’usurpation d’identité a été réalisée en utilisant des méthodes gérées telles que et non par d’autres moyens tels que la plate-forme invoquer des méthodes indigènes. Cet élément est utilisé pour spécifier que l’identité Windows ne flux à travers les points asynchrones, indépendamment de la façon dont l’usurpation d’identité a été réalisée.  
  
 Vous pouvez modifier ce comportement par défaut de deux autres façons :  
  
1. Dans le code géré sur une base par thread.  
  
     Vous pouvez supprimer le flux par fil en <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> modifiant le <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>les <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> paramètres en utilisant le , , ou la méthode.  
  
2. Dans l’appel à l’interface d’hébergement non gérée pour charger l’heure courante de course de langue (CLR).  
  
     Si une interface d’hébergement non gérée (au lieu d’une simple gestion exécutable) est utilisée pour charger le CLR, vous pouvez spécifier un drapeau spécial dans l’appel à la fonction [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Pour activer le mode de compatibilité `flags` pour l’ensemble du processus, `STARTUP_ALWAYSFLOW_IMPERSONATION`définissez le paramètre de la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) à .  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Dans une application cadre .NET, cet élément ne peut être utilisé que dans le fichier de configuration d’application.  
  
 Pour une application ASP.NET, le flux d’usurpation d’identité peut être configuré dans le fichier aspnet.config trouvé dans le \<dossier Windows>-Microsoft.NET-Framework-vx.x.xxxx annuaire.  
  
 ASP.NET par défaut désactive le flux d’usurpation d’identité dans le fichier aspnet.config en utilisant les paramètres de configuration suivants :  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Dans ASP.NET, si vous souhaitez autoriser le flux d’usurpation d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment spécifier que l’identité Windows circule à travers des points asynchrones, même lorsque l’usurpation d’identité est réalisée par d’autres moyens que des méthodes gérées.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- [\<héritageImpersonationPolicy> Element](legacyimpersonationpolicy-element.md)
