---
title: Élément <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 2fd776ce8605e6dcf288dcb3852ded16638a1873
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73114924"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="69eba-102">Élément \<UseSmallInternalThreadStacks></span><span class="sxs-lookup"><span data-stu-id="69eba-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="69eba-103">Demande que le common language runtime (CLR) réduit l’utilisation de la mémoire en spécifiant des tailles de pile explicites lorsqu’il crée certains threads qu’il utilise en interne, au lieu d’utiliser la taille de pile par défaut pour ces threads.</span><span class="sxs-lookup"><span data-stu-id="69eba-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="69eba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69eba-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69eba-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="69eba-105">Attributes and Elements</span></span>  
 <span data-ttu-id="69eba-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="69eba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69eba-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="69eba-107">Attributes</span></span>  
  
|<span data-ttu-id="69eba-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="69eba-108">Attribute</span></span>|<span data-ttu-id="69eba-109">Description</span><span class="sxs-lookup"><span data-stu-id="69eba-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69eba-110">enabled</span><span class="sxs-lookup"><span data-stu-id="69eba-110">enabled</span></span>|<span data-ttu-id="69eba-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="69eba-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="69eba-112">Spécifie s’il faut demander que le CLR utilise des tailles de pile explicites au lieu de la taille de la pile par défaut lorsqu’il crée certains threads qu’il utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="69eba-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="69eba-113">Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.</span><span class="sxs-lookup"><span data-stu-id="69eba-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="69eba-114">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="69eba-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="69eba-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="69eba-115">Value</span></span>|<span data-ttu-id="69eba-116">Description</span><span class="sxs-lookup"><span data-stu-id="69eba-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="69eba-117">true</span><span class="sxs-lookup"><span data-stu-id="69eba-117">true</span></span>|<span data-ttu-id="69eba-118">Demander des tailles de pile explicites.</span><span class="sxs-lookup"><span data-stu-id="69eba-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="69eba-119">false</span><span class="sxs-lookup"><span data-stu-id="69eba-119">false</span></span>|<span data-ttu-id="69eba-120">Utilisez la taille de pile par défaut.</span><span class="sxs-lookup"><span data-stu-id="69eba-120">Use the default stack size.</span></span> <span data-ttu-id="69eba-121">Il s’agit de la valeur par défaut pour le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="69eba-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69eba-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="69eba-122">Child Elements</span></span>  
 <span data-ttu-id="69eba-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="69eba-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69eba-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="69eba-124">Parent Elements</span></span>  
  
|<span data-ttu-id="69eba-125">Élément</span><span class="sxs-lookup"><span data-stu-id="69eba-125">Element</span></span>|<span data-ttu-id="69eba-126">Description</span><span class="sxs-lookup"><span data-stu-id="69eba-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="69eba-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69eba-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="69eba-128">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="69eba-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69eba-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="69eba-129">Remarks</span></span>  
 <span data-ttu-id="69eba-130">Cet élément de configuration est utilisé pour demander une utilisation réduite de la mémoire virtuelle dans un processus, car les tailles de thread explicites utilisées par le CLR pour ses threads internes, si la demande est honorée, sont inférieures à la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="69eba-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="69eba-131">Cet élément de configuration est une demande au CLR plutôt qu’une exigence absolue.</span><span class="sxs-lookup"><span data-stu-id="69eba-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="69eba-132">Dans le .NET Framework 4, la demande est honorée uniquement pour l’architecture x86.</span><span class="sxs-lookup"><span data-stu-id="69eba-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="69eba-133">Cet élément peut être complètement ignoré dans les futures versions du CLR ou remplacé par des tailles de pile explicites qui sont toujours utilisées pour les threads internes sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="69eba-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="69eba-134">La spécification de cet élément de configuration pour la fiabilité pour une plus petite utilisation de la mémoire virtuelle si le CLR honore la demande, parce que les plus petites tailles de pile peuvent potentiellement rendre les débordements de pile plus probables.</span><span class="sxs-lookup"><span data-stu-id="69eba-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69eba-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="69eba-135">Example</span></span>  
 <span data-ttu-id="69eba-136">L’exemple suivant montre comment demander que le CLR utilise des tailles de pile explicites pour certains threads qu’il utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="69eba-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69eba-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69eba-137">See also</span></span>

- [<span data-ttu-id="69eba-138">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="69eba-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="69eba-139">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="69eba-139">Configuration File Schema</span></span>](../index.md)
