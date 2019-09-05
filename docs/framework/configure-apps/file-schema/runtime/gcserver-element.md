---
title: Élément <gcServer>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa03179df1cd2595b4be428106dd3ec10b309317
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252549"
---
# <a name="gcserver-element"></a><span data-ttu-id="b50c7-102">\<gcServer >, élément</span><span class="sxs-lookup"><span data-stu-id="b50c7-102">\<gcServer> Element</span></span>
<span data-ttu-id="b50c7-103">Spécifie si le common language runtime exécute le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="b50c7-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
<span data-ttu-id="b50c7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b50c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b50c7-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b50c7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b50c7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcServer>**</span><span class="sxs-lookup"><span data-stu-id="b50c7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcServer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50c7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b50c7-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b50c7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b50c7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b50c7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b50c7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b50c7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b50c7-110">Attributes</span></span>  
  
|<span data-ttu-id="b50c7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b50c7-111">Attribute</span></span>|<span data-ttu-id="b50c7-112">Description</span><span class="sxs-lookup"><span data-stu-id="b50c7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b50c7-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b50c7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b50c7-114">Spécifie si le runtime exécute le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="b50c7-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b50c7-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="b50c7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b50c7-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="b50c7-116">Value</span></span>|<span data-ttu-id="b50c7-117">Description</span><span class="sxs-lookup"><span data-stu-id="b50c7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b50c7-118">N'exécute pas le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="b50c7-118">Does not run server garbage collection.</span></span> <span data-ttu-id="b50c7-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b50c7-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b50c7-120">Exécute le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="b50c7-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b50c7-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b50c7-121">Child Elements</span></span>  
 <span data-ttu-id="b50c7-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b50c7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b50c7-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b50c7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b50c7-124">Élément</span><span class="sxs-lookup"><span data-stu-id="b50c7-124">Element</span></span>|<span data-ttu-id="b50c7-125">Description</span><span class="sxs-lookup"><span data-stu-id="b50c7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b50c7-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b50c7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b50c7-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b50c7-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b50c7-128">Notes</span><span class="sxs-lookup"><span data-stu-id="b50c7-128">Remarks</span></span>  
 <span data-ttu-id="b50c7-129">Le common language runtime (ou CLR) prend en charge deux types de garbage collection : le garbage collection côté station de travail, qui est disponible sur tous les systèmes, et le garbage collection côté serveur, qui est disponible sur les systèmes multiprocesseurs.</span><span class="sxs-lookup"><span data-stu-id="b50c7-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="b50c7-130">Utilisez l’élément `<gcServer>` pour contrôler le type de garbage collection effectué par le CLR.</span><span class="sxs-lookup"><span data-stu-id="b50c7-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="b50c7-131">Utilisez la propriété <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> pour déterminer si le garbage collection côté serveur est activé.</span><span class="sxs-lookup"><span data-stu-id="b50c7-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="b50c7-132">Pour les ordinateurs monoprocesseurs, le garbage collection côté station de travail configuré par défaut représente normalement l'option la plus rapide.</span><span class="sxs-lookup"><span data-stu-id="b50c7-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="b50c7-133">L'option station de travail ou serveur peut être utilisée pour les ordinateurs biprocesseurs.</span><span class="sxs-lookup"><span data-stu-id="b50c7-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="b50c7-134">Le garbage collection côté serveur est normalement l'option la plus rapide pour les ordinateurs comptant plus de deux processeurs.</span><span class="sxs-lookup"><span data-stu-id="b50c7-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="b50c7-135">Cet élément peut être défini uniquement dans le fichier de configuration de l'application (il est ignoré s'il est défini dans le fichier de configuration de l'ordinateur).</span><span class="sxs-lookup"><span data-stu-id="b50c7-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b50c7-136">Dans .NET Framework 4 et les versions antérieures, le garbage collection simultané n'est pas disponible si le garbage collection côté serveur est activé.</span><span class="sxs-lookup"><span data-stu-id="b50c7-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="b50c7-137">À partir de la .NET Framework 4,5, le garbage collection du serveur est simultané.</span><span class="sxs-lookup"><span data-stu-id="b50c7-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="b50c7-138">Pour utiliser des garbage collection de serveur non simultanées, `<gcServer>` affectez `true` à l’élément la valeur et `false`à l' [ \<élément gcConcurrent >](gcconcurrent-element.md) la valeur.</span><span class="sxs-lookup"><span data-stu-id="b50c7-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b50c7-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="b50c7-139">Example</span></span>  
 <span data-ttu-id="b50c7-140">L’exemple suivant active le garbage collection côté serveur.</span><span class="sxs-lookup"><span data-stu-id="b50c7-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b50c7-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b50c7-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b50c7-142">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="b50c7-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b50c7-143">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b50c7-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b50c7-144">Pour désactiver les garbage collection simultanées</span><span class="sxs-lookup"><span data-stu-id="b50c7-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
