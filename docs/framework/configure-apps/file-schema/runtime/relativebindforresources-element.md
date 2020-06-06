---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153904"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="b12cd-102">Élément \<relativeBindForResources></span><span class="sxs-lookup"><span data-stu-id="b12cd-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="b12cd-103">Optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="b12cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b12cd-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b12cd-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b12cd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b12cd-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b12cd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b12cd-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b12cd-107">Attributes</span></span>  
  
|<span data-ttu-id="b12cd-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b12cd-108">Attribute</span></span>|<span data-ttu-id="b12cd-109">Description</span><span class="sxs-lookup"><span data-stu-id="b12cd-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b12cd-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b12cd-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b12cd-111">Spécifie si le common language runtime optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b12cd-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="b12cd-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="b12cd-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="b12cd-113">Value</span></span>|<span data-ttu-id="b12cd-114">Description</span><span class="sxs-lookup"><span data-stu-id="b12cd-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b12cd-115">Le runtime n’optimise pas la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="b12cd-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b12cd-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="b12cd-117">Le runtime optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b12cd-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b12cd-118">Child Elements</span></span>  
 <span data-ttu-id="b12cd-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b12cd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b12cd-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b12cd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b12cd-121">Élément</span><span class="sxs-lookup"><span data-stu-id="b12cd-121">Element</span></span>|<span data-ttu-id="b12cd-122">Description</span><span class="sxs-lookup"><span data-stu-id="b12cd-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b12cd-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b12cd-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b12cd-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="b12cd-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b12cd-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="b12cd-125">Remarks</span></span>  
 <span data-ttu-id="b12cd-126">En général, Gestionnaire des ressources sondes pour les ressources, comme indiqué dans la rubrique [empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="b12cd-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="b12cd-127">Cela signifie que lorsque Gestionnaire des ressources détecte une version localisée particulière d’une ressource, il peut regarder dans le Global Assembly Cache, Rechercher dans un dossier propre à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblys satellites et déclencher l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="b12cd-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="b12cd-128">L' `<relativeBindForResources>` élément optimise la façon dont gestionnaire des ressources sondes pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="b12cd-129">Elle peut améliorer les performances lors de la détection des ressources dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b12cd-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="b12cd-130">Lorsque l’assembly satellite est déployé dans le même emplacement que l’assembly de code.</span><span class="sxs-lookup"><span data-stu-id="b12cd-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="b12cd-131">En d’autres termes, si l’assembly de code est installé dans le Global Assembly Cache, les assemblys satellites doivent également être installés ici.</span><span class="sxs-lookup"><span data-stu-id="b12cd-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="b12cd-132">Si l’assembly de code est installé dans la base de code de l’application, les assemblys satellites doivent également être installés dans un dossier propre à la culture dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="b12cd-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="b12cd-133">Lorsque Windows Installer n’est pas utilisé ou est rarement utilisé pour l’installation à la demande d’assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="b12cd-134">Lorsque le code d’application ne gère pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="b12cd-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="b12cd-135">La définition `enabled` de l’attribut de l' `<relativeBindForResources>` élément pour `true` optimiser la sonde de gestionnaire des ressources pour les assemblys satellites comme suit :</span><span class="sxs-lookup"><span data-stu-id="b12cd-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="b12cd-136">Elle utilise l’emplacement de l’assembly de code parent pour détecter l’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="b12cd-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="b12cd-137">Il n’interroge pas Windows Installer pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="b12cd-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="b12cd-138">Elle ne déclenche pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="b12cd-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12cd-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b12cd-139">See also</span></span>

- [<span data-ttu-id="b12cd-140">Packaging and Deploying Resources</span><span class="sxs-lookup"><span data-stu-id="b12cd-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="b12cd-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="b12cd-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b12cd-142">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b12cd-142">Configuration File Schema</span></span>](../index.md)
