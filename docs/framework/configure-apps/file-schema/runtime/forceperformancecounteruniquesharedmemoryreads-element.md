---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: efa6dce1035f7d2cf63b74c6a03d911b5dede722
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116949"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="1abc1-102">\<élément forcePerformanceCounterUniqueSharedMemoryReads ></span><span class="sxs-lookup"><span data-stu-id="1abc1-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="1abc1-103">Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="1abc1-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="1abc1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1abc1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1abc1-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1abc1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1abc1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads** ></span><span class="sxs-lookup"><span data-stu-id="1abc1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abc1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1abc1-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1abc1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1abc1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1abc1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1abc1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1abc1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1abc1-110">Attributes</span></span>  
  
|<span data-ttu-id="1abc1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="1abc1-111">Attribute</span></span>|<span data-ttu-id="1abc1-112">Description</span><span class="sxs-lookup"><span data-stu-id="1abc1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1abc1-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="1abc1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1abc1-114">Indique si PerfCounter. dll utilise le paramètre de Registre CategoryOptions pour déterminer s’il faut charger les données du compteur de performance à partir de la mémoire partagée ou de la mémoire globale spécifique à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="1abc1-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1abc1-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="1abc1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1abc1-116">valeur</span><span class="sxs-lookup"><span data-stu-id="1abc1-116">Value</span></span>|<span data-ttu-id="1abc1-117">Description</span><span class="sxs-lookup"><span data-stu-id="1abc1-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1abc1-118">PerfCounter. dll n’utilise pas le paramètre de Registre CategoryOptions. il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1abc1-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="1abc1-119">PerfCounter. dll utilise le paramètre de Registre CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="1abc1-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1abc1-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1abc1-120">Child Elements</span></span>  
 <span data-ttu-id="1abc1-121">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="1abc1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1abc1-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1abc1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1abc1-123">Élément</span><span class="sxs-lookup"><span data-stu-id="1abc1-123">Element</span></span>|<span data-ttu-id="1abc1-124">Description</span><span class="sxs-lookup"><span data-stu-id="1abc1-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1abc1-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1abc1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1abc1-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1abc1-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1abc1-127">Notes</span><span class="sxs-lookup"><span data-stu-id="1abc1-127">Remarks</span></span>  
 <span data-ttu-id="1abc1-128">Dans les versions du .NET Framework avant le .NET Framework 4, la version de PerfCounter. dll qui a été chargée correspond au runtime qui a été chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1abc1-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="1abc1-129">Si le .NET Framework version 1,1 et le .NET Framework 2,0 ont été installés sur un ordinateur, une application .NET Framework 1,1 chargera la version .NET Framework 1,1 de PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="1abc1-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="1abc1-130">À partir du .NET Framework 4, la dernière version installée de PerfCounter. dll est chargée.</span><span class="sxs-lookup"><span data-stu-id="1abc1-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="1abc1-131">Cela signifie qu’une application .NET Framework 1,1 chargera la version .NET Framework 4 de PerfCounter. dll si le .NET Framework 4 est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1abc1-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="1abc1-132">À partir du .NET Framework 4, lors de l’utilisation de compteurs de performance, PerfCounter. dll vérifie l’entrée de Registre CategoryOptions pour chaque fournisseur afin de déterminer si elle doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="1abc1-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="1abc1-133">Le .NET Framework 1,1 PerfCounter. dll ne lit pas cette entrée de Registre, car il n’est pas conscient de la mémoire partagée propre à la catégorie ; Il lit toujours à partir de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="1abc1-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="1abc1-134">Pour la compatibilité descendante, le .NET Framework 4 PerfCounter. dll ne vérifie pas l’entrée de Registre CategoryOptions lors de l’exécution dans une application .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="1abc1-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="1abc1-135">Elle utilise simplement la mémoire partagée globale, comme le .NET Framework 1,1 PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="1abc1-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="1abc1-136">Toutefois, vous pouvez indiquer au .NET Framework 4 PerfCounter. dll de vérifier le paramètre de registre en activant l’élément `<forcePerformanceCounterUniqueSharedMemoryReads>`.</span><span class="sxs-lookup"><span data-stu-id="1abc1-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1abc1-137">L’activation de l’élément `<forcePerformanceCounterUniqueSharedMemoryReads>` ne garantit pas que la mémoire partagée propre à la catégorie sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="1abc1-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="1abc1-138">Si vous affectez la valeur `true`, PerfCounter. dll fait référence au paramètre de Registre CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="1abc1-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="1abc1-139">Le paramètre par défaut pour CategoryOptions consiste à utiliser la mémoire partagée propre à la catégorie. Toutefois, vous pouvez modifier CategoryOptions pour indiquer que la mémoire partagée globale doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="1abc1-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="1abc1-140">La clé de Registre qui contient le paramètre CategoryOptions est HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="1abc1-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="1abc1-141">Par défaut, CategoryOptions a la valeur 3, ce qui indique à PerfCounter. dll d’utiliser la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="1abc1-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="1abc1-142">Si CategoryOptions a la valeur 0, PerfCounter. dll utilise la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="1abc1-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="1abc1-143">Les données d’instance sont réutilisées uniquement si le nom de l’instance en cours de création est identique à l’instance réutilisée.</span><span class="sxs-lookup"><span data-stu-id="1abc1-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="1abc1-144">Toutes les versions seront en mesure d’écrire dans la catégorie.</span><span class="sxs-lookup"><span data-stu-id="1abc1-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="1abc1-145">Si CategoryOptions a la valeur 1, la mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de la catégorie a la même longueur que la catégorie réutilisée.</span><span class="sxs-lookup"><span data-stu-id="1abc1-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="1abc1-146">Les paramètres 0 et 1 peuvent entraîner des fuites de mémoire et la saturation de la mémoire du compteur de performances.</span><span class="sxs-lookup"><span data-stu-id="1abc1-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1abc1-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="1abc1-147">Example</span></span>  
 <span data-ttu-id="1abc1-148">L’exemple suivant montre comment spécifier que PerfCounter. dll doit faire référence à l’entrée du Registre CategoryOptions pour déterminer si elle doit utiliser la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="1abc1-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1abc1-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1abc1-149">See also</span></span>

- [<span data-ttu-id="1abc1-150">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="1abc1-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1abc1-151">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="1abc1-151">Configuration File Schema</span></span>](../index.md)
