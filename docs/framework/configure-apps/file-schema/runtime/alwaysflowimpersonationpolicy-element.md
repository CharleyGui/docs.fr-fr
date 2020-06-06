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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154481"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="29c4b-102">Élément \<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="29c4b-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="29c4b-103">Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="29c4b-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="29c4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29c4b-104">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29c4b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="29c4b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="29c4b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="29c4b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29c4b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="29c4b-107">Attributes</span></span>  
  
|<span data-ttu-id="29c4b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="29c4b-108">Attribute</span></span>|<span data-ttu-id="29c4b-109">Description</span><span class="sxs-lookup"><span data-stu-id="29c4b-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="29c4b-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="29c4b-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="29c4b-111">Indique si l’identité Windows circule entre des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="29c4b-111">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="29c4b-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="29c4b-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="29c4b-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="29c4b-113">Value</span></span>|<span data-ttu-id="29c4b-114">Description</span><span class="sxs-lookup"><span data-stu-id="29c4b-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="29c4b-115">L’identité Windows ne passe pas entre des points asynchrones, sauf si l’emprunt d’identité est effectué via des méthodes managées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .</span><span class="sxs-lookup"><span data-stu-id="29c4b-115">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="29c4b-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="29c4b-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="29c4b-117">L’identité Windows est toujours transgérée entre les points asynchrones, indépendamment de la façon dont l’emprunt d’identité a été effectué.</span><span class="sxs-lookup"><span data-stu-id="29c4b-117">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29c4b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29c4b-118">Child Elements</span></span>  
 <span data-ttu-id="29c4b-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="29c4b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29c4b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29c4b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="29c4b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="29c4b-121">Element</span></span>|<span data-ttu-id="29c4b-122">Description</span><span class="sxs-lookup"><span data-stu-id="29c4b-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="29c4b-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29c4b-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="29c4b-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="29c4b-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29c4b-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="29c4b-125">Remarks</span></span>  
 <span data-ttu-id="29c4b-126">Dans les versions 1,0 et 1,1 de .NET Framework, l’identité Windows ne passe pas entre les points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="29c4b-126">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="29c4b-127">Dans la .NET Framework version 2,0, il existe un <xref:System.Threading.ExecutionContext> objet qui contient des informations sur le thread en cours d’exécution et le transmet entre des points asynchrones au sein d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="29c4b-127">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="29c4b-128">Le <xref:System.Security.Principal.WindowsIdentity> flux est également inclus dans les informations qui circulent entre les points asynchrones, à condition que l’emprunt d’identité ait été obtenu à l’aide de méthodes managées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> et non par d’autres moyens tels que l’appel de code non managé aux méthodes natives.</span><span class="sxs-lookup"><span data-stu-id="29c4b-128">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="29c4b-129">Cet élément est utilisé pour spécifier que l’identité Windows circule entre des points asynchrones, quelle que soit la façon dont l’emprunt d’identité a été atteint.</span><span class="sxs-lookup"><span data-stu-id="29c4b-129">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="29c4b-130">Vous pouvez modifier ce comportement par défaut de deux manières :</span><span class="sxs-lookup"><span data-stu-id="29c4b-130">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="29c4b-131">En code managé pour chaque thread.</span><span class="sxs-lookup"><span data-stu-id="29c4b-131">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="29c4b-132">Vous pouvez supprimer le workflow pour chaque thread en modifiant les <xref:System.Threading.ExecutionContext> paramètres et à <xref:System.Security.SecurityContext> l’aide de la <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> méthode, ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="29c4b-132">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="29c4b-133">Dans l’appel à l’interface d’hébergement non managée pour charger le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="29c4b-133">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="29c4b-134">Si une interface d’hébergement non managée (au lieu d’un simple exécutable managé) est utilisée pour charger le CLR, vous pouvez spécifier un indicateur spécial dans l’appel à la fonction [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="29c4b-134">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="29c4b-135">Pour activer le mode de compatibilité pour l’ensemble du processus, définissez le `flags` paramètre de la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) sur `STARTUP_ALWAYSFLOW_IMPERSONATION` .</span><span class="sxs-lookup"><span data-stu-id="29c4b-135">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="29c4b-136">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="29c4b-136">Configuration File</span></span>  
 <span data-ttu-id="29c4b-137">Dans une application .NET Framework, cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="29c4b-137">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="29c4b-138">Pour une application ASP.NET, le workflow d’emprunt d’identité peut être configuré dans le fichier Aspnet. config qui se trouve dans le \<Windows Folder> répertoire \Microsoft.NET\Framework\vx.x.xxxx</span><span class="sxs-lookup"><span data-stu-id="29c4b-138">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="29c4b-139">Par défaut, ASP.NET désactive le workflow d’emprunt d’identité dans le fichier Aspnet. config à l’aide des paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="29c4b-139">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="29c4b-140">Dans ASP.NET, si vous souhaitez autoriser le workflow d’emprunt d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="29c4b-140">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="29c4b-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="29c4b-141">Example</span></span>  
 <span data-ttu-id="29c4b-142">L’exemple suivant montre comment spécifier que l’identité Windows passe d’un point asynchrone à un autre, même lorsque l’emprunt d’identité est réalisé à l’aide d’autres moyens que les méthodes managées.</span><span class="sxs-lookup"><span data-stu-id="29c4b-142">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29c4b-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29c4b-143">See also</span></span>

- [<span data-ttu-id="29c4b-144">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="29c4b-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="29c4b-145">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="29c4b-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="29c4b-146">\<legacyImpersonationPolicy>Appartient</span><span class="sxs-lookup"><span data-stu-id="29c4b-146">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
