---
title: Élément GCHeapCount
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283069"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="eb1ba-102">\<élément GCHeapCount ></span><span class="sxs-lookup"><span data-stu-id="eb1ba-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="eb1ba-103">Spécifie le nombre de segments/threads à utiliser pour le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

<span data-ttu-id="eb1ba-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="eb1ba-104">\<configuration></span></span>\
<span data-ttu-id="eb1ba-105">&nbsp;&nbsp;\<Runtime > </span><span class="sxs-lookup"><span data-stu-id="eb1ba-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="eb1ba-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount ></span><span class="sxs-lookup"><span data-stu-id="eb1ba-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount></span></span>

## <a name="syntax"></a><span data-ttu-id="eb1ba-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb1ba-107">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb1ba-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eb1ba-108">Attributes and elements</span></span>

<span data-ttu-id="eb1ba-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb1ba-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="eb1ba-110">Attributes</span></span>

|<span data-ttu-id="eb1ba-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="eb1ba-111">Attribute</span></span>|<span data-ttu-id="eb1ba-112">Description</span><span class="sxs-lookup"><span data-stu-id="eb1ba-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="eb1ba-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-113">Required attribute.</span></span><br /><br /><span data-ttu-id="eb1ba-114">Spécifie le nombre de segments de mémoire à utiliser pour le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-114">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="eb1ba-115">Le nombre réel de tas est le nombre minimal de segments de mémoire que vous spécifiez et le nombre de processeurs que votre processus est autorisé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-115">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="eb1ba-116">attribut activé</span><span class="sxs-lookup"><span data-stu-id="eb1ba-116">enabled attribute</span></span>

|<span data-ttu-id="eb1ba-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="eb1ba-117">Value</span></span>|<span data-ttu-id="eb1ba-118">Description</span><span class="sxs-lookup"><span data-stu-id="eb1ba-118">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="eb1ba-119">Nombre de segments de mémoire à utiliser pour le garbage collector du serveur.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-119">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="eb1ba-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eb1ba-120">Child elements</span></span>

<span data-ttu-id="eb1ba-121">aucune.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eb1ba-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eb1ba-122">Parent elements</span></span>

|<span data-ttu-id="eb1ba-123">Élément</span><span class="sxs-lookup"><span data-stu-id="eb1ba-123">Element</span></span>|<span data-ttu-id="eb1ba-124">Description</span><span class="sxs-lookup"><span data-stu-id="eb1ba-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="eb1ba-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="eb1ba-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-126">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eb1ba-127">Notes</span><span class="sxs-lookup"><span data-stu-id="eb1ba-127">Remarks</span></span>

<span data-ttu-id="eb1ba-128">Par défaut, les threads de garbage collection de serveur sont affinités avec leur processeur respectif, de sorte qu’il existe un tas GC, un thread GC de serveur et un thread de garbage collection de serveur d’arrière-plan pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-128">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="eb1ba-129">À compter de .NET Framework 4.6.2, vous pouvez utiliser l’élément **GCHeapCount** pour limiter le nombre de segments de mémoire utilisés par votre application pour le garbage collector du serveur.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-129">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="eb1ba-130">Limiter le nombre de segments de mémoire utilisés pour le garbage collection de serveur est particulièrement utile pour les systèmes qui exécutent plusieurs instances d’une application serveur.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-130">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="eb1ba-131">**GCHeapCount** est généralement utilisé avec deux autres indicateurs :</span><span class="sxs-lookup"><span data-stu-id="eb1ba-131">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="eb1ba-132">[GCNoAffinitize](gcnoaffinitize-element.md), qui contrôle si les threads/segments de mémoire GC du serveur sont affinité avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-132">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="eb1ba-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), qui contrôle l’affinité des threads/tas GC avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="eb1ba-134">Si **GCHeapCount** est défini et **GCNoAffinitize** est désactivé (paramètre par défaut), il existe une affinité entre les segments de mémoire/tas GC *nn* et les premiers processeurs *nn* .</span><span class="sxs-lookup"><span data-stu-id="eb1ba-134">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="eb1ba-135">Vous pouvez utiliser l’élément **GCHeapAffinitizeMask** pour spécifier quels processeurs sont utilisés par les tas GC du serveur du processus.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-135">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="eb1ba-136">Dans le cas contraire, si plusieurs processus serveur s’exécutent sur un système, leur utilisation se chevauchera.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-136">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="eb1ba-137">Si **GCHeapCount** est défini et que **GCNoAffinitize** est activé, le garbage collector limite le nombre de processeurs utilisés pour le garbage collector du serveur, mais ne affinité pas les tas et les processeurs gc.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-137">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="eb1ba-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb1ba-138">Example</span></span>

<span data-ttu-id="eb1ba-139">L’exemple suivant indique qu’une application utilise le garbage collection de serveur avec 10 tas/threads.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-139">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="eb1ba-140">Étant donné que vous ne voulez pas que ces tas chevauchent les tas d’autres applications s’exécutant sur le système, vous utilisez **GCHeapAffinitizeMask** pour spécifier que le processus doit utiliser les UC de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-140">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="eb1ba-141">L’exemple suivant n’affinité pas les threads GC du serveur et limite le nombre de tas/threads GC à 10.</span><span class="sxs-lookup"><span data-stu-id="eb1ba-141">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="eb1ba-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb1ba-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="eb1ba-143">Élément GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="eb1ba-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="eb1ba-144">Élément GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="eb1ba-144">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="eb1ba-145">Notions de base du garbage collection</span><span class="sxs-lookup"><span data-stu-id="eb1ba-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="eb1ba-146">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="eb1ba-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eb1ba-147">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="eb1ba-147">Configuration File Schema</span></span>](../index.md)
