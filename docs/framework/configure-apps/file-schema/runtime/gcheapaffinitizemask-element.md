---
title: Élément GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978381"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="b69fd-102">\<élément GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="b69fd-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="b69fd-103">Définit l’affinité entre les tas GC et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="b69fd-103">Defines the affinity between GC heaps and individual processors.</span></span>

<span data-ttu-id="b69fd-104">\<> de configuration </span><span class="sxs-lookup"><span data-stu-id="b69fd-104">\<configuration></span></span>\
<span data-ttu-id="b69fd-105">&nbsp;&nbsp;\<Runtime > </span><span class="sxs-lookup"><span data-stu-id="b69fd-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="b69fd-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="b69fd-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask></span></span>

## <a name="syntax"></a><span data-ttu-id="b69fd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b69fd-107">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b69fd-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b69fd-108">Attributes and elements</span></span>

<span data-ttu-id="b69fd-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b69fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b69fd-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b69fd-110">Attributes</span></span>

|<span data-ttu-id="b69fd-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b69fd-111">Attribute</span></span>|<span data-ttu-id="b69fd-112">Description</span><span class="sxs-lookup"><span data-stu-id="b69fd-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b69fd-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b69fd-113">Required attribute.</span></span><br /><br /><span data-ttu-id="b69fd-114">Spécifie l’affinité entre les tas GC et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="b69fd-114">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="b69fd-115">attribut activé</span><span class="sxs-lookup"><span data-stu-id="b69fd-115">enabled attribute</span></span>

|<span data-ttu-id="b69fd-116">valeur</span><span class="sxs-lookup"><span data-stu-id="b69fd-116">Value</span></span>|<span data-ttu-id="b69fd-117">Description</span><span class="sxs-lookup"><span data-stu-id="b69fd-117">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="b69fd-118">Valeur décimale qui forme un masque de masque définissant l’affinité entre les segments de mémoire GC du serveur et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="b69fd-118">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="b69fd-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b69fd-119">Child elements</span></span>

<span data-ttu-id="b69fd-120">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="b69fd-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b69fd-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b69fd-121">Parent elements</span></span>

|<span data-ttu-id="b69fd-122">Élément</span><span class="sxs-lookup"><span data-stu-id="b69fd-122">Element</span></span>|<span data-ttu-id="b69fd-123">Description</span><span class="sxs-lookup"><span data-stu-id="b69fd-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b69fd-124">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b69fd-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b69fd-125">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b69fd-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b69fd-126">Notes</span><span class="sxs-lookup"><span data-stu-id="b69fd-126">Remarks</span></span>

<span data-ttu-id="b69fd-127">Par défaut, les threads de garbage collection de serveur sont affinités avec leur processeur respectif, de sorte qu’il existe un tas GC, un thread GC de serveur et un thread de garbage collection de serveur d’arrière-plan pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="b69fd-127">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="b69fd-128">À compter de .NET Framework 4.6.2, vous pouvez utiliser l’élément **GCHeapAffinitizeMask** pour contrôler l’affinité entre les tas et les processeurs de garbage collection de serveur lorsque le nombre de segments est limité par l’élément **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="b69fd-128">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="b69fd-129">**GCHeapAffinitizeMask** est généralement utilisé avec deux autres indicateurs :</span><span class="sxs-lookup"><span data-stu-id="b69fd-129">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="b69fd-130">[GCNoAffinitize](gcnoaffinitize-element.md), qui contrôle si les threads/segments de mémoire GC du serveur sont affinité avec des processeurs.</span><span class="sxs-lookup"><span data-stu-id="b69fd-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="b69fd-131">L’attribut `enabled` de l’élément [GCNoAffinitize](gcnoaffinitize-element.md) doit être `false` (sa valeur par défaut) pour que le paramètre **GCHeapAffinitizeMask** soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="b69fd-131">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="b69fd-132">[GCHeapCount](gcheapcount-element.md), qui limite le nombre de segments de mémoire utilisés par le processus pour le garbage collection de serveur.</span><span class="sxs-lookup"><span data-stu-id="b69fd-132">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="b69fd-133">Par défaut, il existe un tas pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="b69fd-133">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="b69fd-134">**nnnn** est un masque de bits exprimé sous la forme d’une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="b69fd-134">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="b69fd-135">Le bit 0 de l’octet 0 représente le processeur 0, le bit 1 de l’octet 0 représente le processeur 1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b69fd-135">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="b69fd-136">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b69fd-136">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="b69fd-137">La valeur 1023 est 0x3FF ou 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="b69fd-137">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="b69fd-138">Le processus utilise 10 processeurs, du processeur 0 jusqu’au processeur 9.</span><span class="sxs-lookup"><span data-stu-id="b69fd-138">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="b69fd-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="b69fd-139">Example</span></span>

<span data-ttu-id="b69fd-140">L’exemple suivant indique qu’une application utilise le garbage collection de serveur avec 10 tas/threads.</span><span class="sxs-lookup"><span data-stu-id="b69fd-140">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="b69fd-141">Étant donné que vous ne voulez pas que ces tas chevauchent les tas d’autres applications s’exécutant sur le système, utilisez **GCHeapAffinitizeMask** pour spécifier que le processus doit utiliser les UC de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="b69fd-141">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b69fd-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b69fd-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b69fd-143">Élément GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="b69fd-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="b69fd-144">Élément GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="b69fd-144">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="b69fd-145">Notions de base du garbage collection</span><span class="sxs-lookup"><span data-stu-id="b69fd-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="b69fd-146">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="b69fd-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b69fd-147">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b69fd-147">Configuration File Schema</span></span>](../index.md)
