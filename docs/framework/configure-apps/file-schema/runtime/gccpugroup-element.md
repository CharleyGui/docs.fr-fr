---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116832"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="80b43-102">\<élément GCCpuGroup ></span><span class="sxs-lookup"><span data-stu-id="80b43-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="80b43-103">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="80b43-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="80b43-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="80b43-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="80b43-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="80b43-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="80b43-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup** ></span><span class="sxs-lookup"><span data-stu-id="80b43-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="80b43-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80b43-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80b43-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="80b43-108">Attributes and Elements</span></span>

<span data-ttu-id="80b43-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="80b43-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="80b43-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="80b43-110">Attributes</span></span>

|<span data-ttu-id="80b43-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="80b43-111">Attribute</span></span>|<span data-ttu-id="80b43-112">Description</span><span class="sxs-lookup"><span data-stu-id="80b43-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="80b43-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="80b43-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="80b43-114">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="80b43-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="80b43-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="80b43-115">enabled Attribute</span></span>

|<span data-ttu-id="80b43-116">valeur</span><span class="sxs-lookup"><span data-stu-id="80b43-116">Value</span></span>|<span data-ttu-id="80b43-117">Description</span><span class="sxs-lookup"><span data-stu-id="80b43-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="80b43-118">Le garbage collection ne prend pas en charge plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="80b43-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="80b43-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="80b43-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="80b43-120">Le garbage collection prend en charge plusieurs groupes de PROCESSEURs, si le serveur garbage collection est activé.</span><span class="sxs-lookup"><span data-stu-id="80b43-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="80b43-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="80b43-121">Child Elements</span></span>

<span data-ttu-id="80b43-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="80b43-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80b43-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="80b43-123">Parent Elements</span></span>

|<span data-ttu-id="80b43-124">Élément</span><span class="sxs-lookup"><span data-stu-id="80b43-124">Element</span></span>|<span data-ttu-id="80b43-125">Description</span><span class="sxs-lookup"><span data-stu-id="80b43-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="80b43-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80b43-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="80b43-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="80b43-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80b43-128">Notes</span><span class="sxs-lookup"><span data-stu-id="80b43-128">Remarks</span></span>

<span data-ttu-id="80b43-129">Quand un ordinateur a plusieurs groupes d’UC et que la garbage collection du serveur est activée (Voir l’élément [\<gcServer >](gcserver-element.md) ), l’activation de cet élément étend garbage collection sur tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et équilibrage des tas.</span><span class="sxs-lookup"><span data-stu-id="80b43-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="80b43-130">Cet élément s’applique uniquement aux threads garbage collections.</span><span class="sxs-lookup"><span data-stu-id="80b43-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="80b43-131">Pour permettre au runtime de distribuer des threads utilisateur sur tous les groupes de PROCESSEURs, vous devez également activer l’élément [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="80b43-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="80b43-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="80b43-132">Example</span></span>

<span data-ttu-id="80b43-133">L’exemple suivant montre comment activer garbage collection pour plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="80b43-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="80b43-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80b43-134">See also</span></span>

- [<span data-ttu-id="80b43-135">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="80b43-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="80b43-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="80b43-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="80b43-137">Pour désactiver les garbage collection simultanées</span><span class="sxs-lookup"><span data-stu-id="80b43-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="80b43-138">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="80b43-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
