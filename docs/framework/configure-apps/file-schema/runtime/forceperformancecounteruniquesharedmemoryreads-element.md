---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54bccd134a2f77925e80bfc681770b28c05f77a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252602"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="38ec2-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="38ec2-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="38ec2-103">Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="38ec2-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="38ec2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38ec2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38ec2-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="38ec2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="38ec2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads>**</span><span class="sxs-lookup"><span data-stu-id="38ec2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38ec2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38ec2-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38ec2-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38ec2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="38ec2-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="38ec2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38ec2-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="38ec2-110">Attributes</span></span>  
  
|<span data-ttu-id="38ec2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="38ec2-111">Attribute</span></span>|<span data-ttu-id="38ec2-112">Description</span><span class="sxs-lookup"><span data-stu-id="38ec2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="38ec2-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="38ec2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="38ec2-114">Indique si PerfCounter. dll utilise le paramètre de Registre CategoryOptions pour déterminer s’il faut charger les données du compteur de performance à partir de la mémoire partagée ou de la mémoire globale spécifique à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="38ec2-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="38ec2-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="38ec2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="38ec2-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="38ec2-116">Value</span></span>|<span data-ttu-id="38ec2-117">Description</span><span class="sxs-lookup"><span data-stu-id="38ec2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="38ec2-118">PerfCounter. dll n’utilise pas le paramètre de Registre CategoryOptions. il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="38ec2-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="38ec2-119">PerfCounter. dll utilise le paramètre de Registre CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="38ec2-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38ec2-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38ec2-120">Child Elements</span></span>  
 <span data-ttu-id="38ec2-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38ec2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38ec2-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38ec2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="38ec2-123">Élément</span><span class="sxs-lookup"><span data-stu-id="38ec2-123">Element</span></span>|<span data-ttu-id="38ec2-124">Description</span><span class="sxs-lookup"><span data-stu-id="38ec2-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="38ec2-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38ec2-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="38ec2-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="38ec2-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38ec2-127">Notes</span><span class="sxs-lookup"><span data-stu-id="38ec2-127">Remarks</span></span>  
 <span data-ttu-id="38ec2-128">Dans les versions du .NET Framework avant le .NET Framework 4, la version de PerfCounter. dll qui a été chargée correspond au runtime qui a été chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="38ec2-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="38ec2-129">Si le .NET Framework version 1,1 et le .NET Framework 2,0 ont été installés sur un ordinateur, une application .NET Framework 1,1 chargera la version .NET Framework 1,1 de PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="38ec2-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="38ec2-130">À partir du .NET Framework 4, la dernière version installée de PerfCounter. dll est chargée.</span><span class="sxs-lookup"><span data-stu-id="38ec2-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="38ec2-131">Cela signifie qu’une application .NET Framework 1,1 chargera la version .NET Framework 4 de PerfCounter. dll si le .NET Framework 4 est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38ec2-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="38ec2-132">À partir du .NET Framework 4, lors de l’utilisation de compteurs de performance, PerfCounter. dll vérifie l’entrée de Registre CategoryOptions pour chaque fournisseur afin de déterminer si elle doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="38ec2-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="38ec2-133">Le .NET Framework 1,1 PerfCounter. dll ne lit pas cette entrée de Registre, car il n’est pas conscient de la mémoire partagée propre à la catégorie ; Il lit toujours à partir de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="38ec2-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="38ec2-134">Pour la compatibilité descendante, le .NET Framework 4 PerfCounter. dll ne vérifie pas l’entrée de Registre CategoryOptions lors de l’exécution dans une application .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="38ec2-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="38ec2-135">Elle utilise simplement la mémoire partagée globale, comme le .NET Framework 1,1 PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="38ec2-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="38ec2-136">Toutefois, vous pouvez indiquer au .NET Framework 4 PerfCounter. dll de vérifier le paramètre de registre en activant `<forcePerformanceCounterUniqueSharedMemoryReads>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="38ec2-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38ec2-137">L’activation `<forcePerformanceCounterUniqueSharedMemoryReads>` de l’élément ne garantit pas que la mémoire partagée propre à la catégorie sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="38ec2-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="38ec2-138">Si vous affectez la valeur à `true` activé, PerfCounter. dll fait référence au paramètre de Registre CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="38ec2-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="38ec2-139">Le paramètre par défaut pour CategoryOptions consiste à utiliser la mémoire partagée propre à la catégorie. Toutefois, vous pouvez modifier CategoryOptions pour indiquer que la mémoire partagée globale doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="38ec2-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="38ec2-140">La clé de Registre qui contient le paramètre CategoryOptions est\\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services <\>CategoryName \Performance.</span><span class="sxs-lookup"><span data-stu-id="38ec2-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="38ec2-141">Par défaut, CategoryOptions a la valeur 3, ce qui indique à PerfCounter. dll d’utiliser la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="38ec2-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="38ec2-142">Si CategoryOptions a la valeur 0, PerfCounter. dll utilise la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="38ec2-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="38ec2-143">Les données d’instance sont réutilisées uniquement si le nom de l’instance en cours de création est identique à l’instance réutilisée.</span><span class="sxs-lookup"><span data-stu-id="38ec2-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="38ec2-144">Toutes les versions seront en mesure d’écrire dans la catégorie.</span><span class="sxs-lookup"><span data-stu-id="38ec2-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="38ec2-145">Si CategoryOptions a la valeur 1, la mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de la catégorie a la même longueur que la catégorie réutilisée.</span><span class="sxs-lookup"><span data-stu-id="38ec2-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="38ec2-146">Les paramètres 0 et 1 peuvent entraîner des fuites de mémoire et la saturation de la mémoire du compteur de performances.</span><span class="sxs-lookup"><span data-stu-id="38ec2-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38ec2-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="38ec2-147">Example</span></span>  
 <span data-ttu-id="38ec2-148">L’exemple suivant montre comment spécifier que PerfCounter. dll doit faire référence à l’entrée du Registre CategoryOptions pour déterminer si elle doit utiliser la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="38ec2-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38ec2-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38ec2-149">See also</span></span>

- [<span data-ttu-id="38ec2-150">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="38ec2-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="38ec2-151">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="38ec2-151">Configuration File Schema</span></span>](../index.md)
