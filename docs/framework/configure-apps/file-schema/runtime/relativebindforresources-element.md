---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: daf576488e38bed28c7c0e5222bc053659372ff0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183999"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="63221-102">Élément \<relativeBindForResources></span><span class="sxs-lookup"><span data-stu-id="63221-102">\<relativeBindForResources> Element</span></span>

<span data-ttu-id="63221-103">Optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="63221-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63221-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63221-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="63221-105">Attributes and Elements</span></span>  

 <span data-ttu-id="63221-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="63221-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63221-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="63221-107">Attributes</span></span>  
  
|<span data-ttu-id="63221-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="63221-108">Attribute</span></span>|<span data-ttu-id="63221-109">Description</span><span class="sxs-lookup"><span data-stu-id="63221-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="63221-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="63221-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="63221-111">Spécifie si le common language runtime optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="63221-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="63221-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="63221-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="63221-113">Value</span></span>|<span data-ttu-id="63221-114">Description</span><span class="sxs-lookup"><span data-stu-id="63221-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="63221-115">Le runtime n’optimise pas la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="63221-116">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63221-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="63221-117">Le runtime optimise la sonde pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63221-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63221-118">Child Elements</span></span>  

 <span data-ttu-id="63221-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="63221-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63221-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63221-120">Parent Elements</span></span>  
  
|<span data-ttu-id="63221-121">Élément</span><span class="sxs-lookup"><span data-stu-id="63221-121">Element</span></span>|<span data-ttu-id="63221-122">Description</span><span class="sxs-lookup"><span data-stu-id="63221-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="63221-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63221-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="63221-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="63221-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63221-125">Notes</span><span class="sxs-lookup"><span data-stu-id="63221-125">Remarks</span></span>  

 <span data-ttu-id="63221-126">En général, Gestionnaire des ressources sondes pour les ressources, comme indiqué dans la rubrique [empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="63221-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="63221-127">Cela signifie que lorsque Gestionnaire des ressources détecte une version localisée particulière d’une ressource, il peut regarder dans le Global Assembly Cache, Rechercher dans un dossier propre à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblys satellites et déclencher l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="63221-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="63221-128">L' `<relativeBindForResources>` élément optimise la façon dont gestionnaire des ressources sondes pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="63221-129">Elle peut améliorer les performances lors de la détection des ressources dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="63221-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="63221-130">Lorsque l’assembly satellite est déployé dans le même emplacement que l’assembly de code.</span><span class="sxs-lookup"><span data-stu-id="63221-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="63221-131">En d’autres termes, si l’assembly de code est installé dans le Global Assembly Cache, les assemblys satellites doivent également être installés ici.</span><span class="sxs-lookup"><span data-stu-id="63221-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="63221-132">Si l’assembly de code est installé dans la base de code de l’application, les assemblys satellites doivent également être installés dans un dossier propre à la culture dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="63221-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="63221-133">Lorsque Windows Installer n’est pas utilisé ou est rarement utilisé pour l’installation à la demande d’assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="63221-134">Lorsque le code d’application ne gère pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="63221-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="63221-135">La définition `enabled` de l’attribut de l' `<relativeBindForResources>` élément pour `true` optimiser la sonde de gestionnaire des ressources pour les assemblys satellites comme suit :</span><span class="sxs-lookup"><span data-stu-id="63221-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="63221-136">Elle utilise l’emplacement de l’assembly de code parent pour détecter l’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="63221-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="63221-137">Il n’interroge pas Windows Installer pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="63221-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="63221-138">Elle ne déclenche pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.</span><span class="sxs-lookup"><span data-stu-id="63221-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63221-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63221-139">See also</span></span>

- [<span data-ttu-id="63221-140">Empaquetage et déploiement de ressources</span><span class="sxs-lookup"><span data-stu-id="63221-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="63221-141">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="63221-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="63221-142">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="63221-142">Configuration File Schema</span></span>](../index.md)
