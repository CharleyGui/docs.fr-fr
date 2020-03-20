---
title: <applicationPool>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152852"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="0c265-102">\<applicationPool >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="0c265-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="0c265-103">Spécifie les paramètres de configuration qui sont utilisés par ASP.NET pour gérer le comportement à l’échelle du processus lorsqu’une application ASP.NET est en mode intégré sur IIS 7.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0c265-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0c265-104">Cet élément et la fonctionnalité qu’il prend en charge ne fonctionnent que si votre application ASP.NET est hébergée sur les versions IIS 7.0 ou ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0c265-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[<span data-ttu-id="0c265-105">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="0c265-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0c265-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0c265-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="0c265-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span><span class="sxs-lookup"><span data-stu-id="0c265-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c265-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c265-108">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c265-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c265-109">Attributes and Elements</span></span>  

<span data-ttu-id="0c265-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c265-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c265-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c265-111">Attributes</span></span>  
  
|<span data-ttu-id="0c265-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c265-112">Attribute</span></span>|<span data-ttu-id="0c265-113">Description</span><span class="sxs-lookup"><span data-stu-id="0c265-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="0c265-114">Précise le nombre de demandes simultanées ASP.NET permet par processeur.</span><span class="sxs-lookup"><span data-stu-id="0c265-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="0c265-115">Précise le nombre de threads simultanés qui peuvent être en cours d’exécution pour un pool d’applications pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="0c265-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="0c265-116">Cela fournit un autre moyen de contrôler ASP.NET concurrence, car vous pouvez limiter le nombre de threads gérés qui peuvent être utilisés par processeur pour servir les demandes.</span><span class="sxs-lookup"><span data-stu-id="0c265-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="0c265-117">Par défaut, ce paramètre est de 0, ce qui signifie que ASP.NET ne limite pas le nombre de threads qui peuvent être créés par processeur, bien que le pool de thread CLR limite également le nombre de threads qui peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="0c265-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="0c265-118">Spécifie le nombre maximum de demandes qui peuvent être en file d’attente pour ASP.NET en un seul processus.</span><span class="sxs-lookup"><span data-stu-id="0c265-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="0c265-119">Lorsque deux demandes de ASP.NET s’exécutent dans un seul pool d’applications, l’ensemble cumulatif de demandes adressées à toute demande dans le pool de demandes est soumis à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="0c265-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c265-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c265-120">Child Elements</span></span>  
 <span data-ttu-id="0c265-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c265-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c265-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c265-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0c265-123">Élément</span><span class="sxs-lookup"><span data-stu-id="0c265-123">Element</span></span>|<span data-ttu-id="0c265-124">Description</span><span class="sxs-lookup"><span data-stu-id="0c265-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c265-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="0c265-125">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="0c265-126">Contient des informations sur la façon dont ASP.NET interagit avec une application hôte.</span><span class="sxs-lookup"><span data-stu-id="0c265-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c265-127">Notes </span><span class="sxs-lookup"><span data-stu-id="0c265-127">Remarks</span></span>  

<span data-ttu-id="0c265-128">Lorsque vous exécutez IIS 7.0 ou une version ultérieure en mode intégré, cette combinaison d’éléments vous permet de configurer la façon dont ASP.NET gère les demandes de threads et de files d’attente lorsque l’application est hébergée dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="0c265-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="0c265-129">Si vous exécutez IIS 6 ou si vous exécutez IIS 7.0 en mode Classique ou en mode ISAPI, ces paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="0c265-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="0c265-130">Les `applicationPool` paramètres s’appliquent à tous les pools d’applications qui s’exécutent sur une version particulière du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="0c265-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="0c265-131">Les paramètres sont contenus dans un fichier aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="0c265-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="0c265-132">Il existe une version de ce fichier pour les versions 2.0 et 4.0 du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="0c265-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="0c265-133">(Versions 3.0 et 3.5 du cadre .NET part du fichier aspnet.config avec la version 2.0.)</span><span class="sxs-lookup"><span data-stu-id="0c265-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0c265-134">Si vous exécutez IIS 7.0 sur Windows 7, vous pouvez configurer un fichier aspnet.config séparé pour chaque pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="0c265-134">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="0c265-135">Cela vous permet d’adapter les performances des threads pour chaque pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="0c265-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="0c265-136">Pour `maxConcurrentRequestsPerCPU` le paramètre, le paramètre par défaut de "5000" dans le cadre .NET 4 éteint effectivement la limitation de demande qui est contrôlée par ASP.NET, sauf si vous avez réellement 5000 demandes ou plus par processeur.</span><span class="sxs-lookup"><span data-stu-id="0c265-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="0c265-137">Le paramètre par défaut dépend plutôt du thread-pool CLR pour gérer automatiquement la concurrence par processeur.</span><span class="sxs-lookup"><span data-stu-id="0c265-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="0c265-138">Les applications qui font un usage intensif du traitement des demandes asynchrones, ou qui ont de nombreuses demandes de longue durée bloquées sur le réseau I / O, bénéficieront de la limite accrue par défaut dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="0c265-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="0c265-139">Le `maxConcurrentRequestsPerCPU` réglage à zéro éteint l’utilisation de threads gérés pour le traitement des demandes ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0c265-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="0c265-140">Lorsqu’une application s’exécute dans un pool d’applications IIS, demande de rester sur le thread IIS I/O et donc la concurrence est étranglée par les paramètres de thread IIS.</span><span class="sxs-lookup"><span data-stu-id="0c265-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="0c265-141">Le `requestQueueLimit` paramètre fonctionne de `requestQueueLimit` la même manière que l’attribut de l’élément [processModel,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) qui est défini dans les fichiers Web.config pour ASP.NET applications.</span><span class="sxs-lookup"><span data-stu-id="0c265-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="0c265-142">Cependant, `requestQueueLimit` le paramètre dans un fichier aspnet.config remplace le `requestQueueLimit` paramètre dans un fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="0c265-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="0c265-143">En d’autres termes, si les deux attributs sont `requestQueueLimit` définis (par défaut, c’est vrai), le paramètre dans le fichier aspnet.config prime.</span><span class="sxs-lookup"><span data-stu-id="0c265-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c265-144"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0c265-144">Example</span></span>  

<span data-ttu-id="0c265-145">L’exemple suivant montre comment configurer ASP.NET comportement à l’échelle du processus dans le fichier aspnet.config dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c265-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="0c265-146">L’application est hébergée dans un pool d’applications IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="0c265-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="0c265-147">L’IIS 7.0 fonctionne en mode intégré.</span><span class="sxs-lookup"><span data-stu-id="0c265-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="0c265-148">L’application utilise le .NET Framework 3.5 SP1 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0c265-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="0c265-149">Les valeurs dans l’exemple sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c265-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="0c265-150">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="0c265-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c265-151">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="0c265-151">Namespace</span></span>||  
|<span data-ttu-id="0c265-152">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="0c265-152">Schema Name</span></span>||  
|<span data-ttu-id="0c265-153">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="0c265-153">Validation File</span></span>||  
|<span data-ttu-id="0c265-154">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="0c265-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="0c265-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c265-155">See also</span></span>

- [<span data-ttu-id="0c265-156">\<system.web> Element (Paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="0c265-156">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
