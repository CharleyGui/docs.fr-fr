---
title: <applicationPool>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152852"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="a95e5-102">\<applicationPool>, élément (paramètres web)</span><span class="sxs-lookup"><span data-stu-id="a95e5-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="a95e5-103">Spécifie les paramètres de configuration utilisés par ASP.NET pour gérer le comportement au niveau du processus quand une application ASP.NET s’exécute en mode intégré sur IIS 7,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a95e5-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a95e5-104">Cet élément et la fonctionnalité qu’il prend en charge fonctionnent uniquement si votre application ASP.NET est hébergée sur IIS 7,0 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a95e5-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a><span data-ttu-id="a95e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a95e5-105">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a95e5-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a95e5-106">Attributes and Elements</span></span>  

<span data-ttu-id="a95e5-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a95e5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a95e5-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="a95e5-108">Attributes</span></span>  
  
|<span data-ttu-id="a95e5-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="a95e5-109">Attribute</span></span>|<span data-ttu-id="a95e5-110">Description</span><span class="sxs-lookup"><span data-stu-id="a95e5-110">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="a95e5-111">Spécifie le nombre de requêtes simultanées que ASP.NET autorise par UC.</span><span class="sxs-lookup"><span data-stu-id="a95e5-111">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="a95e5-112">Spécifie le nombre de threads simultanés pouvant être en cours d’exécution pour un pool d’applications pour chaque UC.</span><span class="sxs-lookup"><span data-stu-id="a95e5-112">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="a95e5-113">Cela fournit une autre façon de contrôler l’accès concurrentiel ASP.NET, car vous pouvez limiter le nombre de threads managés qui peuvent être utilisés par UC pour traiter les demandes.</span><span class="sxs-lookup"><span data-stu-id="a95e5-113">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="a95e5-114">Par défaut, ce paramètre a la valeur 0, ce qui signifie que ASP.NET ne limite pas le nombre de threads qui peuvent être créés par UC, bien que le pool de threads CLR limite également le nombre de threads qui peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="a95e5-114">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="a95e5-115">Spécifie le nombre maximal de demandes qui peuvent être mises en file d’attente pour ASP.NET dans un même processus.</span><span class="sxs-lookup"><span data-stu-id="a95e5-115">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="a95e5-116">Quand plusieurs applications ASP.NET s’exécutent dans un seul pool d’applications, l’ensemble cumulé des demandes adressées à une application dans le pool d’applications est soumis à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="a95e5-116">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a95e5-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a95e5-117">Child Elements</span></span>  
 <span data-ttu-id="a95e5-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a95e5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a95e5-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a95e5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a95e5-120">Élément</span><span class="sxs-lookup"><span data-stu-id="a95e5-120">Element</span></span>|<span data-ttu-id="a95e5-121">Description</span><span class="sxs-lookup"><span data-stu-id="a95e5-121">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="a95e5-122">Contient des informations sur la façon dont ASP.NET interagit avec une application hôte.</span><span class="sxs-lookup"><span data-stu-id="a95e5-122">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a95e5-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="a95e5-123">Remarks</span></span>  

<span data-ttu-id="a95e5-124">Lorsque vous exécutez IIS 7,0 ou une version ultérieure en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les demandes de threads et de files d’attente lorsque l’application est hébergée dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="a95e5-124">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="a95e5-125">Si vous exécutez IIS 6 ou IIS 7,0 en mode classique ou en mode ISAPI, ces paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="a95e5-125">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="a95e5-126">Les `applicationPool` paramètres s’appliquent à tous les pools d’applications qui s’exécutent sur une version particulière du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a95e5-126">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="a95e5-127">Les paramètres sont contenus dans un fichier Aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="a95e5-127">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="a95e5-128">Il existe une version de ce fichier pour les versions 2,0 et 4,0 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a95e5-128">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="a95e5-129">(Les versions 3,0 et 3,5 du .NET Framework partagent le fichier Aspnet. config avec la version 2,0.)</span><span class="sxs-lookup"><span data-stu-id="a95e5-129">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a95e5-130">Si vous exécutez IIS 7,0 sur Windows 7, vous pouvez configurer un fichier Aspnet. config distinct pour chaque pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="a95e5-130">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="a95e5-131">Cela vous permet de personnaliser les performances des threads pour chaque pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="a95e5-131">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="a95e5-132">Pour le `maxConcurrentRequestsPerCPU` paramètre, le paramètre par défaut « 5000 » dans le .NET Framework 4 désactive efficacement la limitation des demandes qui est contrôlée par ASP.net, à moins que vous n’ayez au moins 5000 demandes par UC.</span><span class="sxs-lookup"><span data-stu-id="a95e5-132">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="a95e5-133">Le paramètre par défaut dépend plutôt du pool de threads CLR pour gérer automatiquement l’accès concurrentiel par UC.</span><span class="sxs-lookup"><span data-stu-id="a95e5-133">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="a95e5-134">Les applications qui utilisent de manière intensive le traitement des demandes asynchrones, ou qui ont de nombreuses requêtes à long terme bloquées sur les e/s réseau, tireront parti de l’augmentation de la limite par défaut dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a95e5-134">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="a95e5-135">`maxConcurrentRequestsPerCPU`La définition de la valeur zéro désactive l’utilisation de threads managés pour le traitement des demandes ASP.net.</span><span class="sxs-lookup"><span data-stu-id="a95e5-135">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="a95e5-136">Quand une application s’exécute dans un pool d’applications IIS, les demandes sont conservées sur le thread d’e/s IIS et par conséquent, la concurrence est limitée par les paramètres de thread IIS.</span><span class="sxs-lookup"><span data-stu-id="a95e5-136">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="a95e5-137">Le `requestQueueLimit` paramètre fonctionne de la même façon que l' `requestQueueLimit` attribut de l’élément [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) , qui est défini dans les fichiers Web. config pour les applications ASP.net.</span><span class="sxs-lookup"><span data-stu-id="a95e5-137">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="a95e5-138">Toutefois, le `requestQueueLimit` paramètre dans un fichier Aspnet. config remplace le `requestQueueLimit` paramètre dans un fichier Web. config.</span><span class="sxs-lookup"><span data-stu-id="a95e5-138">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="a95e5-139">En d’autres termes, si les deux attributs sont définis (par défaut, cela est vrai), le `requestQueueLimit` paramètre dans le fichier Aspnet. config est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="a95e5-139">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a95e5-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="a95e5-140">Example</span></span>  

<span data-ttu-id="a95e5-141">L’exemple suivant montre comment configurer le comportement à l’ensemble du processus ASP.NET dans le fichier Aspnet. config dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="a95e5-141">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="a95e5-142">L’application est hébergée dans un pool d’applications IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a95e5-142">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="a95e5-143">IIS 7,0 s’exécute en mode intégré.</span><span class="sxs-lookup"><span data-stu-id="a95e5-143">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="a95e5-144">L’application utilise le .NET Framework 3,5 SP1 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a95e5-144">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="a95e5-145">Les valeurs de l’exemple sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="a95e5-145">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="a95e5-146">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="a95e5-146">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a95e5-147">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="a95e5-147">Namespace</span></span>||  
|<span data-ttu-id="a95e5-148">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="a95e5-148">Schema Name</span></span>||  
|<span data-ttu-id="a95e5-149">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="a95e5-149">Validation File</span></span>||  
|<span data-ttu-id="a95e5-150">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="a95e5-150">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="a95e5-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a95e5-151">See also</span></span>

- [<span data-ttu-id="a95e5-152">\<system.web>, Élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="a95e5-152">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
