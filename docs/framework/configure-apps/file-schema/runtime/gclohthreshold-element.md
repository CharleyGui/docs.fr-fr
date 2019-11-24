---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451219"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="0fca9-102">GCLOHThreshold element</span><span class="sxs-lookup"><span data-stu-id="0fca9-102">GCLOHThreshold element</span></span>

<span data-ttu-id="0fca9-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span><span class="sxs-lookup"><span data-stu-id="0fca9-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="0fca9-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fca9-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="0fca9-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fca9-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="0fca9-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span><span class="sxs-lookup"><span data-stu-id="0fca9-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="0fca9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fca9-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="0fca9-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="0fca9-108">Attributes</span></span>

|<span data-ttu-id="0fca9-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0fca9-109">Attribute</span></span>|<span data-ttu-id="0fca9-110">Description</span><span class="sxs-lookup"><span data-stu-id="0fca9-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0fca9-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0fca9-111">Required attribute.</span></span><br /><br /><span data-ttu-id="0fca9-112">Specifies the threshold size that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="0fca9-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="0fca9-113">enabled attribute</span><span class="sxs-lookup"><span data-stu-id="0fca9-113">enabled attribute</span></span>

|<span data-ttu-id="0fca9-114">valeur</span><span class="sxs-lookup"><span data-stu-id="0fca9-114">Value</span></span>|<span data-ttu-id="0fca9-115">Description</span><span class="sxs-lookup"><span data-stu-id="0fca9-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="0fca9-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="0fca9-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="0fca9-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0fca9-117">Child elements</span></span>

<span data-ttu-id="0fca9-118">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="0fca9-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="0fca9-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0fca9-119">Parent elements</span></span>

|<span data-ttu-id="0fca9-120">Élément</span><span class="sxs-lookup"><span data-stu-id="0fca9-120">Element</span></span>|<span data-ttu-id="0fca9-121">Description</span><span class="sxs-lookup"><span data-stu-id="0fca9-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0fca9-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fca9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0fca9-123">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0fca9-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0fca9-124">Notes</span><span class="sxs-lookup"><span data-stu-id="0fca9-124">Remarks</span></span>

<span data-ttu-id="0fca9-125">This setting was introduced in .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="0fca9-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fca9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fca9-126">See also</span></span>

- [<span data-ttu-id="0fca9-127">Run-time settings schema</span><span class="sxs-lookup"><span data-stu-id="0fca9-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="0fca9-128">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0fca9-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="0fca9-129">Notions de base du garbage collection</span><span class="sxs-lookup"><span data-stu-id="0fca9-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="0fca9-130">NET Core run-time config options for GC</span><span class="sxs-lookup"><span data-stu-id="0fca9-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
