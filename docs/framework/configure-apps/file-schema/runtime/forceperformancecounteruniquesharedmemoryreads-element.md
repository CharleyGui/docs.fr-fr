---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 719448ba3de2aca0621fc17b9fadbdd3b8588f2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178240"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="7b583-102">Élément \<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="7b583-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>

<span data-ttu-id="7b583-103">Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="7b583-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="7b583-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b583-104">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b583-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7b583-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7b583-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7b583-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b583-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7b583-107">Attributes</span></span>  
  
|<span data-ttu-id="7b583-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7b583-108">Attribute</span></span>|<span data-ttu-id="7b583-109">Description</span><span class="sxs-lookup"><span data-stu-id="7b583-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7b583-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="7b583-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="7b583-111">Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions pour déterminer s’il faut charger les données de compteur de performance à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.</span><span class="sxs-lookup"><span data-stu-id="7b583-111">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7b583-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="7b583-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="7b583-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="7b583-113">Value</span></span>|<span data-ttu-id="7b583-114">Description</span><span class="sxs-lookup"><span data-stu-id="7b583-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7b583-115">PerfCounter.dll n’utilise pas le paramètre de Registre CategoryOptions, il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7b583-115">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="7b583-116">PerfCounter.dll utilise le paramètre de Registre CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="7b583-116">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b583-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7b583-117">Child Elements</span></span>  

 <span data-ttu-id="7b583-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7b583-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b583-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7b583-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b583-120">Élément</span><span class="sxs-lookup"><span data-stu-id="7b583-120">Element</span></span>|<span data-ttu-id="7b583-121">Description</span><span class="sxs-lookup"><span data-stu-id="7b583-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7b583-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b583-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7b583-123">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b583-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b583-124">Notes</span><span class="sxs-lookup"><span data-stu-id="7b583-124">Remarks</span></span>  

 <span data-ttu-id="7b583-125">Dans les versions du .NET Framework avant le .NET Framework 4, la version de PerfCounter.dll qui a été chargée correspond au runtime qui a été chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7b583-125">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="7b583-126">Si le .NET Framework version 1,1 et le .NET Framework 2,0 ont été installés sur un ordinateur, une application .NET Framework 1,1 chargera la version .NET Framework 1,1 de PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="7b583-126">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="7b583-127">À partir du .NET Framework 4, la dernière version installée de PerfCounter.dll est chargée.</span><span class="sxs-lookup"><span data-stu-id="7b583-127">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="7b583-128">Cela signifie qu’une application .NET Framework 1,1 chargera la version .NET Framework 4 de PerfCounter.dll si le .NET Framework 4 est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7b583-128">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="7b583-129">À partir du .NET Framework 4, lors de l’utilisation de compteurs de performance, PerfCounter.dll vérifie l’entrée de Registre CategoryOptions pour chaque fournisseur afin de déterminer s’il doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="7b583-129">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="7b583-130">Le .NET Framework 1,1 PerfCounter.dll ne lit pas cette entrée de Registre, car il n’est pas conscient de la mémoire partagée spécifique à la catégorie ; Il lit toujours à partir de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="7b583-130">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="7b583-131">Pour la compatibilité descendante, le .NET Framework 4 PerfCounter.dll ne vérifie pas l’entrée de Registre CategoryOptions lors de l’exécution dans une application .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="7b583-131">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="7b583-132">Elle utilise simplement la mémoire partagée globale, tout comme le .NET Framework 1,1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="7b583-132">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="7b583-133">Toutefois, vous pouvez demander à l' .NET Framework 4 PerfCounter.dll de vérifier le paramètre de registre en activant l' `<forcePerformanceCounterUniqueSharedMemoryReads>` élément.</span><span class="sxs-lookup"><span data-stu-id="7b583-133">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b583-134">L’activation de l' `<forcePerformanceCounterUniqueSharedMemoryReads>` élément ne garantit pas que la mémoire partagée propre à la catégorie sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="7b583-134">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="7b583-135">Si vous affectez à la valeur activé `true` , PerfCounter.dll fait référence uniquement au paramètre de Registre CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="7b583-135">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="7b583-136">Le paramètre par défaut pour CategoryOptions consiste à utiliser la mémoire partagée propre à la catégorie. Toutefois, vous pouvez modifier CategoryOptions pour indiquer que la mémoire partagée globale doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="7b583-136">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="7b583-137">La clé de Registre qui contient le paramètre CategoryOptions est HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<CategoryName \> \Performance.</span><span class="sxs-lookup"><span data-stu-id="7b583-137">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="7b583-138">Par défaut, CategoryOptions a la valeur 3, ce qui indique à PerfCounter.dll d’utiliser la mémoire partagée spécifique à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="7b583-138">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="7b583-139">Si CategoryOptions a la valeur 0, PerfCounter.dll utilise la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="7b583-139">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="7b583-140">Les données d’instance sont réutilisées uniquement si le nom de l’instance en cours de création est identique à l’instance réutilisée.</span><span class="sxs-lookup"><span data-stu-id="7b583-140">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="7b583-141">Toutes les versions seront en mesure d’écrire dans la catégorie.</span><span class="sxs-lookup"><span data-stu-id="7b583-141">All versions will be able to write to the category.</span></span> <span data-ttu-id="7b583-142">Si CategoryOptions a la valeur 1, la mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de la catégorie a la même longueur que la catégorie réutilisée.</span><span class="sxs-lookup"><span data-stu-id="7b583-142">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="7b583-143">Les paramètres 0 et 1 peuvent entraîner des fuites de mémoire et la saturation de la mémoire du compteur de performances.</span><span class="sxs-lookup"><span data-stu-id="7b583-143">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b583-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="7b583-144">Example</span></span>  

 <span data-ttu-id="7b583-145">L’exemple suivant montre comment spécifier que PerfCounter.dll doit référencer l’entrée du Registre CategoryOptions pour déterminer si elle doit utiliser la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="7b583-145">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b583-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b583-146">See also</span></span>

- [<span data-ttu-id="7b583-147">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="7b583-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7b583-148">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="7b583-148">Configuration File Schema</span></span>](../index.md)
