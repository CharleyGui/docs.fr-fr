---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102890"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="ac4ad-102">Élément \<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="ac4ad-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="ac4ad-103">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="ac4ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac4ad-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac4ad-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ac4ad-105">Attributes and Elements</span></span>

<span data-ttu-id="ac4ad-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac4ad-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac4ad-107">Attributes</span></span>

|<span data-ttu-id="ac4ad-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac4ad-108">Attribute</span></span>|<span data-ttu-id="ac4ad-109">Description</span><span class="sxs-lookup"><span data-stu-id="ac4ad-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ac4ad-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac4ad-111">Indique si le garbage collection prend en charge plusieurs groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ac4ad-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="ac4ad-112">enabled Attribute</span></span>

|<span data-ttu-id="ac4ad-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="ac4ad-113">Value</span></span>|<span data-ttu-id="ac4ad-114">Description</span><span class="sxs-lookup"><span data-stu-id="ac4ad-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ac4ad-115">Le garbage collection ne prend pas en charge plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="ac4ad-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="ac4ad-117">Le garbage collection prend en charge plusieurs groupes de PROCESSEURs, si le serveur garbage collection est activé.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ac4ad-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac4ad-118">Child Elements</span></span>

<span data-ttu-id="ac4ad-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac4ad-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac4ad-120">Parent Elements</span></span>

|<span data-ttu-id="ac4ad-121">Élément</span><span class="sxs-lookup"><span data-stu-id="ac4ad-121">Element</span></span>|<span data-ttu-id="ac4ad-122">Description</span><span class="sxs-lookup"><span data-stu-id="ac4ad-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ac4ad-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ac4ad-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ac4ad-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ac4ad-125">Remarks</span></span>

<span data-ttu-id="ac4ad-126">Quand un ordinateur a plusieurs groupes d’UC et que la garbage collection du serveur est activée (Voir l' [\<gcServer>](gcserver-element.md) élément), l’activation de cet élément étend garbage collection sur tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et de l’équilibrage des tas.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="ac4ad-127">Cet élément s’applique uniquement aux threads garbage collections.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="ac4ad-128">Pour permettre au runtime de distribuer des threads utilisateur sur tous les groupes de PROCESSEURs, vous devez également activer l' [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="ac4ad-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac4ad-129">Example</span></span>

<span data-ttu-id="ac4ad-130">L’exemple suivant montre comment activer garbage collection pour plusieurs groupes d’UC.</span><span class="sxs-lookup"><span data-stu-id="ac4ad-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ac4ad-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac4ad-131">See also</span></span>

- [<span data-ttu-id="ac4ad-132">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ac4ad-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac4ad-133">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ac4ad-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ac4ad-134">Désactiver les garbage collection simultanées</span><span class="sxs-lookup"><span data-stu-id="ac4ad-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="ac4ad-135">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="ac4ad-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
