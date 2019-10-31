---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: 6a418fc546313b74bb965a0b223eca9c2e5acc08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115797"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="91236-102">\<élément relativeBindForResources ></span><span class="sxs-lookup"><span data-stu-id="91236-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="91236-103">Optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="91236-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91236-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91236-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="91236-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="91236-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources** ></span><span class="sxs-lookup"><span data-stu-id="91236-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91236-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91236-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91236-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="91236-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91236-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="91236-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91236-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="91236-110">Attributes</span></span>  
  
|<span data-ttu-id="91236-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="91236-111">Attribute</span></span>|<span data-ttu-id="91236-112">Description</span><span class="sxs-lookup"><span data-stu-id="91236-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="91236-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="91236-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="91236-114">Spécifie si le common language runtime optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="91236-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="91236-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="91236-116">valeur</span><span class="sxs-lookup"><span data-stu-id="91236-116">Value</span></span>|<span data-ttu-id="91236-117">Description</span><span class="sxs-lookup"><span data-stu-id="91236-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="91236-118">Le runtime n’optimise pas la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="91236-119">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="91236-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="91236-120">Le runtime optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91236-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="91236-121">Child Elements</span></span>  
 <span data-ttu-id="91236-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="91236-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91236-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="91236-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91236-124">Élément</span><span class="sxs-lookup"><span data-stu-id="91236-124">Element</span></span>|<span data-ttu-id="91236-125">Description</span><span class="sxs-lookup"><span data-stu-id="91236-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91236-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91236-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="91236-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="91236-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91236-128">Notes</span><span class="sxs-lookup"><span data-stu-id="91236-128">Remarks</span></span>  
 <span data-ttu-id="91236-129">En général, Gestionnaire des ressources sondes pour les ressources, comme indiqué dans la rubrique [empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="91236-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="91236-130">Cela signifie que lorsque Gestionnaire des ressources détecte une version localisée particulière d’une ressource, il peut regarder dans le Global Assembly Cache, Rechercher dans un dossier propre à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblys satellites et déclencher l’opération événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91236-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="91236-131">L’élément `<relativeBindForResources>` optimise la manière dont Gestionnaire des ressources sondes pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="91236-132">Elle peut améliorer les performances lors de la détection des ressources dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="91236-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="91236-133">Lorsque l’assembly satellite est déployé dans le même emplacement que l’assembly de code.</span><span class="sxs-lookup"><span data-stu-id="91236-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="91236-134">En d’autres termes, si l’assembly de code est installé dans le Global Assembly Cache, les assemblys satellites doivent également être installés ici.</span><span class="sxs-lookup"><span data-stu-id="91236-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="91236-135">Si l’assembly de code est installé dans la base de code de l’application, les assemblys satellites doivent également être installés dans un dossier propre à la culture dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="91236-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="91236-136">Lorsque Windows Installer n’est pas utilisé ou est rarement utilisé pour l’installation à la demande d’assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="91236-137">Lorsque le code d’application ne gère pas l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91236-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="91236-138">La définition de l’attribut `enabled` de l’élément `<relativeBindForResources>` sur `true` optimise la sonde de Gestionnaire des ressources pour les assemblys satellites comme suit :</span><span class="sxs-lookup"><span data-stu-id="91236-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="91236-139">Elle utilise l’emplacement de l’assembly de code parent pour détecter l’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="91236-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="91236-140">Il n’interroge pas Windows Installer pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="91236-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="91236-141">Elle ne déclenche pas l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91236-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91236-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91236-142">See also</span></span>

- [<span data-ttu-id="91236-143">Empaquetage et déploiement de ressources</span><span class="sxs-lookup"><span data-stu-id="91236-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="91236-144">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="91236-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="91236-145">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="91236-145">Configuration File Schema</span></span>](../index.md)
