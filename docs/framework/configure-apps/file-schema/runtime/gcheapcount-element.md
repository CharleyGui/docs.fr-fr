---
title: Élément GCHeapCount
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283069"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="40c4a-102">\<GCHeapCount>, élément</span><span class="sxs-lookup"><span data-stu-id="40c4a-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="40c4a-103">Spécifie le nombre de segments/threads à utiliser pour le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="40c4a-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="40c4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40c4a-104">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40c4a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="40c4a-105">Attributes and elements</span></span>

<span data-ttu-id="40c4a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="40c4a-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="40c4a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="40c4a-107">Attributes</span></span>

|<span data-ttu-id="40c4a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="40c4a-108">Attribute</span></span>|<span data-ttu-id="40c4a-109">Description</span><span class="sxs-lookup"><span data-stu-id="40c4a-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="40c4a-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="40c4a-110">Required attribute.</span></span><br /><br /><span data-ttu-id="40c4a-111">Spécifie le nombre de segments de mémoire à utiliser pour le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="40c4a-111">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="40c4a-112">Le nombre réel de tas est le nombre minimal de segments de mémoire que vous spécifiez et le nombre de processeurs que votre processus est autorisé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="40c4a-112">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="40c4a-113">attribut activé</span><span class="sxs-lookup"><span data-stu-id="40c4a-113">enabled attribute</span></span>

|<span data-ttu-id="40c4a-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="40c4a-114">Value</span></span>|<span data-ttu-id="40c4a-115">Description</span><span class="sxs-lookup"><span data-stu-id="40c4a-115">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="40c4a-116">Nombre de segments de mémoire à utiliser pour le garbage collector du serveur.</span><span class="sxs-lookup"><span data-stu-id="40c4a-116">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40c4a-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40c4a-117">Child elements</span></span>

<span data-ttu-id="40c4a-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="40c4a-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40c4a-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40c4a-119">Parent elements</span></span>

|<span data-ttu-id="40c4a-120">Élément</span><span class="sxs-lookup"><span data-stu-id="40c4a-120">Element</span></span>|<span data-ttu-id="40c4a-121">Description</span><span class="sxs-lookup"><span data-stu-id="40c4a-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="40c4a-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40c4a-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="40c4a-123">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="40c4a-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40c4a-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="40c4a-124">Remarks</span></span>

<span data-ttu-id="40c4a-125">Par défaut, les threads de garbage collection de serveur sont affinités avec leur processeur respectif, de sorte qu’il existe un tas GC, un thread GC de serveur et un thread de garbage collection de serveur d’arrière-plan pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="40c4a-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="40c4a-126">À compter de .NET Framework 4.6.2, vous pouvez utiliser l’élément **GCHeapCount** pour limiter le nombre de segments de mémoire utilisés par votre application pour le garbage collector du serveur.</span><span class="sxs-lookup"><span data-stu-id="40c4a-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="40c4a-127">Limiter le nombre de segments de mémoire utilisés pour le garbage collection de serveur est particulièrement utile pour les systèmes qui exécutent plusieurs instances d’une application serveur.</span><span class="sxs-lookup"><span data-stu-id="40c4a-127">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="40c4a-128">**GCHeapCount** est généralement utilisé avec deux autres indicateurs :</span><span class="sxs-lookup"><span data-stu-id="40c4a-128">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="40c4a-129">[GCNoAffinitize](gcnoaffinitize-element.md), qui contrôle si les threads/segments de mémoire GC du serveur sont affinité avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="40c4a-129">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="40c4a-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), qui contrôle l’affinité des threads/tas GC avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="40c4a-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="40c4a-131">Si **GCHeapCount** est défini et **GCNoAffinitize** est désactivé (paramètre par défaut), il existe une affinité entre les segments de mémoire/tas GC *nn* et les premiers processeurs *nn* .</span><span class="sxs-lookup"><span data-stu-id="40c4a-131">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="40c4a-132">Vous pouvez utiliser l’élément **GCHeapAffinitizeMask** pour spécifier quels processeurs sont utilisés par les tas GC du serveur du processus.</span><span class="sxs-lookup"><span data-stu-id="40c4a-132">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="40c4a-133">Dans le cas contraire, si plusieurs processus serveur s’exécutent sur un système, leur utilisation se chevauchera.</span><span class="sxs-lookup"><span data-stu-id="40c4a-133">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="40c4a-134">Si **GCHeapCount** est défini et que **GCNoAffinitize** est activé, le garbage collector limite le nombre de processeurs utilisés pour le garbage collector du serveur, mais ne affinité pas les tas et les processeurs gc.</span><span class="sxs-lookup"><span data-stu-id="40c4a-134">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="40c4a-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="40c4a-135">Example</span></span>

<span data-ttu-id="40c4a-136">L’exemple suivant indique qu’une application utilise le garbage collection de serveur avec 10 tas/threads.</span><span class="sxs-lookup"><span data-stu-id="40c4a-136">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="40c4a-137">Étant donné que vous ne voulez pas que ces tas chevauchent les tas d’autres applications s’exécutant sur le système, vous utilisez **GCHeapAffinitizeMask** pour spécifier que le processus doit utiliser les UC de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="40c4a-137">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="40c4a-138">L’exemple suivant n’affinité pas les threads GC du serveur et limite le nombre de tas/threads GC à 10.</span><span class="sxs-lookup"><span data-stu-id="40c4a-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="40c4a-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40c4a-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="40c4a-140">Élément GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="40c4a-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="40c4a-141">Élément GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="40c4a-141">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="40c4a-142">Notions de base de garbage collection</span><span class="sxs-lookup"><span data-stu-id="40c4a-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="40c4a-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="40c4a-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40c4a-144">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="40c4a-144">Configuration File Schema</span></span>](../index.md)
