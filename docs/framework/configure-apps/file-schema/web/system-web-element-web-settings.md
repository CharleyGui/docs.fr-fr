---
title: <system.web>, élément (paramètres web)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 41a638afa93e605221d5ef8172e243b1c61676bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941385"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="f65ee-102">\<System. Web >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="f65ee-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="f65ee-103">Contient des informations sur la façon dont la couche d’hébergement ASP.NET gère le comportement à l’ensemble du processus.</span><span class="sxs-lookup"><span data-stu-id="f65ee-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="f65ee-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f65ee-104">\<configuration></span></span>  
<span data-ttu-id="f65ee-105">\<System. Web >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="f65ee-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65ee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f65ee-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f65ee-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f65ee-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f65ee-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f65ee-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f65ee-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f65ee-109">Attributes</span></span>  
 <span data-ttu-id="f65ee-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f65ee-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f65ee-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f65ee-111">Child Elements</span></span>  
  
|<span data-ttu-id="f65ee-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f65ee-112">Element</span></span>|<span data-ttu-id="f65ee-113">Description</span><span class="sxs-lookup"><span data-stu-id="f65ee-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f65ee-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="f65ee-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="f65ee-115">Spécifie les paramètres de configuration des pools d’applications IIS dans un fichier Aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="f65ee-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f65ee-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f65ee-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f65ee-117">Élément</span><span class="sxs-lookup"><span data-stu-id="f65ee-117">Element</span></span>|<span data-ttu-id="f65ee-118">Description</span><span class="sxs-lookup"><span data-stu-id="f65ee-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f65ee-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f65ee-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="f65ee-120">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f65ee-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f65ee-121">Notes</span><span class="sxs-lookup"><span data-stu-id="f65ee-121">Remarks</span></span>  
 <span data-ttu-id="f65ee-122">L' `system.web` élément et son élément `applicationPool` enfant ont été ajoutés au .NET Framework à partir de .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="f65ee-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="f65ee-123">Lorsque vous exécutez IIS 7,0 ou des versions ultérieures en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les threads et la façon dont il met en file d’attente les demandes lorsque ASP.NET est hébergé dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="f65ee-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="f65ee-124">Si vous exécutez IIS 7,0 ou des versions ultérieures en mode classique ou ISAPI, ces paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="f65ee-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f65ee-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="f65ee-125">Example</span></span>  
 <span data-ttu-id="f65ee-126">L’exemple suivant montre comment configurer le comportement à l’ensemble du processus ASP.NET dans le fichier Aspnet. config lorsque ASP.NET est hébergé dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="f65ee-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="f65ee-127">L’exemple suppose qu’IIS s’exécute en mode intégré et que l’application utilise le .NET Framework 3,5 SP1 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f65ee-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="f65ee-128">Ce comportement ne se produit pas dans les versions de la .NET Framework antérieures à la .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="f65ee-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="f65ee-129">Les valeurs de l’exemple sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f65ee-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="f65ee-130">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="f65ee-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f65ee-131">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="f65ee-131">Namespace</span></span>||  
|<span data-ttu-id="f65ee-132">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="f65ee-132">Schema Name</span></span>||  
|<span data-ttu-id="f65ee-133">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="f65ee-133">Validation File</span></span>||  
|<span data-ttu-id="f65ee-134">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="f65ee-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="f65ee-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f65ee-135">See also</span></span>

- [<span data-ttu-id="f65ee-136">\<applicationPool >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="f65ee-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
