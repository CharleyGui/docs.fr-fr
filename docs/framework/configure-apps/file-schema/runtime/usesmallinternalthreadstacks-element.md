---
title: Élément <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74678089bb1b19295983064eb7ad54fbf0a1e361
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663385"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="821a8-102">\<UseSmallInternalThreadStacks >, élément</span><span class="sxs-lookup"><span data-stu-id="821a8-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="821a8-103">Demande que le common language runtime (CLR) réduit l’utilisation de la mémoire en spécifiant des tailles de pile explicites lorsqu’il crée certains threads qu’il utilise en interne, au lieu d’utiliser la taille de pile par défaut pour ces threads.</span><span class="sxs-lookup"><span data-stu-id="821a8-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="821a8-104">\<Élément de > de configuration</span><span class="sxs-lookup"><span data-stu-id="821a8-104">\<configuration> Element</span></span>  
<span data-ttu-id="821a8-105">\<Élément > du Runtime</span><span class="sxs-lookup"><span data-stu-id="821a8-105">\<runtime> Element</span></span>  
<span data-ttu-id="821a8-106">\<UseSmallInternalThreadStacks >, élément</span><span class="sxs-lookup"><span data-stu-id="821a8-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="821a8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="821a8-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="821a8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="821a8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="821a8-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="821a8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="821a8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="821a8-110">Attributes</span></span>  
  
|<span data-ttu-id="821a8-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="821a8-111">Attribute</span></span>|<span data-ttu-id="821a8-112">Description</span><span class="sxs-lookup"><span data-stu-id="821a8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="821a8-113">enabled</span><span class="sxs-lookup"><span data-stu-id="821a8-113">enabled</span></span>|<span data-ttu-id="821a8-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="821a8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="821a8-115">Spécifie s’il faut demander que le CLR utilise des tailles de pile explicites au lieu de la taille de la pile par défaut lorsqu’il crée certains threads qu’il utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="821a8-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="821a8-116">Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.</span><span class="sxs-lookup"><span data-stu-id="821a8-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="821a8-117">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="821a8-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="821a8-118">`Value`</span><span class="sxs-lookup"><span data-stu-id="821a8-118">Value</span></span>|<span data-ttu-id="821a8-119">Description</span><span class="sxs-lookup"><span data-stu-id="821a8-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="821a8-120">true</span><span class="sxs-lookup"><span data-stu-id="821a8-120">true</span></span>|<span data-ttu-id="821a8-121">Demander des tailles de pile explicites.</span><span class="sxs-lookup"><span data-stu-id="821a8-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="821a8-122">false</span><span class="sxs-lookup"><span data-stu-id="821a8-122">false</span></span>|<span data-ttu-id="821a8-123">Utilisez la taille de pile par défaut.</span><span class="sxs-lookup"><span data-stu-id="821a8-123">Use the default stack size.</span></span> <span data-ttu-id="821a8-124">Il s’agit de la valeur par défaut pour le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="821a8-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="821a8-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="821a8-125">Child Elements</span></span>  
 <span data-ttu-id="821a8-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="821a8-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="821a8-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="821a8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="821a8-128">Élément</span><span class="sxs-lookup"><span data-stu-id="821a8-128">Element</span></span>|<span data-ttu-id="821a8-129">Description</span><span class="sxs-lookup"><span data-stu-id="821a8-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="821a8-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="821a8-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="821a8-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="821a8-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="821a8-132">Notes</span><span class="sxs-lookup"><span data-stu-id="821a8-132">Remarks</span></span>  
 <span data-ttu-id="821a8-133">Cet élément de configuration est utilisé pour demander une utilisation réduite de la mémoire virtuelle dans un processus, car les tailles de thread explicites utilisées par le CLR pour ses threads internes, si la demande est honorée, sont inférieures à la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="821a8-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="821a8-134">Cet élément de configuration est une demande au CLR plutôt qu’une exigence absolue.</span><span class="sxs-lookup"><span data-stu-id="821a8-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="821a8-135">Dans le .NET Framework 4, la demande est honorée uniquement pour l’architecture x86.</span><span class="sxs-lookup"><span data-stu-id="821a8-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="821a8-136">Cet élément peut être complètement ignoré dans les futures versions du CLR ou remplacé par des tailles de pile explicites qui sont toujours utilisées pour les threads internes sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="821a8-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="821a8-137">La spécification de cet élément de configuration pour la fiabilité pour une plus petite utilisation de la mémoire virtuelle si le CLR honore la demande, parce que les plus petites tailles de pile peuvent potentiellement rendre les débordements de pile plus probables.</span><span class="sxs-lookup"><span data-stu-id="821a8-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="821a8-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="821a8-138">Example</span></span>  
 <span data-ttu-id="821a8-139">L’exemple suivant montre comment demander que le CLR utilise des tailles de pile explicites pour certains threads qu’il utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="821a8-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="821a8-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="821a8-140">See also</span></span>

- [<span data-ttu-id="821a8-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="821a8-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="821a8-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="821a8-142">Configuration File Schema</span></span>](../index.md)
