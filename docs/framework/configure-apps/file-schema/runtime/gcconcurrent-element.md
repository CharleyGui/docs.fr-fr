---
title: gc Élément courant
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
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102916"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="60543-102">\<gcConcurrent> élément</span><span class="sxs-lookup"><span data-stu-id="60543-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="60543-103">Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="60543-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="60543-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60543-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="60543-105">&nbsp;&nbsp;[\<>de temps d’exécution](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="60543-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="60543-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="60543-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="60543-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60543-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60543-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="60543-108">Attributes and elements</span></span>

<span data-ttu-id="60543-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="60543-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="60543-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="60543-110">Attributes</span></span>

|<span data-ttu-id="60543-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="60543-111">Attribute</span></span>|<span data-ttu-id="60543-112">Description</span><span class="sxs-lookup"><span data-stu-id="60543-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="60543-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="60543-113">Required attribute.</span></span><br /><br /><span data-ttu-id="60543-114">Spécifie si le runtime exécute l’opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="60543-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="60543-115">attribut activé</span><span class="sxs-lookup"><span data-stu-id="60543-115">enabled attribute</span></span>

|<span data-ttu-id="60543-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="60543-116">Value</span></span>|<span data-ttu-id="60543-117">Description</span><span class="sxs-lookup"><span data-stu-id="60543-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="60543-118">Il n’exécute pas la collecte des ordures en même temps.</span><span class="sxs-lookup"><span data-stu-id="60543-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="60543-119">Exécute l'opération garbage collection simultanément.</span><span class="sxs-lookup"><span data-stu-id="60543-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="60543-120">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="60543-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="60543-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="60543-121">Child elements</span></span>

<span data-ttu-id="60543-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="60543-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60543-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="60543-123">Parent elements</span></span>

|<span data-ttu-id="60543-124">Élément</span><span class="sxs-lookup"><span data-stu-id="60543-124">Element</span></span>|<span data-ttu-id="60543-125">Description</span><span class="sxs-lookup"><span data-stu-id="60543-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="60543-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="60543-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="60543-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="60543-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="60543-128">Notes</span><span class="sxs-lookup"><span data-stu-id="60543-128">Remarks</span></span>

<span data-ttu-id="60543-129">Avant .NET Framework 4, la collecte des ordures de poste de travail a soutenu la collecte simultanée des ordures, qui a effectué la collecte des ordures en arrière-plan sur un fil séparé.</span><span class="sxs-lookup"><span data-stu-id="60543-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="60543-130">Dans .NET Framework 4, la collecte simultanée des ordures a été remplacée par GC de fond, qui effectue également la collecte des ordures en arrière-plan sur un fil séparé.</span><span class="sxs-lookup"><span data-stu-id="60543-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="60543-131">À partir de .NET Framework 4.5, la collecte d’arrière-plan est devenue disponible dans la collecte des ordures serveur.</span><span class="sxs-lookup"><span data-stu-id="60543-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="60543-132">**L’élément gcConcurrent** contrôle si le temps d’exécution effectue la collecte des ordures simultanées ou de fond, s’il est disponible, ou s’il effectue la collecte des ordures au premier plan.</span><span class="sxs-lookup"><span data-stu-id="60543-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="60543-133">Désactiver la collecte des ordures de fond</span><span class="sxs-lookup"><span data-stu-id="60543-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="60543-134">À partir du cadre .NET 4, la collecte simultanée des ordures est remplacée par la collecte des ordures de fond.</span><span class="sxs-lookup"><span data-stu-id="60543-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="60543-135">Les termes *simultanés* et *les antécédents* sont utilisés de façon interchangeable dans la documentation du Cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="60543-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="60543-136">Pour désactiver la collecte des ordures de fond, utilisez **l’élément GCConcurrent,** tel que discuté dans cet article.</span><span class="sxs-lookup"><span data-stu-id="60543-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="60543-137">Par défaut, le runtime utilise le garbage collection simultané ou d’arrière-plan, dont la latence est optimisée.</span><span class="sxs-lookup"><span data-stu-id="60543-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="60543-138">Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="60543-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="60543-139">Si vous `enabled` définissez l’attribut de **l’élément gcConcurrent** à `false`, le temps d’exécution utilise la collecte des ordures non-concurrentes, qui est optimisée pour le débit.</span><span class="sxs-lookup"><span data-stu-id="60543-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="60543-140">Le fichier de configuration suivant désactive la collecte des ordures de fond :</span><span class="sxs-lookup"><span data-stu-id="60543-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="60543-141">S’il y a un paramètre **gcConcurrentSetting** dans le fichier de configuration de la machine, il définit la valeur par défaut pour toutes les applications cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="60543-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="60543-142">Ce paramètre se substitue au paramètre du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="60543-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="60543-143">Pour plus d’informations sur la collecte des ordures simultanées et de fond, voir [Collection d’ordures de fond](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="60543-143">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="60543-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="60543-144">Example</span></span>

<span data-ttu-id="60543-145">L’exemple suivant permet la collecte des ordures de fond :</span><span class="sxs-lookup"><span data-stu-id="60543-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="60543-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60543-146">See also</span></span>

- [<span data-ttu-id="60543-147">Paramètres de durée d’exécution Schema</span><span class="sxs-lookup"><span data-stu-id="60543-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="60543-148">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="60543-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="60543-149">Principes de base du Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="60543-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
