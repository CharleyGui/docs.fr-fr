---
title: Élément <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154125"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="c10a3-102">\<gcAllowVeryLargeObjects> Element</span><span class="sxs-lookup"><span data-stu-id="c10a3-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="c10a3-103">Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="c10a3-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="c10a3-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c10a3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c10a3-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c10a3-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c10a3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span><span class="sxs-lookup"><span data-stu-id="c10a3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c10a3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c10a3-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c10a3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c10a3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c10a3-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c10a3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c10a3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c10a3-110">Attributes</span></span>  
  
|<span data-ttu-id="c10a3-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c10a3-111">Attribute</span></span>|<span data-ttu-id="c10a3-112">Description</span><span class="sxs-lookup"><span data-stu-id="c10a3-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c10a3-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c10a3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c10a3-114">Précise si les tableaux de plus de 2 Go de taille totale sont activés sur des plates-formes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c10a3-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c10a3-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="c10a3-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c10a3-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="c10a3-116">Value</span></span>|<span data-ttu-id="c10a3-117">Description</span><span class="sxs-lookup"><span data-stu-id="c10a3-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c10a3-118">Les tableaux de plus de 2 Go en taille totale ne sont pas activés.</span><span class="sxs-lookup"><span data-stu-id="c10a3-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="c10a3-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c10a3-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c10a3-120">Les tableaux de plus de 2 Go de taille totale sont activés sur des plates-formes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c10a3-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c10a3-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c10a3-121">Child Elements</span></span>  
 <span data-ttu-id="c10a3-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c10a3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c10a3-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c10a3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c10a3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="c10a3-124">Element</span></span>|<span data-ttu-id="c10a3-125">Description</span><span class="sxs-lookup"><span data-stu-id="c10a3-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c10a3-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c10a3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c10a3-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="c10a3-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c10a3-128">Notes </span><span class="sxs-lookup"><span data-stu-id="c10a3-128">Remarks</span></span>  
 <span data-ttu-id="c10a3-129">L’utilisation de cet élément dans votre fichier de configuration d’application permet des tableaux de plus de 2 Go de taille, mais ne modifie pas d’autres limites sur la taille de l’objet ou la taille du tableau :</span><span class="sxs-lookup"><span data-stu-id="c10a3-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="c10a3-130">Le nombre maximum d’éléments <xref:System.UInt32.MaxValue?displayProperty=nameWithType>dans un tableau est .</span><span class="sxs-lookup"><span data-stu-id="c10a3-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c10a3-131">L’indice maximal dans une seule dimension est de 2 147 483 591 (0x7FFFFFC7) pour les tableaux d’ethètes et les tableaux de structures uninaires, et de 2 146 435 071 (0X7FEFFFFFFF) pour d’autres types.</span><span class="sxs-lookup"><span data-stu-id="c10a3-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="c10a3-132">La taille maximale pour les cordes et autres objets non-array est inchangée.</span><span class="sxs-lookup"><span data-stu-id="c10a3-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c10a3-133">Avant d’activer cette fonctionnalité, assurez-vous que votre application n’inclut pas de code dangereux qui suppose que tous les tableaux sont de moins de 2 Go de taille.</span><span class="sxs-lookup"><span data-stu-id="c10a3-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="c10a3-134">Par exemple, le code dangereux qui utilise des tableaux comme tampons peut être susceptible de dépassements de tampon s’il est écrit en supposant que les tableaux ne dépasseront pas 2 Go.</span><span class="sxs-lookup"><span data-stu-id="c10a3-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c10a3-135"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c10a3-135">Example</span></span>  
 <span data-ttu-id="c10a3-136">L’exemple suivant montre comment activer cette fonctionnalité pour une application.</span><span class="sxs-lookup"><span data-stu-id="c10a3-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="c10a3-137">Pris en charge dans</span><span class="sxs-lookup"><span data-stu-id="c10a3-137">Supported in</span></span>

<span data-ttu-id="c10a3-138">.NET Framework 4.5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="c10a3-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="c10a3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c10a3-139">See also</span></span>

- [<span data-ttu-id="c10a3-140">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="c10a3-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c10a3-141">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="c10a3-141">Configuration File Schema</span></span>](../index.md)
