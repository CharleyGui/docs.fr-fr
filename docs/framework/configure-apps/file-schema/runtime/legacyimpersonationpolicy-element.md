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
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="f66d0-102">\<héritageImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="f66d0-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="f66d0-103">Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.</span><span class="sxs-lookup"><span data-stu-id="f66d0-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="f66d0-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f66d0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f66d0-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f66d0-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f66d0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="f66d0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66d0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f66d0-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f66d0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f66d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f66d0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f66d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f66d0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f66d0-110">Attributes</span></span>  
  
|<span data-ttu-id="f66d0-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f66d0-111">Attribute</span></span>|<span data-ttu-id="f66d0-112">Description</span><span class="sxs-lookup"><span data-stu-id="f66d0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f66d0-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f66d0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f66d0-114">Précise que le <xref:System.Security.Principal.WindowsIdentity> ne coule pas à travers les points <xref:System.Threading.ExecutionContext> asynchrones, indépendamment des paramètres de flux sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="f66d0-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f66d0-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="f66d0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f66d0-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="f66d0-116">Value</span></span>|<span data-ttu-id="f66d0-117">Description</span><span class="sxs-lookup"><span data-stu-id="f66d0-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f66d0-118"><xref:System.Security.Principal.WindowsIdentity>circule à travers les points <xref:System.Threading.ExecutionContext> asynchrones en fonction des paramètres de flux pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="f66d0-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="f66d0-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f66d0-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f66d0-120"><xref:System.Security.Principal.WindowsIdentity>ne coule pas à travers les points <xref:System.Threading.ExecutionContext> asynchrones, indépendamment des paramètres de flux sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="f66d0-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f66d0-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f66d0-121">Child Elements</span></span>  
 <span data-ttu-id="f66d0-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f66d0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f66d0-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f66d0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f66d0-124">Élément</span><span class="sxs-lookup"><span data-stu-id="f66d0-124">Element</span></span>|<span data-ttu-id="f66d0-125">Description</span><span class="sxs-lookup"><span data-stu-id="f66d0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f66d0-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f66d0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f66d0-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f66d0-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f66d0-128">Notes </span><span class="sxs-lookup"><span data-stu-id="f66d0-128">Remarks</span></span>  
 <span data-ttu-id="f66d0-129">Dans les versions .NET Framework 1.0 et <xref:System.Security.Principal.WindowsIdentity> 1.1, le ne circule pas à travers les points asynchrones définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f66d0-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="f66d0-130">En commençant par la version cadre .NET 2.0, il existe un objet qui contient des <xref:System.Threading.ExecutionContext> informations sur le thread actuellement exécutant, et il circule à travers des points asynchrones dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="f66d0-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="f66d0-131">Le <xref:System.Security.Principal.WindowsIdentity> est inclus dans ce contexte d’exécution et donc aussi coule à travers les points asynchrones, ce qui signifie que si un contexte d’usurpation d’identité existe, il coulera ainsi.</span><span class="sxs-lookup"><span data-stu-id="f66d0-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="f66d0-132">En commençant par le cadre .NET 2.0, vous pouvez utiliser l’élément `<legacyImpersonationPolicy>` pour spécifier qui <xref:System.Security.Principal.WindowsIdentity> ne circule pas à travers les points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="f66d0-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f66d0-133">L’heure courante de fonctionnement de langue (CLR) est au courant des opérations d’usurpation d’identité effectuées en utilisant seulement le code géré, pas de l’usurpation d’identité effectuée en dehors du code géré, par exemple par le biais de la plate-forme invoquer le code non géré ou par des appels directs vers des fonctions Win32.</span><span class="sxs-lookup"><span data-stu-id="f66d0-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="f66d0-134">Seuls <xref:System.Security.Principal.WindowsIdentity> les objets gérés peuvent circuler à travers `alwaysFlowImpersonationPolicy` des points asynchrones, à moins que l’élément n’ait été mis en place pour vrai (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="f66d0-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="f66d0-135">La `alwaysFlowImpersonationPolicy` définition de l’élément à vrai spécifie que l’identité Windows circule toujours à travers des points asynchrones, indépendamment de la façon dont l’usurpation d’identité a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="f66d0-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="f66d0-136">Pour plus d’informations sur l’usurpation d’identité non mentée à travers les points asynchrones, voir [ \<toujoursFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="f66d0-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="f66d0-137">Vous pouvez modifier ce comportement par défaut de deux autres façons :</span><span class="sxs-lookup"><span data-stu-id="f66d0-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="f66d0-138">Dans le code géré sur une base par thread.</span><span class="sxs-lookup"><span data-stu-id="f66d0-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="f66d0-139">Vous pouvez supprimer le flux par fil en <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> modifiant les <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>paramètres <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> et les paramètres en utilisant la , ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="f66d0-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="f66d0-140">Dans l’appel à l’interface d’hébergement non gérée pour charger l’heure courante de course de langue (CLR).</span><span class="sxs-lookup"><span data-stu-id="f66d0-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="f66d0-141">Si une interface d’hébergement non gérée (au lieu d’une simple gestion exécutable) est utilisée pour charger le CLR, vous pouvez spécifier un drapeau spécial dans l’appel à la fonction [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="f66d0-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="f66d0-142">Pour activer le mode de compatibilité `flags` pour l’ensemble du processus, définissez le paramètre de [la fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) pour STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="f66d0-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="f66d0-143">Pour plus d’informations, voir le [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="f66d0-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f66d0-144">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f66d0-144">Configuration File</span></span>  
 <span data-ttu-id="f66d0-145">Dans une application cadre .NET, cet élément ne peut être utilisé que dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="f66d0-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="f66d0-146">Pour une application ASP.NET, le flux d’usurpation d’identité peut être configuré dans le fichier aspnet.config trouvé dans le \<dossier Windows>-Microsoft.NET-Framework-vx.x.xxxx annuaire.</span><span class="sxs-lookup"><span data-stu-id="f66d0-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="f66d0-147">ASP.NET par défaut désactive le flux d’usurpation d’identité dans le fichier aspnet.config en utilisant les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="f66d0-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f66d0-148">Dans ASP.NET, si vous souhaitez autoriser le flux d’usurpation d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="f66d0-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="f66d0-149"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f66d0-149">Example</span></span>  
 <span data-ttu-id="f66d0-150">L’exemple suivant montre comment spécifier le comportement hérité qui ne circule pas l’identité Windows à travers les points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="f66d0-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f66d0-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f66d0-151">See also</span></span>

- [<span data-ttu-id="f66d0-152">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="f66d0-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f66d0-153">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="f66d0-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f66d0-154">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="f66d0-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
