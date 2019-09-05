---
title: Élément <disableCachingBindingFailures>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5b45ea4b30677d17e72685b16c19f9192c8c144
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252680"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="4dec2-102">\<disableCachingBindingFailures >, élément</span><span class="sxs-lookup"><span data-stu-id="4dec2-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="4dec2-103">Spécifie s’il faut désactiver la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
<span data-ttu-id="4dec2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4dec2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4dec2-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="4dec2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="4dec2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCachingBindingFailures>**</span><span class="sxs-lookup"><span data-stu-id="4dec2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dec2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dec2-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dec2-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4dec2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4dec2-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4dec2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dec2-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4dec2-110">Attributes</span></span>  
  
|<span data-ttu-id="4dec2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="4dec2-111">Attribute</span></span>|<span data-ttu-id="4dec2-112">Description</span><span class="sxs-lookup"><span data-stu-id="4dec2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dec2-113">enabled</span><span class="sxs-lookup"><span data-stu-id="4dec2-113">enabled</span></span>|<span data-ttu-id="4dec2-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4dec2-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="4dec2-115">Spécifie s’il faut désactiver la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4dec2-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="4dec2-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="4dec2-117">`Value`</span><span class="sxs-lookup"><span data-stu-id="4dec2-117">Value</span></span>|<span data-ttu-id="4dec2-118">Description</span><span class="sxs-lookup"><span data-stu-id="4dec2-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4dec2-119">0</span><span class="sxs-lookup"><span data-stu-id="4dec2-119">0</span></span>|<span data-ttu-id="4dec2-120">Ne désactivez pas la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="4dec2-121">Il s’agit du comportement de liaison par défaut à partir de la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4dec2-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="4dec2-122">1</span><span class="sxs-lookup"><span data-stu-id="4dec2-122">1</span></span>|<span data-ttu-id="4dec2-123">Désactivez la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="4dec2-124">Ce paramètre revient au comportement de liaison du .NET Framework version 1,1.</span><span class="sxs-lookup"><span data-stu-id="4dec2-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dec2-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4dec2-125">Child Elements</span></span>  
 <span data-ttu-id="4dec2-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4dec2-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dec2-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4dec2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4dec2-128">Élément</span><span class="sxs-lookup"><span data-stu-id="4dec2-128">Element</span></span>|<span data-ttu-id="4dec2-129">Description</span><span class="sxs-lookup"><span data-stu-id="4dec2-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4dec2-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4dec2-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4dec2-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dec2-132">Notes</span><span class="sxs-lookup"><span data-stu-id="4dec2-132">Remarks</span></span>  
 <span data-ttu-id="4dec2-133">À partir de la version 2,0 de .NET Framework, le comportement par défaut pour le chargement des assemblys consiste à mettre en cache toutes les erreurs de liaison et de chargement.</span><span class="sxs-lookup"><span data-stu-id="4dec2-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="4dec2-134">Autrement dit, si une tentative de chargement d’un assembly échoue, les demandes suivantes de chargement du même assembly échouent immédiatement, sans aucune tentative de localisation de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4dec2-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="4dec2-135">Cet élément désactive le comportement par défaut pour les échecs de liaison qui se produisent parce que l’assembly est introuvable dans le chemin d’accès de détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="4dec2-136">Ces échecs lèvent <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="4dec2-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="4dec2-137">Certains échecs de liaison et de chargement ne sont pas affectés par cet élément et sont toujours mis en cache.</span><span class="sxs-lookup"><span data-stu-id="4dec2-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="4dec2-138">Ces échecs se produisent parce que l’assembly a été trouvé mais n’a pas pu être chargé.</span><span class="sxs-lookup"><span data-stu-id="4dec2-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="4dec2-139">Elles <xref:System.BadImageFormatException> lèvent <xref:System.IO.FileLoadException>ou.</span><span class="sxs-lookup"><span data-stu-id="4dec2-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="4dec2-140">La liste suivante présente quelques exemples de tels échecs.</span><span class="sxs-lookup"><span data-stu-id="4dec2-140">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="4dec2-141">Si vous essayez de charger un fichier qui n’est pas un assembly valide, les tentatives suivantes de chargement de l’assembly échouent même si le fichier incorrect est remplacé par l’assembly approprié.</span><span class="sxs-lookup"><span data-stu-id="4dec2-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="4dec2-142">Si vous essayez de charger un assembly qui est verrouillé par le système de fichiers, les tentatives suivantes de chargement de l’assembly échouent même après la libération de l’assembly par le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4dec2-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="4dec2-143">Si une ou plusieurs versions de l’assembly que vous tentez de charger se trouvent dans le chemin d’accès de détection, mais que la version spécifique que vous demandez n’est pas parmi celles-ci, les tentatives de chargement ultérieures de cette version échouent même si la version correcte est déplacée dans le chemin d’accès de détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dec2-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="4dec2-144">Example</span></span>  
 <span data-ttu-id="4dec2-145">L’exemple suivant montre comment désactiver la mise en cache des échecs de liaison d’assembly qui se produisent parce que l’assembly n’a pas été trouvé par la détection.</span><span class="sxs-lookup"><span data-stu-id="4dec2-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dec2-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dec2-146">See also</span></span>

- [<span data-ttu-id="4dec2-147">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="4dec2-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4dec2-148">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4dec2-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4dec2-149">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="4dec2-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
