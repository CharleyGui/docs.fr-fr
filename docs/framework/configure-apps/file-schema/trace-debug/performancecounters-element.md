---
title: Élément <performanceCounters>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697153"
---
# <a name="performancecounters-element"></a><span data-ttu-id="3f8bc-102">Élément \<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="3f8bc-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="3f8bc-103">Spécifie la taille de la mémoire globale partagée par les compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-103">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="3f8bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f8bc-104">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f8bc-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f8bc-105">Attributes and Elements</span></span>

<span data-ttu-id="3f8bc-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f8bc-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f8bc-107">Attributes</span></span>

|<span data-ttu-id="3f8bc-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f8bc-108">Attribute</span></span>|<span data-ttu-id="3f8bc-109">Description</span><span class="sxs-lookup"><span data-stu-id="3f8bc-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3f8bc-110">FileMappingSize</span><span class="sxs-lookup"><span data-stu-id="3f8bc-110">filemappingsize</span></span>|<span data-ttu-id="3f8bc-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f8bc-112">Spécifie la taille, en octets, de la mémoire globale partagée par les compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-112">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="3f8bc-113">La valeur par défaut est 524288.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-113">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3f8bc-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f8bc-114">Child Elements</span></span>

<span data-ttu-id="3f8bc-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3f8bc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f8bc-116">Parent Elements</span></span>

|<span data-ttu-id="3f8bc-117">Élément</span><span class="sxs-lookup"><span data-stu-id="3f8bc-117">Element</span></span>|<span data-ttu-id="3f8bc-118">Description</span><span class="sxs-lookup"><span data-stu-id="3f8bc-118">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="3f8bc-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="3f8bc-120">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-120">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f8bc-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f8bc-121">Remarks</span></span>

<span data-ttu-id="3f8bc-122">Les compteurs de performance utilisent un fichier mappé en mémoire, ou mémoire partagée, pour publier les données de performances.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-122">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="3f8bc-123">La taille de la mémoire partagée détermine le nombre d’instances qui peuvent être utilisées à la fois.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-123">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="3f8bc-124">Il existe deux types de mémoire partagée : la mémoire partagée globale et la mémoire partagée séparée.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-124">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="3f8bc-125">La mémoire partagée globale est utilisée par toutes les catégories de compteurs de performance installées avec les versions .NET Framework 1,0 ou 1,1.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-125">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="3f8bc-126">Les catégories de compteurs de performance installées avec la version de .NET Framework 2,0 utilisent une mémoire partagée distincte, chaque catégorie de compteur de performances ayant sa propre mémoire.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-126">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="3f8bc-127">La taille de la mémoire partagée globale ne peut être définie qu’avec un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-127">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="3f8bc-128">La taille par défaut est de 524 288 octets, la taille maximale est de 33 554 432 octets et la taille minimale est de 32 768 octets.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-128">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="3f8bc-129">Étant donné que la mémoire partagée globale est partagée par tous les processus et toutes les catégories, le premier créateur spécifie la taille.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-129">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="3f8bc-130">Si vous définissez la taille dans votre fichier de configuration de l’application, cette taille est utilisée uniquement si votre application est la première application qui provoque l’exécution des compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-130">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="3f8bc-131">Par conséquent, l’emplacement correct pour spécifier la `filemappingsize` valeur est le fichier machine. config.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-131">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="3f8bc-132">La mémoire dans la mémoire partagée globale ne peut pas être libérée par des compteurs de performances individuels. par conséquent, la mémoire partagée globale finit par être épuisée si un grand nombre d’instances de compteur de performance avec des noms différents sont créés.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-132">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="3f8bc-133">Pour la taille de la mémoire partagée séparée, la valeur DWORD FileMappingSize dans la clé de Registre HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services \\ *\<category name>* \Performance est référencée en premier, suivie de la valeur spécifiée pour la mémoire partagée globale dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-133">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="3f8bc-134">Si la valeur FileMappingSize n’existe pas, la taille de la mémoire partagée séparée est définie sur un quatrième (1/4) du paramètre global dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3f8bc-134">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f8bc-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f8bc-135">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
