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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 164492eb1abc7329481f158963118b47d2c4aebc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252859"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="d1e00-102">\<alwaysFlowImpersonationPolicy >, élément</span><span class="sxs-lookup"><span data-stu-id="d1e00-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="d1e00-103">Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="d1e00-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="d1e00-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1e00-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d1e00-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1e00-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d1e00-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysFlowImpersonationPolicy>** </span><span class="sxs-lookup"><span data-stu-id="d1e00-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="d1e00-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1e00-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1e00-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1e00-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1e00-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1e00-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1e00-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1e00-110">Attributes</span></span>  
  
|<span data-ttu-id="d1e00-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1e00-111">Attribute</span></span>|<span data-ttu-id="d1e00-112">Description</span><span class="sxs-lookup"><span data-stu-id="d1e00-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d1e00-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="d1e00-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d1e00-114">Indique si l’identité Windows circule entre des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="d1e00-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d1e00-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="d1e00-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d1e00-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="d1e00-116">Value</span></span>|<span data-ttu-id="d1e00-117">Description</span><span class="sxs-lookup"><span data-stu-id="d1e00-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d1e00-118">L’identité Windows ne passe pas entre des points asynchrones, sauf si l’emprunt d’identité est effectué via des <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>méthodes managées telles que.</span><span class="sxs-lookup"><span data-stu-id="d1e00-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="d1e00-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d1e00-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d1e00-120">L’identité Windows est toujours transgérée entre les points asynchrones, indépendamment de la façon dont l’emprunt d’identité a été effectué.</span><span class="sxs-lookup"><span data-stu-id="d1e00-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1e00-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1e00-121">Child Elements</span></span>  
 <span data-ttu-id="d1e00-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d1e00-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1e00-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1e00-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d1e00-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d1e00-124">Element</span></span>|<span data-ttu-id="d1e00-125">Description</span><span class="sxs-lookup"><span data-stu-id="d1e00-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1e00-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1e00-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d1e00-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d1e00-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1e00-128">Notes</span><span class="sxs-lookup"><span data-stu-id="d1e00-128">Remarks</span></span>  
 <span data-ttu-id="d1e00-129">Dans les versions 1,0 et 1,1 de .NET Framework, l’identité Windows ne passe pas entre les points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="d1e00-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="d1e00-130">Dans la .NET Framework version 2,0, il existe un <xref:System.Threading.ExecutionContext> objet qui contient des informations sur le thread en cours d’exécution et le transmet entre des points asynchrones au sein d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d1e00-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="d1e00-131">Le <xref:System.Security.Principal.WindowsIdentity> flux est également inclus dans les informations qui circulent entre les points asynchrones, à condition que l’emprunt d’identité ait été obtenu <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> à l’aide de méthodes managées telles que et non par d’autres moyens tels que l’appel de code non managé aux méthodes natives.</span><span class="sxs-lookup"><span data-stu-id="d1e00-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="d1e00-132">Cet élément est utilisé pour spécifier que l’identité Windows circule entre des points asynchrones, quelle que soit la façon dont l’emprunt d’identité a été atteint.</span><span class="sxs-lookup"><span data-stu-id="d1e00-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="d1e00-133">Vous pouvez modifier ce comportement par défaut de deux manières :</span><span class="sxs-lookup"><span data-stu-id="d1e00-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="d1e00-134">En code managé pour chaque thread.</span><span class="sxs-lookup"><span data-stu-id="d1e00-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="d1e00-135">Vous pouvez supprimer le workflow pour chaque <xref:System.Threading.ExecutionContext> thread en modifiant les paramètres et <xref:System.Security.SecurityContext> à l’aide de la <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>méthode, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d1e00-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="d1e00-136">Dans l’appel à l’interface d’hébergement non managée pour charger le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d1e00-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="d1e00-137">Si une interface d’hébergement non managée (au lieu d’un simple exécutable managé) est utilisée pour charger le CLR, vous pouvez spécifier un indicateur spécial dans l’appel à la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d1e00-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="d1e00-138">Pour activer le mode de compatibilité pour l’ensemble du processus, `flags` définissez le paramètre de la `STARTUP_ALWAYSFLOW_IMPERSONATION` [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) sur.</span><span class="sxs-lookup"><span data-stu-id="d1e00-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d1e00-139">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="d1e00-139">Configuration File</span></span>  
 <span data-ttu-id="d1e00-140">Dans une application .NET Framework, cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="d1e00-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="d1e00-141">Pour une application ASP.net, le workflow d’emprunt d’identité peut être configuré dans le fichier Aspnet. config qui se \<trouve dans le dossier Windows > répertoire \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="d1e00-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="d1e00-142">Par défaut, ASP.NET désactive le workflow d’emprunt d’identité dans le fichier Aspnet. config à l’aide des paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="d1e00-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d1e00-143">Dans ASP.NET, si vous souhaitez autoriser le workflow d’emprunt d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="d1e00-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d1e00-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="d1e00-144">Example</span></span>  
 <span data-ttu-id="d1e00-145">L’exemple suivant montre comment spécifier que l’identité Windows passe d’un point asynchrone à un autre, même lorsque l’emprunt d’identité est réalisé à l’aide d’autres moyens que les méthodes managées.</span><span class="sxs-lookup"><span data-stu-id="d1e00-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1e00-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1e00-146">See also</span></span>

- [<span data-ttu-id="d1e00-147">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="d1e00-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d1e00-148">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d1e00-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d1e00-149">\<legacyImpersonationPolicy >, élément</span><span class="sxs-lookup"><span data-stu-id="d1e00-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
