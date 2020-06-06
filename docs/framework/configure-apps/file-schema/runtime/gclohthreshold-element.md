---
title: Élément GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451219"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="31ba6-102">Élément GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="31ba6-102">GCLOHThreshold element</span></span>

<span data-ttu-id="31ba6-103">Spécifie la taille du seuil, en octets, qui amène le garbage collector à placer des objets sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="31ba6-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="31ba6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31ba6-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="31ba6-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="31ba6-105">Attributes</span></span>

|<span data-ttu-id="31ba6-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="31ba6-106">Attribute</span></span>|<span data-ttu-id="31ba6-107">Description</span><span class="sxs-lookup"><span data-stu-id="31ba6-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="31ba6-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="31ba6-108">Required attribute.</span></span><br /><br /><span data-ttu-id="31ba6-109">Spécifie la taille du seuil qui amène les objets sur le tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="31ba6-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="31ba6-110">attribut activé</span><span class="sxs-lookup"><span data-stu-id="31ba6-110">enabled attribute</span></span>

|<span data-ttu-id="31ba6-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="31ba6-111">Value</span></span>|<span data-ttu-id="31ba6-112">Description</span><span class="sxs-lookup"><span data-stu-id="31ba6-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="31ba6-113">Taille du seuil, en octets, qui provoque l’accès des objets sur le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="31ba6-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="31ba6-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="31ba6-114">Child elements</span></span>

<span data-ttu-id="31ba6-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="31ba6-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="31ba6-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="31ba6-116">Parent elements</span></span>

|<span data-ttu-id="31ba6-117">Élément</span><span class="sxs-lookup"><span data-stu-id="31ba6-117">Element</span></span>|<span data-ttu-id="31ba6-118">Description</span><span class="sxs-lookup"><span data-stu-id="31ba6-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="31ba6-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31ba6-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="31ba6-120">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="31ba6-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="31ba6-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="31ba6-121">Remarks</span></span>

<span data-ttu-id="31ba6-122">Ce paramètre a été introduit dans .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="31ba6-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="31ba6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31ba6-123">See also</span></span>

- [<span data-ttu-id="31ba6-124">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="31ba6-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="31ba6-125">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="31ba6-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="31ba6-126">Notions de base de garbage collection</span><span class="sxs-lookup"><span data-stu-id="31ba6-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="31ba6-127">Options de configuration du runtime NET Core pour GC</span><span class="sxs-lookup"><span data-stu-id="31ba6-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
