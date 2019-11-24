---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430480"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="39f14-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="39f14-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="39f14-103">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="39f14-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="39f14-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39f14-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39f14-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="39f14-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="39f14-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="39f14-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="39f14-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39f14-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="39f14-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="39f14-108">Attributes and Elements</span></span>

<span data-ttu-id="39f14-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="39f14-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="39f14-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="39f14-110">Attributes</span></span>

|<span data-ttu-id="39f14-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="39f14-111">Attribute</span></span>|<span data-ttu-id="39f14-112">Description</span><span class="sxs-lookup"><span data-stu-id="39f14-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="39f14-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="39f14-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="39f14-114">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="39f14-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="39f14-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="39f14-115">enabled Attribute</span></span>

|<span data-ttu-id="39f14-116">valeur</span><span class="sxs-lookup"><span data-stu-id="39f14-116">Value</span></span>|<span data-ttu-id="39f14-117">Description</span><span class="sxs-lookup"><span data-stu-id="39f14-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="39f14-118">Garbage collection does not support multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="39f14-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="39f14-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="39f14-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="39f14-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span><span class="sxs-lookup"><span data-stu-id="39f14-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="39f14-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="39f14-121">Child Elements</span></span>

<span data-ttu-id="39f14-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="39f14-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="39f14-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="39f14-123">Parent Elements</span></span>

|<span data-ttu-id="39f14-124">Élément</span><span class="sxs-lookup"><span data-stu-id="39f14-124">Element</span></span>|<span data-ttu-id="39f14-125">Description</span><span class="sxs-lookup"><span data-stu-id="39f14-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="39f14-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39f14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="39f14-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="39f14-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="39f14-128">Notes</span><span class="sxs-lookup"><span data-stu-id="39f14-128">Remarks</span></span>

<span data-ttu-id="39f14-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span><span class="sxs-lookup"><span data-stu-id="39f14-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="39f14-130">This element applies only to garbage collection threads.</span><span class="sxs-lookup"><span data-stu-id="39f14-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="39f14-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="39f14-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="39f14-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="39f14-132">Example</span></span>

<span data-ttu-id="39f14-133">The following example shows how to enable garbage collection for multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="39f14-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="39f14-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39f14-134">See also</span></span>

- [<span data-ttu-id="39f14-135">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="39f14-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="39f14-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="39f14-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="39f14-137">To disable concurrent garbage collection</span><span class="sxs-lookup"><span data-stu-id="39f14-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="39f14-138">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="39f14-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
