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
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="e2a9e-102">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="e2a9e-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="e2a9e-103">Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="e2a9e-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2a9e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2a9e-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2a9e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e2a9e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="e2a9e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="e2a9e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2a9e-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2a9e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e2a9e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2a9e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2a9e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e2a9e-110">Attributes</span></span>  
  
|<span data-ttu-id="e2a9e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e2a9e-111">Attribute</span></span>|<span data-ttu-id="e2a9e-112">Description</span><span class="sxs-lookup"><span data-stu-id="e2a9e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e2a9e-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e2a9e-114">Indique si l’identité Windows circule à travers des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e2a9e-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="e2a9e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e2a9e-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="e2a9e-116">Value</span></span>|<span data-ttu-id="e2a9e-117">Description</span><span class="sxs-lookup"><span data-stu-id="e2a9e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e2a9e-118">L’identité Windows ne coule pas à travers les points asynchrones, sauf si l’usurpation d’identité est effectuée par des méthodes gérées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="e2a9e-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e2a9e-120">L’identité Windows circule toujours à travers des points asynchrones, indépendamment de la façon dont l’usurpation d’identité a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2a9e-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e2a9e-121">Child Elements</span></span>  
 <span data-ttu-id="e2a9e-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2a9e-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e2a9e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e2a9e-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e2a9e-124">Element</span></span>|<span data-ttu-id="e2a9e-125">Description</span><span class="sxs-lookup"><span data-stu-id="e2a9e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e2a9e-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e2a9e-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2a9e-128">Notes </span><span class="sxs-lookup"><span data-stu-id="e2a9e-128">Remarks</span></span>  
 <span data-ttu-id="e2a9e-129">Dans les versions .NET Framework 1.0 et 1.1, l’identité Windows ne circule pas à travers les points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="e2a9e-130">Dans la version cadre .NET 2.0, il existe un objet qui contient des <xref:System.Threading.ExecutionContext> informations sur le thread actuellement exécutant, et le circule à travers des points asynchrones dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="e2a9e-131">L’imitation <xref:System.Security.Principal.WindowsIdentity> s’écoule également dans le cadre de l’information qui circule à travers <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> les points asynchrones, à condition que l’usurpation d’identité a été réalisée en utilisant des méthodes gérées telles que et non par d’autres moyens tels que la plate-forme invoquer des méthodes indigènes.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="e2a9e-132">Cet élément est utilisé pour spécifier que l’identité Windows ne flux à travers les points asynchrones, indépendamment de la façon dont l’usurpation d’identité a été réalisée.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="e2a9e-133">Vous pouvez modifier ce comportement par défaut de deux autres façons :</span><span class="sxs-lookup"><span data-stu-id="e2a9e-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="e2a9e-134">Dans le code géré sur une base par thread.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="e2a9e-135">Vous pouvez supprimer le flux par fil en <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> modifiant le <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>les <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> paramètres en utilisant le , , ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="e2a9e-136">Dans l’appel à l’interface d’hébergement non gérée pour charger l’heure courante de course de langue (CLR).</span><span class="sxs-lookup"><span data-stu-id="e2a9e-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="e2a9e-137">Si une interface d’hébergement non gérée (au lieu d’une simple gestion exécutable) est utilisée pour charger le CLR, vous pouvez spécifier un drapeau spécial dans l’appel à la fonction [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="e2a9e-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="e2a9e-138">Pour activer le mode de compatibilité `flags` pour l’ensemble du processus, `STARTUP_ALWAYSFLOW_IMPERSONATION`définissez le paramètre de la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) à .</span><span class="sxs-lookup"><span data-stu-id="e2a9e-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e2a9e-139">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e2a9e-139">Configuration File</span></span>  
 <span data-ttu-id="e2a9e-140">Dans une application cadre .NET, cet élément ne peut être utilisé que dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="e2a9e-141">Pour une application ASP.NET, le flux d’usurpation d’identité peut être configuré dans le fichier aspnet.config trouvé dans le \<dossier Windows>-Microsoft.NET-Framework-vx.x.xxxx annuaire.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="e2a9e-142">ASP.NET par défaut désactive le flux d’usurpation d’identité dans le fichier aspnet.config en utilisant les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="e2a9e-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e2a9e-143">Dans ASP.NET, si vous souhaitez autoriser le flux d’usurpation d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="e2a9e-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e2a9e-144"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e2a9e-144">Example</span></span>  
 <span data-ttu-id="e2a9e-145">L’exemple suivant montre comment spécifier que l’identité Windows circule à travers des points asynchrones, même lorsque l’usurpation d’identité est réalisée par d’autres moyens que des méthodes gérées.</span><span class="sxs-lookup"><span data-stu-id="e2a9e-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2a9e-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2a9e-146">See also</span></span>

- [<span data-ttu-id="e2a9e-147">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="e2a9e-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e2a9e-148">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="e2a9e-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e2a9e-149">\<héritageImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="e2a9e-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
