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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154102"
---
# <a name="legacyimpersonationpolicy-element"></a>\<héritageImpersonationPolicy> Element
Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
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
|`enabled`|Attribut requis.<br /><br /> Précise que le <xref:System.Security.Principal.WindowsIdentity> ne coule pas à travers les points <xref:System.Threading.ExecutionContext> asynchrones, indépendamment des paramètres de flux sur le thread actuel.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>circule à travers les points <xref:System.Threading.ExecutionContext> asynchrones en fonction des paramètres de flux pour le thread actuel. Il s’agit de la valeur par défaut.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>ne coule pas à travers les points <xref:System.Threading.ExecutionContext> asynchrones, indépendamment des paramètres de flux sur le thread actuel.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Dans les versions .NET Framework 1.0 et <xref:System.Security.Principal.WindowsIdentity> 1.1, le ne circule pas à travers les points asynchrones définis par l’utilisateur. En commençant par la version cadre .NET 2.0, il existe un objet qui contient des <xref:System.Threading.ExecutionContext> informations sur le thread actuellement exécutant, et il circule à travers des points asynchrones dans un domaine d’application. Le <xref:System.Security.Principal.WindowsIdentity> est inclus dans ce contexte d’exécution et donc aussi coule à travers les points asynchrones, ce qui signifie que si un contexte d’usurpation d’identité existe, il coulera ainsi.  
  
 En commençant par le cadre .NET 2.0, vous pouvez utiliser l’élément `<legacyImpersonationPolicy>` pour spécifier qui <xref:System.Security.Principal.WindowsIdentity> ne circule pas à travers les points asynchrones.  
  
> [!NOTE]
> L’heure courante de fonctionnement de langue (CLR) est au courant des opérations d’usurpation d’identité effectuées en utilisant seulement le code géré, pas de l’usurpation d’identité effectuée en dehors du code géré, par exemple par le biais de la plate-forme invoquer le code non géré ou par des appels directs vers des fonctions Win32. Seuls <xref:System.Security.Principal.WindowsIdentity> les objets gérés peuvent circuler à travers `alwaysFlowImpersonationPolicy` des points asynchrones, à moins que l’élément n’ait été mis en place pour vrai (`<alwaysFlowImpersonationPolicy enabled="true"/>`). La `alwaysFlowImpersonationPolicy` définition de l’élément à vrai spécifie que l’identité Windows circule toujours à travers des points asynchrones, indépendamment de la façon dont l’usurpation d’identité a été effectuée. Pour plus d’informations sur l’usurpation d’identité non mentée à travers les points asynchrones, voir [ \<toujoursFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
 Vous pouvez modifier ce comportement par défaut de deux autres façons :  
  
1. Dans le code géré sur une base par thread.  
  
     Vous pouvez supprimer le flux par fil en <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> modifiant les <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>paramètres <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> et les paramètres en utilisant la , ou la méthode.  
  
2. Dans l’appel à l’interface d’hébergement non gérée pour charger l’heure courante de course de langue (CLR).  
  
     Si une interface d’hébergement non gérée (au lieu d’une simple gestion exécutable) est utilisée pour charger le CLR, vous pouvez spécifier un drapeau spécial dans l’appel à la fonction [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Pour activer le mode de compatibilité `flags` pour l’ensemble du processus, définissez le paramètre de [la fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) pour STARTUP_LEGACY_IMPERSONATION.  
  
 Pour plus d’informations, voir le [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Dans une application cadre .NET, cet élément ne peut être utilisé que dans le fichier de configuration d’application.  
  
 Pour une application ASP.NET, le flux d’usurpation d’identité peut être configuré dans le fichier aspnet.config trouvé dans le \<dossier Windows>-Microsoft.NET-Framework-vx.x.xxxx annuaire.  
  
 ASP.NET par défaut désactive le flux d’usurpation d’identité dans le fichier aspnet.config en utilisant les paramètres de configuration suivants :  
  
``` xml
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
 L’exemple suivant montre comment spécifier le comportement hérité qui ne circule pas l’identité Windows à travers les points asynchrones.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md)
