---
title: Élément GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84004736"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="ff684-102">\<GCNoAffinitize>, élément</span><span class="sxs-lookup"><span data-stu-id="ff684-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="ff684-103">Spécifie s’il faut ou non affinité les threads GC du serveur avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="ff684-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="ff684-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff684-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff684-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ff684-105">Attributes and elements</span></span>

<span data-ttu-id="ff684-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ff684-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff684-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff684-107">Attributes</span></span>

|<span data-ttu-id="ff684-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ff684-108">Attribute</span></span>|<span data-ttu-id="ff684-109">Description</span><span class="sxs-lookup"><span data-stu-id="ff684-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ff684-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ff684-110">Required attribute.</span></span><br /><br /><span data-ttu-id="ff684-111">Spécifie si les threads/segments de mémoire GC du serveur sont affinités avec les processeurs disponibles sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ff684-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="ff684-112">attribut activé</span><span class="sxs-lookup"><span data-stu-id="ff684-112">enabled attribute</span></span>

|<span data-ttu-id="ff684-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff684-113">Value</span></span>|<span data-ttu-id="ff684-114">Description</span><span class="sxs-lookup"><span data-stu-id="ff684-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ff684-115">Threads GC affinité entre Server avec UC.</span><span class="sxs-lookup"><span data-stu-id="ff684-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="ff684-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ff684-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="ff684-117">Ne affinité pas les threads GC du serveur avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="ff684-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ff684-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff684-118">Child elements</span></span>

<span data-ttu-id="ff684-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ff684-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ff684-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff684-120">Parent elements</span></span>

|<span data-ttu-id="ff684-121">Élément</span><span class="sxs-lookup"><span data-stu-id="ff684-121">Element</span></span>|<span data-ttu-id="ff684-122">Description</span><span class="sxs-lookup"><span data-stu-id="ff684-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ff684-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff684-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ff684-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ff684-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff684-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff684-125">Remarks</span></span>

<span data-ttu-id="ff684-126">Par défaut, les threads GC de serveur sont affinités avec leurs UC respectives.</span><span class="sxs-lookup"><span data-stu-id="ff684-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="ff684-127">Chacun des processeurs disponibles du système a son propre tas GC et son propre thread.</span><span class="sxs-lookup"><span data-stu-id="ff684-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="ff684-128">Il s’agit généralement du paramètre préféré, car il optimise l’utilisation du cache.</span><span class="sxs-lookup"><span data-stu-id="ff684-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="ff684-129">À compter de .NET Framework 4.6.2, en affectant à l’attribut de l’élément **GCNoAffinitize** la valeur `enabled` `true` , vous pouvez spécifier que les threads de garbage collection du serveur et les processeurs ne doivent pas être étroitement couplés.</span><span class="sxs-lookup"><span data-stu-id="ff684-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="ff684-130">Vous pouvez spécifier l’élément de configuration **GCNoAffinitize** seul pour ne pas affinité les threads GC du serveur avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="ff684-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="ff684-131">Vous pouvez également l’utiliser avec l’élément [GCHeapCount](gcheapcount-element.md) pour contrôler le nombre de tas GC et de threads utilisés par une application.</span><span class="sxs-lookup"><span data-stu-id="ff684-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="ff684-132">Si l' `enabled` attribut de l’élément **GCNoAffinitize** est `false` (sa valeur par défaut), vous pouvez également utiliser l’élément [GCHeapCount](gcheapcount-element.md) pour spécifier le nombre de threads GC et de tas, ainsi que l’élément [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pour spécifier les processeurs sur lesquels les threads GC et les segments de mémoire sont affinité.</span><span class="sxs-lookup"><span data-stu-id="ff684-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="ff684-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff684-133">Example</span></span>

<span data-ttu-id="ff684-134">L’exemple suivant ne prend pas en affinité les threads GC du serveur :</span><span class="sxs-lookup"><span data-stu-id="ff684-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="ff684-135">L’exemple suivant n’affinité pas les threads GC du serveur et limite le nombre de tas/threads GC à 10 :</span><span class="sxs-lookup"><span data-stu-id="ff684-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ff684-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff684-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ff684-137">Élément GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="ff684-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="ff684-138">Élément GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="ff684-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="ff684-139">Notions de base de garbage collection</span><span class="sxs-lookup"><span data-stu-id="ff684-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="ff684-140">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ff684-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ff684-141">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="ff684-141">Configuration File Schema</span></span>](../index.md)
