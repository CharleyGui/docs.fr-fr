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
ms.openlocfilehash: c8b01ec217fc1b6b91ccf36c8667922b57f26852
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185585"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="5f5ea-102">\<system.web>, élément (paramètres web)</span><span class="sxs-lookup"><span data-stu-id="5f5ea-102">\<system.web> Element (Web Settings)</span></span>

<span data-ttu-id="5f5ea-103">Contient des informations sur la façon dont la couche d’hébergement ASP.NET gère le comportement à l’ensemble du processus.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="5f5ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f5ea-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f5ea-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5f5ea-105">Attributes and Elements</span></span>  

<span data-ttu-id="5f5ea-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f5ea-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5f5ea-107">Attributes</span></span>  

<span data-ttu-id="5f5ea-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f5ea-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5f5ea-109">Child Elements</span></span>  
  
|<span data-ttu-id="5f5ea-110">Élément</span><span class="sxs-lookup"><span data-stu-id="5f5ea-110">Element</span></span>|<span data-ttu-id="5f5ea-111">Description</span><span class="sxs-lookup"><span data-stu-id="5f5ea-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="5f5ea-112">Spécifie les paramètres de configuration des pools d’applications IIS dans un fichier aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f5ea-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5f5ea-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5f5ea-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5f5ea-114">Element</span></span>|<span data-ttu-id="5f5ea-115">Description</span><span class="sxs-lookup"><span data-stu-id="5f5ea-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="5f5ea-116">Spécifie l’élément racine dans chaque fichier de configuration utilisé par les applications common language runtime et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f5ea-117">Notes</span><span class="sxs-lookup"><span data-stu-id="5f5ea-117">Remarks</span></span>  

<span data-ttu-id="5f5ea-118">L' `system.web` élément et son `applicationPool` élément enfant ont été ajoutés au .NET Framework à partir de .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="5f5ea-119">Lorsque vous exécutez IIS 7,0 ou des versions ultérieures en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les threads et la façon dont il met en file d’attente les demandes lorsque ASP.NET est hébergé dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="5f5ea-120">Si vous exécutez IIS 7,0 ou des versions ultérieures en mode classique ou ISAPI, ces paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f5ea-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f5ea-121">Example</span></span>  

<span data-ttu-id="5f5ea-122">L’exemple suivant montre comment configurer le comportement à l’ensemble du processus ASP.NET dans le fichier aspnet.config lorsque ASP.NET est hébergé dans un pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="5f5ea-123">L’exemple suppose qu’IIS s’exécute en mode intégré et que l’application utilise le .NET Framework 3,5 SP1 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="5f5ea-124">Ce comportement ne se produit pas dans les versions de la .NET Framework antérieures à la .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="5f5ea-125">Les valeurs de l’exemple sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f5ea-125">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="5f5ea-126">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="5f5ea-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f5ea-127">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5f5ea-127">Namespace</span></span>||  
|<span data-ttu-id="5f5ea-128">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="5f5ea-128">Schema Name</span></span>||  
|<span data-ttu-id="5f5ea-129">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="5f5ea-129">Validation File</span></span>||  
|<span data-ttu-id="5f5ea-130">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="5f5ea-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="5f5ea-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f5ea-131">See also</span></span>

- [<span data-ttu-id="5f5ea-132">\<applicationPool> , Élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="5f5ea-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
