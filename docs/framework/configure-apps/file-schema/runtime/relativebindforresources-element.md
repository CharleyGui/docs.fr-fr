---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153904"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="e7af7-102">\<relativeBindForResources> Element</span><span class="sxs-lookup"><span data-stu-id="e7af7-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="e7af7-103">Optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="e7af7-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7af7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7af7-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7af7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e7af7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span><span class="sxs-lookup"><span data-stu-id="e7af7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7af7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7af7-107">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7af7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7af7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e7af7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7af7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7af7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7af7-110">Attributes</span></span>  
  
|<span data-ttu-id="e7af7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7af7-111">Attribute</span></span>|<span data-ttu-id="e7af7-112">Description</span><span class="sxs-lookup"><span data-stu-id="e7af7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e7af7-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e7af7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e7af7-114">Précise si le temps d’exécution de langage commun optimise la sonde pour les assemblages satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e7af7-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="e7af7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e7af7-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="e7af7-116">Value</span></span>|<span data-ttu-id="e7af7-117">Description</span><span class="sxs-lookup"><span data-stu-id="e7af7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e7af7-118">Le temps d’exécution n’optimise pas la sonde pour les assemblages de satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="e7af7-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e7af7-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="e7af7-120">Le temps d’exécution optimise la sonde pour les assemblages de satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7af7-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7af7-121">Child Elements</span></span>  
 <span data-ttu-id="e7af7-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7af7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7af7-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7af7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e7af7-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e7af7-124">Element</span></span>|<span data-ttu-id="e7af7-125">Description</span><span class="sxs-lookup"><span data-stu-id="e7af7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e7af7-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7af7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e7af7-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="e7af7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7af7-128">Notes </span><span class="sxs-lookup"><span data-stu-id="e7af7-128">Remarks</span></span>  
 <span data-ttu-id="e7af7-129">En général, le gestionnaire des ressources sonde les ressources, comme le documente le sujet [des ressources d’emballage et de déploiement.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)</span><span class="sxs-lookup"><span data-stu-id="e7af7-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="e7af7-130">Cela signifie que lorsque Resource Manager sonde pour une version localisée particulière d’une ressource, il peut regarder dans le cache d’assemblage global, regarder dans <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> un dossier spécifique à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblages de satellites, et élever l’événement.</span><span class="sxs-lookup"><span data-stu-id="e7af7-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="e7af7-131">L’élément `<relativeBindForResources>` optimise la façon dont le gestionnaire des ressources sonde les assemblages de satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="e7af7-132">Il peut améliorer les performances lors de l’examen des ressources dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7af7-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="e7af7-133">Lorsque l’assemblage satellite est déployé au même endroit que l’assemblage du code.</span><span class="sxs-lookup"><span data-stu-id="e7af7-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="e7af7-134">En d’autres termes, si l’assemblage de code est installé dans le cache d’assemblage global, les assemblages satellites doivent également y être installés.</span><span class="sxs-lookup"><span data-stu-id="e7af7-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="e7af7-135">Si l’assemblage de code est installé dans la base de code de l’application, les assemblages satellites doivent également être installés dans un dossier spécifique à la culture dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="e7af7-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="e7af7-136">Lorsque Windows Install n’est pas utilisé ou n’est utilisé que rarement pour l’installation à la demande d’assemblages satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="e7af7-137">Lorsque le code d’application ne gère pas l’événement. <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e7af7-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="e7af7-138">Définir `enabled` l’attribut `<relativeBindForResources>` de `true` l’élément pour optimiser la sonde de Resource Manager pour les assemblages satellitaires comme suit :</span><span class="sxs-lookup"><span data-stu-id="e7af7-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="e7af7-139">Il utilise l’emplacement de l’assemblage de code parent pour sonder l’assemblage du satellite.</span><span class="sxs-lookup"><span data-stu-id="e7af7-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="e7af7-140">Il ne demande pas Windows Install pour les assemblages de satellites.</span><span class="sxs-lookup"><span data-stu-id="e7af7-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="e7af7-141">Il ne soulève <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pas l’événement.</span><span class="sxs-lookup"><span data-stu-id="e7af7-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7af7-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7af7-142">See also</span></span>

- [<span data-ttu-id="e7af7-143">Packaging and Deploying Resources</span><span class="sxs-lookup"><span data-stu-id="e7af7-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="e7af7-144">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="e7af7-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7af7-145">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="e7af7-145">Configuration File Schema</span></span>](../index.md)
