---
title: <Thread_UseAllCpuGroups>, élément
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115411"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="8cd25-102">Élément \<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="8cd25-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="8cd25-103">Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="8cd25-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="8cd25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cd25-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cd25-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8cd25-105">Attributes and Elements</span></span>

<span data-ttu-id="8cd25-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8cd25-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cd25-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8cd25-107">Attributes</span></span>

|<span data-ttu-id="8cd25-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="8cd25-108">Attribute</span></span>|<span data-ttu-id="8cd25-109">Description</span><span class="sxs-lookup"><span data-stu-id="8cd25-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8cd25-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="8cd25-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="8cd25-111">Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="8cd25-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="8cd25-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="8cd25-112">enabled Attribute</span></span>

|<span data-ttu-id="8cd25-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="8cd25-113">Value</span></span>|<span data-ttu-id="8cd25-114">Description</span><span class="sxs-lookup"><span data-stu-id="8cd25-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="8cd25-115">Le runtime ne distribue pas les threads managés sur plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="8cd25-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="8cd25-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8cd25-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="8cd25-117">Le runtime distribue des threads managés sur plusieurs groupes de PROCESSEURs, si l’ordinateur a plusieurs groupes d’UC et que l' [\<GCCpuGroup>](gccpugroup-element.md) élément est activé.</span><span class="sxs-lookup"><span data-stu-id="8cd25-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8cd25-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8cd25-118">Child Elements</span></span>

<span data-ttu-id="8cd25-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8cd25-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8cd25-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8cd25-120">Parent Elements</span></span>

|<span data-ttu-id="8cd25-121">Élément</span><span class="sxs-lookup"><span data-stu-id="8cd25-121">Element</span></span>|<span data-ttu-id="8cd25-122">Description</span><span class="sxs-lookup"><span data-stu-id="8cd25-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8cd25-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8cd25-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8cd25-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8cd25-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8cd25-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="8cd25-125">Remarks</span></span>

<span data-ttu-id="8cd25-126">Lorsqu’un ordinateur possède plusieurs groupes d’UC, l’activation de cet élément amène le runtime à distribuer des threads managés sur tous les groupes de PROCESSEURs.</span><span class="sxs-lookup"><span data-stu-id="8cd25-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="8cd25-127">Pour utiliser cette fonctionnalité, vous devez également activer l' [\<GCCpuGroup>](gccpugroup-element.md) élément, qui étend garbage collection à tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et de l’équilibrage des tas.</span><span class="sxs-lookup"><span data-stu-id="8cd25-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="8cd25-128">L’activation de l' [\<GCCpuGroup>](gccpugroup-element.md) élément nécessite l’activation de l' [\<gcServer>](gcserver-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="8cd25-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="8cd25-129">Si ces éléments ne sont pas activés, l’activation de l' `<Thread_UseAllCpuGroups>` élément n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="8cd25-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="8cd25-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="8cd25-130">Example</span></span>

<span data-ttu-id="8cd25-131">L’exemple suivant montre comment activer la prise en charge de plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="8cd25-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8cd25-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cd25-132">See also</span></span>

- [<span data-ttu-id="8cd25-133">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="8cd25-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8cd25-134">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8cd25-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8cd25-135">\<GCCpuGroup>Appartient</span><span class="sxs-lookup"><span data-stu-id="8cd25-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
