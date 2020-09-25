---
title: Élément <legacyImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: ca10c809ddf319817aaa074ba5fc3415abf6387d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192514"
---
# <a name="legacyimpersonationpolicy-element"></a>Élément \<legacyImpersonationPolicy>

Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie que le <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones, quels que soient les <xref:System.Threading.ExecutionContext> paramètres de flow sur le thread actuel.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> passe entre des points asynchrones en fonction des <xref:System.Threading.ExecutionContext> paramètres de flux du thread actuel. Il s’agit de la valeur par défaut.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones, quels que soient les <xref:System.Threading.ExecutionContext> paramètres de flow sur le thread actuel.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  

 Dans les versions de .NET Framework 1,0 et 1,1, le <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis sur les points asynchrones définis par l’utilisateur. À partir de la version .NET Framework 2,0, il existe un <xref:System.Threading.ExecutionContext> objet qui contient des informations sur le thread en cours d’exécution et qui est transmis entre des points asynchrones au sein d’un domaine d’application. Le <xref:System.Security.Principal.WindowsIdentity> est inclus dans ce contexte d’exécution et est, par conséquent, transmis entre les points asynchrones, ce qui signifie que si un contexte d’emprunt d’identité existe, il est également transmis.  
  
 À partir de la .NET Framework 2,0, vous pouvez utiliser l' `<legacyImpersonationPolicy>` élément pour spécifier que  <xref:System.Security.Principal.WindowsIdentity> ne passe pas entre des points asynchrones.  
  
> [!NOTE]
> Le common language runtime (CLR) tient compte des opérations d’emprunt d’identité effectuées à l’aide du code managé uniquement, et non de l’emprunt d’identité effectué en dehors du code managé, par exemple par le biais de l’appel de code non managé au code non managé ou via des appels directs à des fonctions Win32. Seuls <xref:System.Security.Principal.WindowsIdentity> les objets managés peuvent circuler entre des points asynchrones, sauf si l' `alwaysFlowImpersonationPolicy` élément a la valeur true ( `<alwaysFlowImpersonationPolicy enabled="true"/>` ). L’affectation `alwaysFlowImpersonationPolicy` de la valeur true à l’élément spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité. Pour plus d’informations sur le passage de l’emprunt d’identité non managé entre des points asynchrones, consultez [ \<alwaysFlowImpersonationPolicy> élément](alwaysflowimpersonationpolicy-element.md).  
  
 Vous pouvez modifier ce comportement par défaut de deux manières :  
  
1. En code managé pour chaque thread.  
  
     Vous pouvez supprimer le workflow pour chaque thread en modifiant les <xref:System.Threading.ExecutionContext> paramètres et à <xref:System.Security.SecurityContext> l’aide de la <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> méthode, ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .  
  
2. Dans l’appel à l’interface d’hébergement non managée pour charger le common language runtime (CLR).  
  
     Si une interface d’hébergement non managée (au lieu d’un simple exécutable managé) est utilisée pour charger le CLR, vous pouvez spécifier un indicateur spécial dans l’appel à la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Pour activer le mode de compatibilité pour l’ensemble du processus, définissez le `flags` paramètre de la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) sur STARTUP_LEGACY_IMPERSONATION.  
  
 Pour plus d’informations, consultez l' [ \<alwaysFlowImpersonationPolicy> élément](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Fichier de configuration  

 Dans une application .NET Framework, cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.  
  
 Pour une application ASP.NET, le workflow d’emprunt d’identité peut être configuré dans le fichier aspnet.config qui se trouve dans le \<Windows Folder> répertoire \Microsoft.NET\Framework\vx.x.xxxx  
  
 Par défaut, ASP.NET désactive le workflow d’emprunt d’identité dans le fichier aspnet.config à l’aide des paramètres de configuration suivants :  
  
``` xml
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

 L’exemple suivant montre comment spécifier le comportement hérité qui ne passe pas l’identité Windows entre des points asynchrones.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
- [\<alwaysFlowImpersonationPolicy> Appartient](alwaysflowimpersonationpolicy-element.md)
