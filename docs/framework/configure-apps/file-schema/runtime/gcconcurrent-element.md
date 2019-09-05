---
title: Élément <gcConcurrent>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b2774c32b4ee3e67772f84d599ecc5dbeb6598b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252592"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="abc98-102">\<gcConcurrent >, élément</span><span class="sxs-lookup"><span data-stu-id="abc98-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="abc98-103">Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="abc98-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="abc98-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="abc98-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="abc98-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="abc98-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="abc98-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcConcurrent>**</span><span class="sxs-lookup"><span data-stu-id="abc98-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcConcurrent>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="abc98-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abc98-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abc98-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="abc98-108">Attributes and elements</span></span>

<span data-ttu-id="abc98-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="abc98-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="abc98-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="abc98-110">Attributes</span></span>

|<span data-ttu-id="abc98-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="abc98-111">Attribute</span></span>|<span data-ttu-id="abc98-112">Description</span><span class="sxs-lookup"><span data-stu-id="abc98-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="abc98-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="abc98-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="abc98-114">Spécifie si le runtime exécute l’opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="abc98-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="abc98-115">attribut activé</span><span class="sxs-lookup"><span data-stu-id="abc98-115">enabled attribute</span></span>

|<span data-ttu-id="abc98-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="abc98-116">Value</span></span>|<span data-ttu-id="abc98-117">Description</span><span class="sxs-lookup"><span data-stu-id="abc98-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="abc98-118">Ne s’exécute pas garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="abc98-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="abc98-119">Exécute l'opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="abc98-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="abc98-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="abc98-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="abc98-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="abc98-121">Child elements</span></span>

<span data-ttu-id="abc98-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="abc98-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="abc98-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="abc98-123">Parent elements</span></span>

|<span data-ttu-id="abc98-124">Élément</span><span class="sxs-lookup"><span data-stu-id="abc98-124">Element</span></span>|<span data-ttu-id="abc98-125">Description</span><span class="sxs-lookup"><span data-stu-id="abc98-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="abc98-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abc98-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="abc98-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="abc98-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="abc98-128">Notes</span><span class="sxs-lookup"><span data-stu-id="abc98-128">Remarks</span></span>

<span data-ttu-id="abc98-129">Dans les versions antérieures à .NET Framework 4, le garbage collection de station de travail prenait en charge le garbage collection simultané, qui exécutait l'opération garbage collection en arrière-plan sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="abc98-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="abc98-130">Dans .NET Framework 4, le garbage collection simultané a été remplacé par le garbage collection d'arrière-plan pour effectuer l'opération de la même manière.</span><span class="sxs-lookup"><span data-stu-id="abc98-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="abc98-131">Depuis .NET Framework 4.5, le garbage collection d'arrière-plan est disponible dans le garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="abc98-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="abc98-132">L' `<gcConcurrent>` élément contrôle si le runtime effectue une garbage collection simultanée ou d’arrière-plan, s’il est disponible, ou s’il effectue des garbage collection au premier plan.</span><span class="sxs-lookup"><span data-stu-id="abc98-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="abc98-133">Pour désactiver les garbage collection d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="abc98-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="abc98-134">Depuis .NET Framework 4, le garbage collection simultané est remplacé par le garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="abc98-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="abc98-135">Les termes *simultanés* et en *arrière-plan* sont utilisés de manière interchangeable dans la documentation de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abc98-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="abc98-136">Pour désactiver le garbage collection d'arrière-plan, utilisez l'élément `<gcConcurrent>` comme indiqué dans cet article.</span><span class="sxs-lookup"><span data-stu-id="abc98-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="abc98-137">Par défaut, le runtime utilise le garbage collection simultané ou d’arrière-plan, dont la latence est optimisée.</span><span class="sxs-lookup"><span data-stu-id="abc98-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="abc98-138">Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="abc98-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="abc98-139">Si vous définissez l’attribut `enabled` de l’élément `<gcConcurrent>` avec la valeur `false`, le runtime utilise le garbage collection non simultané, dont le débit est optimisé.</span><span class="sxs-lookup"><span data-stu-id="abc98-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="abc98-140">Le fichier de configuration suivant désactive le garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="abc98-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="abc98-141">S’il existe un `<gcConcurrentSetting>` paramètre dans le fichier de configuration de l’ordinateur, il définit la valeur par défaut pour toutes les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abc98-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="abc98-142">Ce paramètre se substitue au paramètre du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="abc98-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="abc98-143">Pour plus d’informations sur les garbage collection simultanés et d’arrière-plan, consultez la section [garbage collection simultanées](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) dans l’article [notions de base du garbage collection](../../../../standard/garbage-collection/fundamentals.md) .</span><span class="sxs-lookup"><span data-stu-id="abc98-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="abc98-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="abc98-144">Example</span></span>

<span data-ttu-id="abc98-145">L’exemple suivant active garbage collection simultanées :</span><span class="sxs-lookup"><span data-stu-id="abc98-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="abc98-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abc98-146">See also</span></span>

- [<span data-ttu-id="abc98-147">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="abc98-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="abc98-148">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="abc98-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="abc98-149">Principes de base du Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="abc98-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
