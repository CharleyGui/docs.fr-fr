---
title: Élément GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978381"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="c5b1a-102">\<GCHeapAffinitizeMask>, élément</span><span class="sxs-lookup"><span data-stu-id="c5b1a-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="c5b1a-103">Définit l’affinité entre les tas GC et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="c5b1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5b1a-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5b1a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c5b1a-105">Attributes and elements</span></span>

<span data-ttu-id="c5b1a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5b1a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c5b1a-107">Attributes</span></span>

|<span data-ttu-id="c5b1a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c5b1a-108">Attribute</span></span>|<span data-ttu-id="c5b1a-109">Description</span><span class="sxs-lookup"><span data-stu-id="c5b1a-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c5b1a-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-110">Required attribute.</span></span><br /><br /><span data-ttu-id="c5b1a-111">Spécifie l’affinité entre les tas GC et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="c5b1a-112">attribut activé</span><span class="sxs-lookup"><span data-stu-id="c5b1a-112">enabled attribute</span></span>

|<span data-ttu-id="c5b1a-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="c5b1a-113">Value</span></span>|<span data-ttu-id="c5b1a-114">Description</span><span class="sxs-lookup"><span data-stu-id="c5b1a-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="c5b1a-115">Valeur décimale qui forme un masque de masque définissant l’affinité entre les segments de mémoire GC du serveur et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="c5b1a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c5b1a-116">Child elements</span></span>

<span data-ttu-id="c5b1a-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5b1a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c5b1a-118">Parent elements</span></span>

|<span data-ttu-id="c5b1a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c5b1a-119">Element</span></span>|<span data-ttu-id="c5b1a-120">Description</span><span class="sxs-lookup"><span data-stu-id="c5b1a-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c5b1a-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c5b1a-122">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c5b1a-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5b1a-123">Remarks</span></span>

<span data-ttu-id="c5b1a-124">Par défaut, les threads de garbage collection de serveur sont affinités avec leur processeur respectif, de sorte qu’il existe un tas GC, un thread GC de serveur et un thread de garbage collection de serveur d’arrière-plan pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="c5b1a-125">À compter de .NET Framework 4.6.2, vous pouvez utiliser l’élément **GCHeapAffinitizeMask** pour contrôler l’affinité entre les tas et les processeurs de garbage collection de serveur lorsque le nombre de segments est limité par l’élément **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="c5b1a-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="c5b1a-126">**GCHeapAffinitizeMask** est généralement utilisé avec deux autres indicateurs :</span><span class="sxs-lookup"><span data-stu-id="c5b1a-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="c5b1a-127">[GCNoAffinitize](gcnoaffinitize-element.md), qui contrôle si les threads/segments de mémoire GC du serveur sont affinité avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="c5b1a-128">L' `enabled` attribut de l’élément [GCNoAffinitize](gcnoaffinitize-element.md) doit être `false` (sa valeur par défaut) pour que le paramètre **GCHeapAffinitizeMask** soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="c5b1a-129">[GCHeapCount](gcheapcount-element.md), qui limite le nombre de segments de mémoire utilisés par le processus pour le garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="c5b1a-130">Par défaut, il existe un tas pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="c5b1a-131">**nnnn** est un masque de bits exprimé sous la forme d’une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="c5b1a-132">Le bit 0 de l’octet 0 représente le processeur 0, le bit 1 de l’octet 0 représente le processeur 1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="c5b1a-133">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c5b1a-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="c5b1a-134">La valeur 1023 est 0x3FF ou 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="c5b1a-135">Le processus utilise 10 processeurs, du processeur 0 jusqu’au processeur 9.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="c5b1a-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5b1a-136">Example</span></span>

<span data-ttu-id="c5b1a-137">L’exemple suivant indique qu’une application utilise le garbage collection de serveur avec 10 tas/threads.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="c5b1a-138">Étant donné que vous ne voulez pas que ces tas chevauchent les tas d’autres applications s’exécutant sur le système, utilisez **GCHeapAffinitizeMask** pour spécifier que le processus doit utiliser les UC de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="c5b1a-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c5b1a-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5b1a-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c5b1a-140">Élément GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c5b1a-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="c5b1a-141">Élément GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="c5b1a-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="c5b1a-142">Notions de base de garbage collection</span><span class="sxs-lookup"><span data-stu-id="c5b1a-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="c5b1a-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="c5b1a-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c5b1a-144">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c5b1a-144">Configuration File Schema</span></span>](../index.md)
