---
title: <Thread_UseAllCpuGroups>, élément
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663421"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="9f75b-102">\<Thread_UseAllCpuGroups >, élément</span><span class="sxs-lookup"><span data-stu-id="9f75b-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="9f75b-103">Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="9f75b-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="9f75b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9f75b-104">\<configuration></span></span>\
<span data-ttu-id="9f75b-105">\<> du runtime </span><span class="sxs-lookup"><span data-stu-id="9f75b-105">\<runtime></span></span>\
<span data-ttu-id="9f75b-106">\<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="9f75b-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="9f75b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f75b-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f75b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9f75b-108">Attributes and Elements</span></span>

<span data-ttu-id="9f75b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9f75b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f75b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9f75b-110">Attributes</span></span>

|<span data-ttu-id="9f75b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="9f75b-111">Attribute</span></span>|<span data-ttu-id="9f75b-112">Description</span><span class="sxs-lookup"><span data-stu-id="9f75b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9f75b-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9f75b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9f75b-114">Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="9f75b-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="9f75b-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="9f75b-115">enabled Attribute</span></span>

|<span data-ttu-id="9f75b-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="9f75b-116">Value</span></span>|<span data-ttu-id="9f75b-117">Description</span><span class="sxs-lookup"><span data-stu-id="9f75b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="9f75b-118">Le runtime ne distribue pas les threads managés sur plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="9f75b-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="9f75b-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9f75b-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="9f75b-120">Le runtime distribue des threads managés sur plusieurs groupes de processeurs, si l’ordinateur a plusieurs groupes de processeurs et que l' [ \<élément GCCpuGroup >](gccpugroup-element.md) est activé.</span><span class="sxs-lookup"><span data-stu-id="9f75b-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9f75b-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9f75b-121">Child Elements</span></span>

<span data-ttu-id="9f75b-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9f75b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f75b-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9f75b-123">Parent Elements</span></span>

|<span data-ttu-id="9f75b-124">Élément</span><span class="sxs-lookup"><span data-stu-id="9f75b-124">Element</span></span>|<span data-ttu-id="9f75b-125">Description</span><span class="sxs-lookup"><span data-stu-id="9f75b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9f75b-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f75b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9f75b-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="9f75b-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f75b-128">Notes</span><span class="sxs-lookup"><span data-stu-id="9f75b-128">Remarks</span></span>

<span data-ttu-id="9f75b-129">Lorsqu’un ordinateur possède plusieurs groupes d’UC, l’activation de cet élément amène le runtime à distribuer des threads managés sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="9f75b-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="9f75b-130">Pour utiliser cette fonctionnalité, vous devez également activer l' [ \<élément GCCpuGroup >](gccpugroup-element.md) , qui étend garbage collection à tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et de l’équilibrage des tas.</span><span class="sxs-lookup"><span data-stu-id="9f75b-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="9f75b-131">L’activation de l' [ \<élément GCCpuGroup >](gccpugroup-element.md) nécessite l’activation de l' [ \<élément gcServer >](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9f75b-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="9f75b-132">Si ces éléments ne sont pas activés, `<Thread_UseAllCpuGroups>` l’activation de l’élément n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="9f75b-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="9f75b-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="9f75b-133">Example</span></span>

<span data-ttu-id="9f75b-134">L’exemple suivant montre comment activer la prise en charge de plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="9f75b-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9f75b-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f75b-135">See also</span></span>

- [<span data-ttu-id="9f75b-136">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="9f75b-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f75b-137">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="9f75b-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9f75b-138">\<GCCpuGroup >, élément</span><span class="sxs-lookup"><span data-stu-id="9f75b-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
