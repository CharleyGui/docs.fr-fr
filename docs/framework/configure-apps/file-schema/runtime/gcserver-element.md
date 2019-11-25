---
title: Élément gcServer
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968945"
---
# <a name="gcserver-element"></a><span data-ttu-id="0ef80-102">\<élément gcServer ></span><span class="sxs-lookup"><span data-stu-id="0ef80-102">\<gcServer> element</span></span>

<span data-ttu-id="0ef80-103">Spécifie si le common language runtime exécute le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

<span data-ttu-id="0ef80-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ef80-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="0ef80-105">&nbsp;&nbsp;[\<runtime >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ef80-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="0ef80-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer ></span><span class="sxs-lookup"><span data-stu-id="0ef80-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer></span></span>

## <a name="syntax"></a><span data-ttu-id="0ef80-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ef80-107">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ef80-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0ef80-108">Attributes and elements</span></span>

<span data-ttu-id="0ef80-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0ef80-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ef80-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0ef80-110">Attributes</span></span>

|<span data-ttu-id="0ef80-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0ef80-111">Attribute</span></span>|<span data-ttu-id="0ef80-112">Description</span><span class="sxs-lookup"><span data-stu-id="0ef80-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0ef80-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0ef80-113">Required attribute.</span></span><br /><br /><span data-ttu-id="0ef80-114">Spécifie si le runtime exécute le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-114">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="0ef80-115">attribut activé</span><span class="sxs-lookup"><span data-stu-id="0ef80-115">enabled attribute</span></span>

|<span data-ttu-id="0ef80-116">valeur</span><span class="sxs-lookup"><span data-stu-id="0ef80-116">Value</span></span>|<span data-ttu-id="0ef80-117">Description</span><span class="sxs-lookup"><span data-stu-id="0ef80-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0ef80-118">N'exécute pas le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-118">Does not run server garbage collection.</span></span> <span data-ttu-id="0ef80-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ef80-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="0ef80-120">Exécute le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-120">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0ef80-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0ef80-121">Child elements</span></span>

<span data-ttu-id="0ef80-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="0ef80-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ef80-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0ef80-123">Parent elements</span></span>

|<span data-ttu-id="0ef80-124">Élément</span><span class="sxs-lookup"><span data-stu-id="0ef80-124">Element</span></span>|<span data-ttu-id="0ef80-125">Description</span><span class="sxs-lookup"><span data-stu-id="0ef80-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0ef80-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ef80-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0ef80-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0ef80-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ef80-128">Notes</span><span class="sxs-lookup"><span data-stu-id="0ef80-128">Remarks</span></span>

<span data-ttu-id="0ef80-129">Le common language runtime (ou CLR) prend en charge deux types de garbage collection : le garbage collection côté station de travail, qui est disponible sur tous les systèmes, et le garbage collection côté serveur, qui est disponible sur les systèmes multiprocesseurs.</span><span class="sxs-lookup"><span data-stu-id="0ef80-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="0ef80-130">Utilisez l’élément **gcServer** pour contrôler le type de garbage collection que le CLR effectue.</span><span class="sxs-lookup"><span data-stu-id="0ef80-130">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="0ef80-131">Utilisez la propriété <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> pour déterminer si le garbage collection côté serveur est activé.</span><span class="sxs-lookup"><span data-stu-id="0ef80-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="0ef80-132">Pour les ordinateurs monoprocesseurs, le garbage collection côté station de travail configuré par défaut représente normalement l'option la plus rapide.</span><span class="sxs-lookup"><span data-stu-id="0ef80-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="0ef80-133">L'option station de travail ou serveur peut être utilisée pour les ordinateurs biprocesseurs.</span><span class="sxs-lookup"><span data-stu-id="0ef80-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="0ef80-134">Le garbage collection côté serveur est normalement l'option la plus rapide pour les ordinateurs comptant plus de deux processeurs.</span><span class="sxs-lookup"><span data-stu-id="0ef80-134">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="0ef80-135">En règle générale, les systèmes de serveurs multiprocesseurs désactivent le garbage collector du serveur et utilisent le GC de station de travail à la place lorsque de nombreuses instances d’une application serveur s’exécutent sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-135">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="0ef80-136">Cet élément peut être défini uniquement dans le fichier de configuration de l'application (il est ignoré s'il est défini dans le fichier de configuration de l'ordinateur).</span><span class="sxs-lookup"><span data-stu-id="0ef80-136">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef80-137">Dans .NET Framework 4 et les versions antérieures, le garbage collection simultané n'est pas disponible si le garbage collection côté serveur est activé.</span><span class="sxs-lookup"><span data-stu-id="0ef80-137">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="0ef80-138">À partir de la .NET Framework 4,5, le garbage collection du serveur est simultané.</span><span class="sxs-lookup"><span data-stu-id="0ef80-138">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="0ef80-139">Pour utiliser le garbage collection serveur non simultané, définissez l’élément **gcServer** sur `true` et l' [élément gcConcurrent](gcconcurrent-element.md) sur `false`.</span><span class="sxs-lookup"><span data-stu-id="0ef80-139">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="0ef80-140">À compter de .NET Framework 4.6.2, vous pouvez également utiliser les éléments suivants pour configurer le garbage collector du serveur :</span><span class="sxs-lookup"><span data-stu-id="0ef80-140">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="0ef80-141">[GCNoAffinitize](gcnoaffinitize-element.md), qui spécifie s’il existe une affinité entre les tas et les PROCESSEURs GC du serveur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-141">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="0ef80-142">Par défaut, il existe un tas GC de serveur pour chaque processeur.</span><span class="sxs-lookup"><span data-stu-id="0ef80-142">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="0ef80-143">[GCHeapCount](gcheapcount-element.md), qui limite le nombre de segments de mémoire utilisés par un processus.</span><span class="sxs-lookup"><span data-stu-id="0ef80-143">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="0ef80-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), qui définit l’affinité entre les tas de garbage collection de serveur disponibles et les processeurs individuels.</span><span class="sxs-lookup"><span data-stu-id="0ef80-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="0ef80-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="0ef80-145">Example</span></span>

<span data-ttu-id="0ef80-146">L’exemple suivant active le garbage collection serveur :</span><span class="sxs-lookup"><span data-stu-id="0ef80-146">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0ef80-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ef80-147">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0ef80-148">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="0ef80-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0ef80-149">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0ef80-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0ef80-150">Pour désactiver les garbage collection simultanées</span><span class="sxs-lookup"><span data-stu-id="0ef80-150">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
