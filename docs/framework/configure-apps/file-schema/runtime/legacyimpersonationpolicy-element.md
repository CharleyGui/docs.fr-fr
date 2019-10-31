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
ms.openlocfilehash: 18a027bc09f2400a10a06efdc4c5355686bcb56d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116542"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="6b5f6-102">\<élément legacyImpersonationPolicy ></span><span class="sxs-lookup"><span data-stu-id="6b5f6-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="6b5f6-103">Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="6b5f6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b5f6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b5f6-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b5f6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6b5f6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyImpersonationPolicy** ></span><span class="sxs-lookup"><span data-stu-id="6b5f6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5f6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b5f6-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b5f6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6b5f6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6b5f6-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b5f6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="6b5f6-110">Attributes</span></span>  
  
|<span data-ttu-id="6b5f6-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="6b5f6-111">Attribute</span></span>|<span data-ttu-id="6b5f6-112">Description</span><span class="sxs-lookup"><span data-stu-id="6b5f6-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6b5f6-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6b5f6-114">Spécifie que le <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones, quels que soient les paramètres de <xref:System.Threading.ExecutionContext> Flow sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6b5f6-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="6b5f6-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6b5f6-116">valeur</span><span class="sxs-lookup"><span data-stu-id="6b5f6-116">Value</span></span>|<span data-ttu-id="6b5f6-117">Description</span><span class="sxs-lookup"><span data-stu-id="6b5f6-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6b5f6-118"><xref:System.Security.Principal.WindowsIdentity> est transmis entre des points asynchrones en fonction des paramètres de flux de <xref:System.Threading.ExecutionContext> pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="6b5f6-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6b5f6-120"><xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones, quels que soient les paramètres de <xref:System.Threading.ExecutionContext> de flow sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b5f6-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6b5f6-121">Child Elements</span></span>  
 <span data-ttu-id="6b5f6-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="6b5f6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b5f6-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6b5f6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6b5f6-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6b5f6-124">Element</span></span>|<span data-ttu-id="6b5f6-125">Description</span><span class="sxs-lookup"><span data-stu-id="6b5f6-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6b5f6-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6b5f6-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b5f6-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6b5f6-128">Remarks</span></span>  
 <span data-ttu-id="6b5f6-129">Dans les versions 1,0 et 1,1 de .NET Framework, le <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis sur les points asynchrones définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="6b5f6-130">À partir de la version .NET Framework 2,0, il existe un objet <xref:System.Threading.ExecutionContext> qui contient des informations sur le thread en cours d’exécution et qui est transmis entre des points asynchrones au sein d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="6b5f6-131">Le <xref:System.Security.Principal.WindowsIdentity> est inclus dans ce contexte d’exécution et est, par conséquent, transmis entre les points asynchrones, ce qui signifie que si un contexte d’emprunt d’identité existe, il est également transmis.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="6b5f6-132">À partir de la .NET Framework 2,0, vous pouvez utiliser l’élément `<legacyImpersonationPolicy>` pour spécifier que <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b5f6-133">Le common language runtime (CLR) tient compte des opérations d’emprunt d’identité effectuées à l’aide du code managé uniquement, et non de l’emprunt d’identité effectué en dehors du code managé, par exemple par le biais de l’appel de code non managé au code non managé ou via des appels directs à des fonctions Win32.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="6b5f6-134">Seuls les objets <xref:System.Security.Principal.WindowsIdentity> managés peuvent circuler entre des points asynchrones, sauf si l’élément `alwaysFlowImpersonationPolicy` a la valeur true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="6b5f6-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="6b5f6-135">L’affectation de la valeur true à l’élément `alwaysFlowImpersonationPolicy` spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment de la façon dont l’emprunt d’identité a été effectué.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="6b5f6-136">Pour plus d’informations sur le passage de l’emprunt d’identité non managé entre des points asynchrones, consultez [\<élément alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="6b5f6-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="6b5f6-137">Vous pouvez modifier ce comportement par défaut de deux manières :</span><span class="sxs-lookup"><span data-stu-id="6b5f6-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="6b5f6-138">En code managé pour chaque thread.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="6b5f6-139">Vous pouvez supprimer le workflow pour chaque thread en modifiant les paramètres <xref:System.Threading.ExecutionContext> et <xref:System.Security.SecurityContext> à l’aide de la méthode <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="6b5f6-140">Dans l’appel à l’interface d’hébergement non managée pour charger le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6b5f6-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="6b5f6-141">Si une interface d’hébergement non managée (au lieu d’un simple exécutable managé) est utilisée pour charger le CLR, vous pouvez spécifier un indicateur spécial dans l’appel à la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6b5f6-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="6b5f6-142">Pour activer le mode de compatibilité pour l’ensemble du processus, définissez le paramètre `flags` pour la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) sur STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="6b5f6-143">Pour plus d’informations, consultez l' [élément\<alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="6b5f6-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6b5f6-144">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="6b5f6-144">Configuration File</span></span>  
 <span data-ttu-id="6b5f6-145">Dans une application .NET Framework, cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="6b5f6-146">Pour une application ASP.NET, le workflow d’emprunt d’identité peut être configuré dans le fichier Aspnet. config qui se trouve dans le dossier Windows \<> répertoire \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="6b5f6-147">Par défaut, ASP.NET désactive le workflow d’emprunt d’identité dans le fichier Aspnet. config à l’aide des paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="6b5f6-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="6b5f6-148">Dans ASP.NET, si vous souhaitez autoriser le workflow d’emprunt d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="6b5f6-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="6b5f6-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b5f6-149">Example</span></span>  
 <span data-ttu-id="6b5f6-150">L’exemple suivant montre comment spécifier le comportement hérité qui ne passe pas l’identité Windows entre des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="6b5f6-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b5f6-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b5f6-151">See also</span></span>

- [<span data-ttu-id="6b5f6-152">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="6b5f6-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6b5f6-153">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6b5f6-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6b5f6-154">\<élément alwaysFlowImpersonationPolicy ></span><span class="sxs-lookup"><span data-stu-id="6b5f6-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
