---
title: Élément <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154138"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="5a1b4-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="5a1b4-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="5a1b4-103">Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="5a1b4-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a1b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a1b4-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a1b4-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5a1b4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span><span class="sxs-lookup"><span data-stu-id="5a1b4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a1b4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a1b4-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a1b4-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a1b4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a1b4-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a1b4-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a1b4-110">Attributes</span></span>  
  
|<span data-ttu-id="5a1b4-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a1b4-111">Attribute</span></span>|<span data-ttu-id="5a1b4-112">Description</span><span class="sxs-lookup"><span data-stu-id="5a1b4-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5a1b4-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a1b4-114">Indique si PerfCounter.dll utilise le paramètre du registre CatégorieOptions pour déterminer s’il y a lieu de charger les données de compteur de performance de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5a1b4-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="5a1b4-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5a1b4-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="5a1b4-116">Value</span></span>|<span data-ttu-id="5a1b4-117">Description</span><span class="sxs-lookup"><span data-stu-id="5a1b4-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5a1b4-118">PerfCounter.dll n’utilise pas le paramètre de registre CatégorieOptions C’est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="5a1b4-119">PerfCounter.dll utilise le paramètre de registre CatégorieOptions.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a1b4-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a1b4-120">Child Elements</span></span>  
 <span data-ttu-id="5a1b4-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a1b4-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a1b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5a1b4-123">Élément</span><span class="sxs-lookup"><span data-stu-id="5a1b4-123">Element</span></span>|<span data-ttu-id="5a1b4-124">Description</span><span class="sxs-lookup"><span data-stu-id="5a1b4-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a1b4-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a1b4-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a1b4-127">Notes </span><span class="sxs-lookup"><span data-stu-id="5a1b4-127">Remarks</span></span>  
 <span data-ttu-id="5a1b4-128">Dans les versions du cadre .NET avant le cadre .NET 4, la version de PerfCounter.dll qui a été chargée correspondait au temps d’exécution qui a été chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="5a1b4-129">Si un ordinateur avait à la fois la version cadre .NET 1.1 et le cadre .NET 2.0 installé, une application .NET Framework 1.1 chargerait la version .NET Framework 1.1 de PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="5a1b4-130">En commençant par le cadre .NET 4, la nouvelle version installée de PerfCounter.dll est chargée.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="5a1b4-131">Cela signifie qu’une application .NET Framework 1.1 chargera la version .NET Framework 4 de PerfCounter.dll si le cadre .NET 4 est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="5a1b4-132">En commençant par le cadre .NET 4, lors de la consommation de compteurs de performance, PerfCounter.dll vérifie l’entrée de registre CatégorieOptions pour chaque fournisseur pour déterminer s’il doit lire à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="5a1b4-133">Le cadre .NET 1.1 PerfCounter.dll ne lit pas cette inscription au registre, parce qu’il n’est pas au courant de la mémoire partagée spécifique à la catégorie; il lit toujours de mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="5a1b4-134">Pour la compatibilité rétrograde, le .NET Framework 4 PerfCounter.dll ne vérifie pas l’entrée du registre CatégorieOptions lors de l’exécution dans une application .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="5a1b4-135">Il utilise simplement la mémoire partagée globale, tout comme le cadre .NET 1.1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="5a1b4-136">Toutefois, vous pouvez demander au cadre .NET 4 PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` de vérifier le paramètre du registre en permettant l’élément.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a1b4-137">L’activation de l’élément `<forcePerformanceCounterUniqueSharedMemoryReads>` ne garantit pas que la mémoire partagée spécifique à la catégorie sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="5a1b4-138">Le paramètre activé ne fait que référencer `true` perfCounter.dll au paramètre de registre CatégorieOptions.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="5a1b4-139">Le paramètre par défaut pour CategoryOptions est d’utiliser la mémoire partagée spécifique à la catégorie ; cependant, vous pouvez modifier CatégorieOptions pour indiquer que la mémoire partagée globale doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="5a1b4-140">La clé de registre qui contient le paramètre CategoryOptions est HKEY_LOCAL_MACHINE-Système-CurrentControlSet-Services\\<catégorieName\>'Performance.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="5a1b4-141">Par défaut, CategoryOptions est réglé à 3, qui ordonne à PerfCounter.dll d’utiliser la mémoire partagée spécifique à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="5a1b4-142">Si CategoryOptions est réglé à 0, PerfCounter.dll utilise la mémoire partagée globale.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="5a1b4-143">Les données de instance ne seront réutilisées que si le nom de l’instance créée est identique à l’instance réutilisée.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="5a1b4-144">Toutes les versions pourront écrire à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="5a1b4-145">Si CatégorieOptions est définie à 1, la mémoire partagée globale est utilisée, mais les données d’instance peuvent être réutilisées si le nom de la catégorie est de la même longueur que la catégorie réutilisée.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="5a1b4-146">Les réglages 0 et 1 peuvent entraîner des fuites de mémoire et le remplissage de la mémoire de compteur de performance.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a1b4-147"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5a1b4-147">Example</span></span>  
 <span data-ttu-id="5a1b4-148">L’exemple suivant montre comment spécifier que PerfCounter.dll devrait faire référence à l’entrée du registre CatégorieOptions pour déterminer s’il doit utiliser la mémoire partagée spécifique à la catégorie.</span><span class="sxs-lookup"><span data-stu-id="5a1b4-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a1b4-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a1b4-149">See also</span></span>

- [<span data-ttu-id="5a1b4-150">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="5a1b4-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5a1b4-151">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="5a1b4-151">Configuration File Schema</span></span>](../index.md)
