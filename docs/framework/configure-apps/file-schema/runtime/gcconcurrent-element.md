---
title: Élément gcConcurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102916"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="2b5a9-102">\<gcConcurrent>, élément</span><span class="sxs-lookup"><span data-stu-id="2b5a9-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="2b5a9-103">Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="2b5a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b5a9-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b5a9-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2b5a9-105">Attributes and elements</span></span>

<span data-ttu-id="2b5a9-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b5a9-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="2b5a9-107">Attributes</span></span>

|<span data-ttu-id="2b5a9-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="2b5a9-108">Attribute</span></span>|<span data-ttu-id="2b5a9-109">Description</span><span class="sxs-lookup"><span data-stu-id="2b5a9-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2b5a9-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-110">Required attribute.</span></span><br /><br /><span data-ttu-id="2b5a9-111">Spécifie si le runtime exécute l’opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="2b5a9-112">attribut activé</span><span class="sxs-lookup"><span data-stu-id="2b5a9-112">enabled attribute</span></span>

|<span data-ttu-id="2b5a9-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="2b5a9-113">Value</span></span>|<span data-ttu-id="2b5a9-114">Description</span><span class="sxs-lookup"><span data-stu-id="2b5a9-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2b5a9-115">Ne s’exécute pas garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="2b5a9-116">Exécute l'opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="2b5a9-117">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2b5a9-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2b5a9-118">Child elements</span></span>

<span data-ttu-id="2b5a9-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b5a9-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2b5a9-120">Parent elements</span></span>

|<span data-ttu-id="2b5a9-121">Élément</span><span class="sxs-lookup"><span data-stu-id="2b5a9-121">Element</span></span>|<span data-ttu-id="2b5a9-122">Description</span><span class="sxs-lookup"><span data-stu-id="2b5a9-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2b5a9-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2b5a9-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b5a9-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="2b5a9-125">Remarks</span></span>

<span data-ttu-id="2b5a9-126">Avant le .NET Framework 4, la station de travail garbage collection prenait en charge garbage collection simultanés, qui effectuaient garbage collection en arrière-plan sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2b5a9-127">Dans .NET Framework 4, la garbage collection simultanée a été remplacée par le GC d’arrière-plan, qui exécute également garbage collection en arrière-plan sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2b5a9-128">À compter de .NET Framework 4,5, la collecte d’arrière-plan est disponible dans le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="2b5a9-129">L’élément **gcConcurrent** contrôle si le runtime effectue une exécution simultanée ou d’arrière-plan garbage collection, s’il est disponible, ou s’il effectue des garbage collection au premier plan.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="2b5a9-130">Pour désactiver les garbage collection d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="2b5a9-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="2b5a9-131">À partir de .NET Framework 4, la garbage collection simultanée est remplacée par l’garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="2b5a9-132">Les termes *simultanés* et en *arrière-plan* sont utilisés de manière interchangeable dans la documentation de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="2b5a9-133">Pour désactiver les garbage collection d’arrière-plan, utilisez l’élément **gcConcurrent** , comme indiqué dans cet article.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="2b5a9-134">Par défaut, le runtime utilise le garbage collection simultané ou d’arrière-plan, dont la latence est optimisée.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="2b5a9-135">Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="2b5a9-136">Si vous affectez `enabled` à l’attribut de l’élément **gcConcurrent** la valeur `false` , le runtime utilise des garbage collection non simultanées, ce qui est optimisé pour le débit.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="2b5a9-137">Le fichier de configuration suivant désactive les garbage collection d’arrière-plan :</span><span class="sxs-lookup"><span data-stu-id="2b5a9-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="2b5a9-138">S’il existe un paramètre **gcConcurrentSetting** dans le fichier de configuration de l’ordinateur, il définit la valeur par défaut pour toutes les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="2b5a9-139">Ce paramètre se substitue au paramètre du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="2b5a9-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="2b5a9-140">Pour plus d’informations sur les garbage collection simultanés et d’arrière-plan, consultez [garbage collection d’arrière-plan](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="2b5a9-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="2b5a9-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b5a9-141">Example</span></span>

<span data-ttu-id="2b5a9-142">L’exemple suivant active les garbage collection d’arrière-plan :</span><span class="sxs-lookup"><span data-stu-id="2b5a9-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2b5a9-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b5a9-143">See also</span></span>

- [<span data-ttu-id="2b5a9-144">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="2b5a9-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b5a9-145">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2b5a9-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2b5a9-146">Principes de base du Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="2b5a9-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
