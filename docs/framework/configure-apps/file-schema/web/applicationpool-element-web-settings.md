---
title: <applicationPool>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: f0486e9faf70e7d5d147cfef996edcdaa8846963
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456293"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="08b46-102">\<applicationPool >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="08b46-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="08b46-103">Spécifie les paramètres de configuration qui sont utilisés par ASP.NET pour gérer le comportement au niveau du processus lorsqu’une application ASP.NET s’exécute en mode intégré [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="08b46-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08b46-104">Cet élément et la fonctionnalité qu’il prend en charge fonctionnent uniquement si votre application ASP.NET est hébergée sur [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="08b46-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="08b46-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="08b46-105">\<configuration></span></span>  
<span data-ttu-id="08b46-106">\<System.Web >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="08b46-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="08b46-107">\<applicationPool >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="08b46-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b46-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08b46-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08b46-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="08b46-109">Attributes and Elements</span></span>  
 <span data-ttu-id="08b46-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="08b46-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08b46-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="08b46-111">Attributes</span></span>  
  
|<span data-ttu-id="08b46-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="08b46-112">Attribute</span></span>|<span data-ttu-id="08b46-113">Description</span><span class="sxs-lookup"><span data-stu-id="08b46-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="08b46-114">Spécifie le nombre de demandes simultané ASP.NET autorise par UC.</span><span class="sxs-lookup"><span data-stu-id="08b46-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="08b46-115">Spécifie le nombre de threads simultané permettre être en cours d’exécution pour un pool d’applications pour chaque UC.</span><span class="sxs-lookup"><span data-stu-id="08b46-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="08b46-116">Cela fournit une autre façon de contrôler l’accès concurrentiel ASP.NET, car vous pouvez limiter le nombre de threads managés qui peut être utilisé par le processeur pour traiter les demandes.</span><span class="sxs-lookup"><span data-stu-id="08b46-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="08b46-117">Par défaut, ce paramètre est 0, ce qui signifie qu’ASP.NET ne limite pas le nombre de threads qui peuvent être créés par UC, bien que le pool de threads CLR limite également le nombre de threads qui peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="08b46-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="08b46-118">Spécifie le nombre maximal de demandes de file d’attente pour ASP.NET dans un processus unique.</span><span class="sxs-lookup"><span data-stu-id="08b46-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="08b46-119">Lorsque deux ou plusieurs applications de ASP.NET s’exécutent dans un pool d’applications unique, l’ensemble cumulatif de demandes envoyées à n’importe quelle application dans le pool d’applications est soumis à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="08b46-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08b46-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="08b46-120">Child Elements</span></span>  
 <span data-ttu-id="08b46-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="08b46-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08b46-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="08b46-122">Parent Elements</span></span>  
  
|<span data-ttu-id="08b46-123">Élément</span><span class="sxs-lookup"><span data-stu-id="08b46-123">Element</span></span>|<span data-ttu-id="08b46-124">Description</span><span class="sxs-lookup"><span data-stu-id="08b46-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08b46-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="08b46-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="08b46-126">Contient des informations sur la façon dont ASP.NET interagit avec une application hôte.</span><span class="sxs-lookup"><span data-stu-id="08b46-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08b46-127">Notes</span><span class="sxs-lookup"><span data-stu-id="08b46-127">Remarks</span></span>  
 <span data-ttu-id="08b46-128">Lorsque vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou une version ultérieure en mode intégré, cette combinaison d’éléments vous permet de configurer la façon dont ASP.NET gère les demandes de files d’attente et threads lorsque l’application est hébergée dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="08b46-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="08b46-129">Si vous exécutez IIS 6 ou [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] en mode classique ou ISAPI, ces paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="08b46-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="08b46-130">Le `applicationPool` paramètres s’appliquent à tous les pools d’applications qui s’exécutent sur une version particulière du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08b46-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="08b46-131">Les paramètres sont contenus dans un fichier aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="08b46-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="08b46-132">Il existe une version de ce fichier pour les versions 2.0 et 4.0 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08b46-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="08b46-133">(Les versions 3.0 et 3.5 du .NET Framework partagent le fichier aspnet.config avec la version 2.0.)</span><span class="sxs-lookup"><span data-stu-id="08b46-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08b46-134">Si vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] sur [!INCLUDE[win7](../../../../../includes/win7-md.md)], vous pouvez configurer un fichier aspnet.config séparé pour chaque pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="08b46-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="08b46-135">Cela vous permet d’adapter les performances des threads pour chaque pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="08b46-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="08b46-136">Pour le `maxConcurrentRequestsPerCPU` , le paramètre par défaut de « 5000 » dans le .NET Framework 4 efficacement désactive la limitation de requêtes est contrôlée par ASP.NET, sauf si vous avez réellement 5000 requêtes ou plus par UC.</span><span class="sxs-lookup"><span data-stu-id="08b46-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="08b46-137">Le paramètre par défaut dépend à la place le pool de threads CLR pour gérer automatiquement l’accès concurrentiel par UC.</span><span class="sxs-lookup"><span data-stu-id="08b46-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="08b46-138">Les applications qui utilisent beaucoup le traitement des demandes asynchrones ou qui possèdent de nombreuses requêtes de longue bloqués sur le réseau d’e/s, bénéficieront de la limite par défaut accrue dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="08b46-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="08b46-139">Paramètre `maxConcurrentRequestsPerCPU` zéro désactive l’utilisation de threads managés pour le traitement des demandes ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="08b46-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="08b46-140">Quand une application s’exécute dans un pool d’applications IIS, demandes de restent sur le thread d’e/s de IIS et par conséquent, l’accès concurrentiel est limitée par les paramètres de thread IIS.</span><span class="sxs-lookup"><span data-stu-id="08b46-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="08b46-141">Le `requestQueueLimit` paramètre fonctionne de la même façon que le `requestQueueLimit` attribut de la [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) élément, qui est défini dans les fichiers Web.config pour les applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="08b46-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="08b46-142">Toutefois, le `requestQueueLimit` paramètre dans un fichier aspnet.config substitue le `requestQueueLimit` définissant dans un fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="08b46-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="08b46-143">En d’autres termes, si les deux attributs sont définies (par défaut, la valeur est true), le `requestQueueLimit` paramètre dans le fichier aspnet.config est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="08b46-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08b46-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="08b46-144">Example</span></span>  
 <span data-ttu-id="08b46-145">L’exemple suivant montre comment configurer le comportement au niveau du processus ASP.NET dans le fichier aspnet.config dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="08b46-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="08b46-146">L’application est hébergée dans un [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="08b46-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
- [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] <span data-ttu-id="08b46-147">s’exécute en mode intégré.</span><span class="sxs-lookup"><span data-stu-id="08b46-147">is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="08b46-148">À l’aide de l’application est la [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="08b46-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="08b46-149">Les valeurs dans l’exemple sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="08b46-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="08b46-150">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="08b46-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08b46-151">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="08b46-151">Namespace</span></span>||  
|<span data-ttu-id="08b46-152">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="08b46-152">Schema Name</span></span>||  
|<span data-ttu-id="08b46-153">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="08b46-153">Validation File</span></span>||  
|<span data-ttu-id="08b46-154">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="08b46-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="08b46-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08b46-155">See also</span></span>

- [<span data-ttu-id="08b46-156">\<system.web>, élément (paramètres web)</span><span class="sxs-lookup"><span data-stu-id="08b46-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
