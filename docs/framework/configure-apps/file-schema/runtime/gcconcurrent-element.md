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
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969233"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="ddc18-102">\<élément gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="ddc18-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="ddc18-103">Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="ddc18-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="ddc18-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ddc18-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="ddc18-105">&nbsp;&nbsp;[\<runtime >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ddc18-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="ddc18-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="ddc18-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="ddc18-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddc18-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ddc18-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ddc18-108">Attributes and elements</span></span>

<span data-ttu-id="ddc18-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ddc18-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ddc18-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ddc18-110">Attributes</span></span>

|<span data-ttu-id="ddc18-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="ddc18-111">Attribute</span></span>|<span data-ttu-id="ddc18-112">Description</span><span class="sxs-lookup"><span data-stu-id="ddc18-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ddc18-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ddc18-113">Required attribute.</span></span><br /><br /><span data-ttu-id="ddc18-114">Spécifie si le runtime exécute l’opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="ddc18-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="ddc18-115">attribut activé</span><span class="sxs-lookup"><span data-stu-id="ddc18-115">enabled attribute</span></span>

|<span data-ttu-id="ddc18-116">valeur</span><span class="sxs-lookup"><span data-stu-id="ddc18-116">Value</span></span>|<span data-ttu-id="ddc18-117">Description</span><span class="sxs-lookup"><span data-stu-id="ddc18-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ddc18-118">Ne s’exécute pas garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="ddc18-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="ddc18-119">Exécute l'opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="ddc18-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="ddc18-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ddc18-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ddc18-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ddc18-121">Child elements</span></span>

<span data-ttu-id="ddc18-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="ddc18-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ddc18-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ddc18-123">Parent elements</span></span>

|<span data-ttu-id="ddc18-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ddc18-124">Element</span></span>|<span data-ttu-id="ddc18-125">Description</span><span class="sxs-lookup"><span data-stu-id="ddc18-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ddc18-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddc18-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ddc18-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ddc18-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ddc18-128">Notes</span><span class="sxs-lookup"><span data-stu-id="ddc18-128">Remarks</span></span>

<span data-ttu-id="ddc18-129">Avant le .NET Framework 4, la station de travail garbage collection prenait en charge garbage collection simultanés, qui effectuaient garbage collection en arrière-plan sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="ddc18-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="ddc18-130">Dans .NET Framework 4, la garbage collection simultanée a été remplacée par le GC d’arrière-plan, qui exécute également garbage collection en arrière-plan sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="ddc18-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="ddc18-131">À compter de .NET Framework 4,5, la collecte d’arrière-plan est disponible dans le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="ddc18-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="ddc18-132">L’élément **gcConcurrent** contrôle si le runtime effectue une exécution simultanée ou d’arrière-plan garbage collection, s’il est disponible, ou s’il effectue des garbage collection au premier plan.</span><span class="sxs-lookup"><span data-stu-id="ddc18-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="ddc18-133">Pour désactiver les garbage collection d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="ddc18-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="ddc18-134">À partir de .NET Framework 4, la garbage collection simultanée est remplacée par l’garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ddc18-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="ddc18-135">Les termes *simultanés* et en *arrière-plan* sont utilisés de manière interchangeable dans la documentation de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddc18-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="ddc18-136">Pour désactiver les garbage collection d’arrière-plan, utilisez l’élément **gcConcurrent** , comme indiqué dans cet article.</span><span class="sxs-lookup"><span data-stu-id="ddc18-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="ddc18-137">Par défaut, le runtime utilise le garbage collection simultané ou d’arrière-plan, dont la latence est optimisée.</span><span class="sxs-lookup"><span data-stu-id="ddc18-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="ddc18-138">Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ddc18-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="ddc18-139">Si vous définissez l’attribut `enabled` de l’élément **gcConcurrent** sur `false`, le runtime utilise un garbage collection non simultané, qui est optimisé pour le débit.</span><span class="sxs-lookup"><span data-stu-id="ddc18-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="ddc18-140">Le fichier de configuration suivant désactive les garbage collection d’arrière-plan :</span><span class="sxs-lookup"><span data-stu-id="ddc18-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="ddc18-141">S’il existe un paramètre **gcConcurrentSetting** dans le fichier de configuration de l’ordinateur, il définit la valeur par défaut pour toutes les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddc18-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="ddc18-142">Ce paramètre se substitue au paramètre du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="ddc18-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="ddc18-143">Pour plus d’informations sur les garbage collection simultanés et d’arrière-plan, consultez les sections [simultanées garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), de [station de travail en arrière-plan garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)et de [serveur d’arrière-plan garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) dans l’article [notions de base de l’opération garbage collection](../../../../standard/garbage-collection/fundamentals.md) .</span><span class="sxs-lookup"><span data-stu-id="ddc18-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="ddc18-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="ddc18-144">Example</span></span>

<span data-ttu-id="ddc18-145">L’exemple suivant active les garbage collection d’arrière-plan :</span><span class="sxs-lookup"><span data-stu-id="ddc18-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ddc18-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddc18-146">See also</span></span>

- [<span data-ttu-id="ddc18-147">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ddc18-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ddc18-148">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ddc18-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ddc18-149">Principes de base du Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="ddc18-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
