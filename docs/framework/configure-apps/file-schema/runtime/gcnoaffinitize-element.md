---
title: Élément GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978374"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="551c1-102">\<élément GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="551c1-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="551c1-103">Spécifie s’il faut ou non affinité les threads GC du serveur avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="551c1-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

<span data-ttu-id="551c1-104">\<> de configuration </span><span class="sxs-lookup"><span data-stu-id="551c1-104">\<configuration></span></span>\
<span data-ttu-id="551c1-105">&nbsp;&nbsp;\<Runtime > </span><span class="sxs-lookup"><span data-stu-id="551c1-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="551c1-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="551c1-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize></span></span>

## <a name="syntax"></a><span data-ttu-id="551c1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="551c1-107">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="551c1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="551c1-108">Attributes and elements</span></span>

<span data-ttu-id="551c1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="551c1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="551c1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="551c1-110">Attributes</span></span>

|<span data-ttu-id="551c1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="551c1-111">Attribute</span></span>|<span data-ttu-id="551c1-112">Description</span><span class="sxs-lookup"><span data-stu-id="551c1-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="551c1-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="551c1-113">Required attribute.</span></span><br /><br /><span data-ttu-id="551c1-114">Spécifie si les threads/segments de mémoire GC du serveur sont affinités avec les processeurs disponibles sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="551c1-114">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="551c1-115">attribut activé</span><span class="sxs-lookup"><span data-stu-id="551c1-115">enabled attribute</span></span>

|<span data-ttu-id="551c1-116">valeur</span><span class="sxs-lookup"><span data-stu-id="551c1-116">Value</span></span>|<span data-ttu-id="551c1-117">Description</span><span class="sxs-lookup"><span data-stu-id="551c1-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="551c1-118">Threads GC affinité entre Server avec UC.</span><span class="sxs-lookup"><span data-stu-id="551c1-118">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="551c1-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="551c1-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="551c1-120">Ne affinité pas les threads GC du serveur avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="551c1-120">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="551c1-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="551c1-121">Child elements</span></span>

<span data-ttu-id="551c1-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="551c1-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="551c1-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="551c1-123">Parent elements</span></span>

|<span data-ttu-id="551c1-124">Élément</span><span class="sxs-lookup"><span data-stu-id="551c1-124">Element</span></span>|<span data-ttu-id="551c1-125">Description</span><span class="sxs-lookup"><span data-stu-id="551c1-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="551c1-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="551c1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="551c1-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="551c1-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="551c1-128">Notes</span><span class="sxs-lookup"><span data-stu-id="551c1-128">Remarks</span></span>

<span data-ttu-id="551c1-129">Par défaut, les threads GC de serveur sont affinités avec leurs UC respectives.</span><span class="sxs-lookup"><span data-stu-id="551c1-129">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="551c1-130">Chacun des processeurs disponibles du système a son propre tas GC et son propre thread.</span><span class="sxs-lookup"><span data-stu-id="551c1-130">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="551c1-131">Il s’agit généralement du paramètre préféré, car il optimise l’utilisation du cache.</span><span class="sxs-lookup"><span data-stu-id="551c1-131">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="551c1-132">À partir de .NET Framework 4.6.2, en affectant à l’attribut `enabled` de l’élément **GCNoAffinitize** la valeur `false`, vous pouvez spécifier que les threads et les processeurs de garbage collection du serveur ne doivent pas être étroitement couplés.</span><span class="sxs-lookup"><span data-stu-id="551c1-132">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `false`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="551c1-133">Vous pouvez spécifier l’élément de configuration **GCNoAffinitize** seul pour ne pas affinité les threads GC du serveur avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="551c1-133">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="551c1-134">Vous pouvez également l’utiliser avec l’élément [GCHeapCount](gcheapcount-element.md) pour contrôler le nombre de tas GC et de threads utilisés par une application.</span><span class="sxs-lookup"><span data-stu-id="551c1-134">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="551c1-135">Si l’attribut `enabled` de l’élément **GCNoAffinitize** est `false` (sa valeur par défaut), vous pouvez également utiliser l’élément [GCHeapCount](gcheapcount-element.md) pour spécifier le nombre de threads GC et de tas, ainsi que l’élément [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pour spécifier les processeurs sur lesquels les threads GC et les tas sont affinité.</span><span class="sxs-lookup"><span data-stu-id="551c1-135">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="551c1-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="551c1-136">Example</span></span>

<span data-ttu-id="551c1-137">L’exemple suivant ne prend pas en affinité les threads GC du serveur :</span><span class="sxs-lookup"><span data-stu-id="551c1-137">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="551c1-138">L’exemple suivant n’affinité pas les threads GC du serveur et limite le nombre de tas/threads GC à 10 :</span><span class="sxs-lookup"><span data-stu-id="551c1-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="551c1-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="551c1-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="551c1-140">Élément GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="551c1-140">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="551c1-141">Élément GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="551c1-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="551c1-142">Notions de base du garbage collection</span><span class="sxs-lookup"><span data-stu-id="551c1-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="551c1-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="551c1-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="551c1-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="551c1-144">Configuration File Schema</span></span>](../index.md)
