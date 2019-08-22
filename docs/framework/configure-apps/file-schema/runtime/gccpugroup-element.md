---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 197ab9dbc1ec85bf8961f60bb26496eab788e63f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663698"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="a9167-102">\<GCCpuGroup >, élément</span><span class="sxs-lookup"><span data-stu-id="a9167-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="a9167-103">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="a9167-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="a9167-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a9167-104">\<configuration></span></span>\
<span data-ttu-id="a9167-105">\<> du runtime </span><span class="sxs-lookup"><span data-stu-id="a9167-105">\<runtime></span></span>\
<span data-ttu-id="a9167-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="a9167-106">\<GCCpuGroup></span></span>

## <a name="syntax"></a><span data-ttu-id="a9167-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9167-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9167-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a9167-108">Attributes and Elements</span></span>

<span data-ttu-id="a9167-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a9167-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9167-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a9167-110">Attributes</span></span>

|<span data-ttu-id="a9167-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="a9167-111">Attribute</span></span>|<span data-ttu-id="a9167-112">Description</span><span class="sxs-lookup"><span data-stu-id="a9167-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a9167-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a9167-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a9167-114">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="a9167-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="a9167-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="a9167-115">enabled Attribute</span></span>

|<span data-ttu-id="a9167-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="a9167-116">Value</span></span>|<span data-ttu-id="a9167-117">Description</span><span class="sxs-lookup"><span data-stu-id="a9167-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a9167-118">Le garbage collection ne prend pas en charge plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="a9167-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="a9167-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a9167-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="a9167-120">Le garbage collection prend en charge plusieurs groupes de PROCESSEURs, si le serveur garbage collection est activé.</span><span class="sxs-lookup"><span data-stu-id="a9167-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a9167-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a9167-121">Child Elements</span></span>

<span data-ttu-id="a9167-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a9167-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a9167-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a9167-123">Parent Elements</span></span>

|<span data-ttu-id="a9167-124">Élément</span><span class="sxs-lookup"><span data-stu-id="a9167-124">Element</span></span>|<span data-ttu-id="a9167-125">Description</span><span class="sxs-lookup"><span data-stu-id="a9167-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a9167-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9167-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a9167-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a9167-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9167-128">Notes</span><span class="sxs-lookup"><span data-stu-id="a9167-128">Remarks</span></span>

<span data-ttu-id="a9167-129">Quand un ordinateur a plusieurs groupes d’UC et que la garbage collection du serveur est activée (Voir l' [ \<élément gcServer >](gcserver-element.md) ), l’activation de cet élément étend garbage collection sur tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et équilibrage des tas.</span><span class="sxs-lookup"><span data-stu-id="a9167-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="a9167-130">Cet élément s’applique uniquement aux threads garbage collections.</span><span class="sxs-lookup"><span data-stu-id="a9167-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="a9167-131">Pour permettre au runtime de distribuer des threads utilisateur sur tous les groupes de processeurs, vous devez également activer l' [ \<élément Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a9167-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="a9167-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="a9167-132">Example</span></span>

<span data-ttu-id="a9167-133">L’exemple suivant montre comment activer garbage collection pour plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="a9167-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a9167-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9167-134">See also</span></span>

- [<span data-ttu-id="a9167-135">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="a9167-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a9167-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a9167-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a9167-137">Pour désactiver les garbage collection simultanées</span><span class="sxs-lookup"><span data-stu-id="a9167-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="a9167-138">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="a9167-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
