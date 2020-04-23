---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102890"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="75659-102">\<GCCpuGroup> Élément</span><span class="sxs-lookup"><span data-stu-id="75659-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="75659-103">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="75659-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="75659-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75659-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75659-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="75659-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="75659-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="75659-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="75659-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75659-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75659-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75659-108">Attributes and Elements</span></span>

<span data-ttu-id="75659-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75659-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="75659-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="75659-110">Attributes</span></span>

|<span data-ttu-id="75659-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="75659-111">Attribute</span></span>|<span data-ttu-id="75659-112">Description</span><span class="sxs-lookup"><span data-stu-id="75659-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="75659-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="75659-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="75659-114">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="75659-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="75659-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="75659-115">enabled Attribute</span></span>

|<span data-ttu-id="75659-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="75659-116">Value</span></span>|<span data-ttu-id="75659-117">Description</span><span class="sxs-lookup"><span data-stu-id="75659-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="75659-118">La collecte des ordures ne prend pas en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="75659-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="75659-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="75659-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="75659-120">La collecte des ordures prend en charge plusieurs groupes de processeurs, si la collecte des ordures du serveur est activée.</span><span class="sxs-lookup"><span data-stu-id="75659-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="75659-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75659-121">Child Elements</span></span>

<span data-ttu-id="75659-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="75659-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75659-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75659-123">Parent Elements</span></span>

|<span data-ttu-id="75659-124">Élément</span><span class="sxs-lookup"><span data-stu-id="75659-124">Element</span></span>|<span data-ttu-id="75659-125">Description</span><span class="sxs-lookup"><span data-stu-id="75659-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="75659-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75659-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="75659-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="75659-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75659-128">Notes</span><span class="sxs-lookup"><span data-stu-id="75659-128">Remarks</span></span>

<span data-ttu-id="75659-129">Lorsqu’un ordinateur dispose de plusieurs groupes de processeurs et que la collecte des ordures des serveurs est activée (voir [ \<l’élément gcServer>),](gcserver-element.md) ce qui permet à cet élément d’étendre la collecte des ordures dans tous les groupes de processeur et de prendre en compte tous les noyaux lors de la création et de l’équilibrage des tas.</span><span class="sxs-lookup"><span data-stu-id="75659-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="75659-130">Cet élément ne s’applique qu’aux fils de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="75659-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="75659-131">Pour activer le temps d’exécution pour distribuer des threads d’utilisateurs sur tous les groupes de processeurs, vous devez également activer [ \<l’élément Thread_UseAllCpuGroups>.](thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="75659-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="75659-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="75659-132">Example</span></span>

<span data-ttu-id="75659-133">L’exemple suivant montre comment permettre la collecte des ordures pour plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="75659-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="75659-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75659-134">See also</span></span>

- [<span data-ttu-id="75659-135">Paramètres de durée d’exécution Schema</span><span class="sxs-lookup"><span data-stu-id="75659-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="75659-136">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="75659-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="75659-137">Désactiver la collecte simultanée des ordures</span><span class="sxs-lookup"><span data-stu-id="75659-137">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="75659-138">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="75659-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
