---
title: Élément <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: b6230833808ec45d702502e36f929db4e03173e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116793"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="8aa10-102">\<élément gcAllowVeryLargeObjects ></span><span class="sxs-lookup"><span data-stu-id="8aa10-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="8aa10-103">Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="8aa10-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="8aa10-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8aa10-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8aa10-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="8aa10-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8aa10-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcAllowVeryLargeObjects** ></span><span class="sxs-lookup"><span data-stu-id="8aa10-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa10-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa10-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aa10-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8aa10-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8aa10-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8aa10-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aa10-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8aa10-110">Attributes</span></span>  
  
|<span data-ttu-id="8aa10-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="8aa10-111">Attribute</span></span>|<span data-ttu-id="8aa10-112">Description</span><span class="sxs-lookup"><span data-stu-id="8aa10-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8aa10-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="8aa10-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8aa10-114">Spécifie si les tableaux dont la taille totale est supérieure à 2 Go sont activés sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8aa10-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8aa10-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="8aa10-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8aa10-116">valeur</span><span class="sxs-lookup"><span data-stu-id="8aa10-116">Value</span></span>|<span data-ttu-id="8aa10-117">Description</span><span class="sxs-lookup"><span data-stu-id="8aa10-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8aa10-118">Les tableaux d’une taille totale supérieure à 2 Go ne sont pas activés.</span><span class="sxs-lookup"><span data-stu-id="8aa10-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="8aa10-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8aa10-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8aa10-120">Les tableaux d’une taille totale supérieure à 2 Go sont activés sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8aa10-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aa10-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8aa10-121">Child Elements</span></span>  
 <span data-ttu-id="8aa10-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="8aa10-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aa10-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8aa10-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8aa10-124">Élément</span><span class="sxs-lookup"><span data-stu-id="8aa10-124">Element</span></span>|<span data-ttu-id="8aa10-125">Description</span><span class="sxs-lookup"><span data-stu-id="8aa10-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8aa10-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8aa10-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8aa10-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="8aa10-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aa10-128">Notes</span><span class="sxs-lookup"><span data-stu-id="8aa10-128">Remarks</span></span>  
 <span data-ttu-id="8aa10-129">L’utilisation de cet élément dans le fichier de configuration de votre application permet aux tableaux dont la taille est supérieure à 2 Go, mais ne modifie pas les autres limites de taille d’objet ou de taille de tableau :</span><span class="sxs-lookup"><span data-stu-id="8aa10-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="8aa10-130">Le nombre maximal d’éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8aa10-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="8aa10-131">L’index maximal dans une dimension unique est 2 147 483 591 (0x7FFFFFC7) pour les tableaux d’octets et les tableaux de structures sur un octet, et 2 146 435 071 (0X7FEFFFFF) pour d’autres types.</span><span class="sxs-lookup"><span data-stu-id="8aa10-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="8aa10-132">La taille maximale des chaînes et d’autres objets non-tableau est inchangée.</span><span class="sxs-lookup"><span data-stu-id="8aa10-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="8aa10-133">Avant d’activer cette fonctionnalité, assurez-vous que votre application n’inclut pas de code non sécurisé qui suppose que la taille de tous les tableaux est inférieure à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="8aa10-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="8aa10-134">Par exemple, le code unsafe qui utilise des tableaux comme mémoires tampons peut être vulnérable aux dépassements de mémoire tampon s’il est écrit en supposant que les tableaux ne dépasseront pas 2 Go.</span><span class="sxs-lookup"><span data-stu-id="8aa10-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aa10-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="8aa10-135">Example</span></span>  
 <span data-ttu-id="8aa10-136">L’exemple suivant montre comment activer cette fonctionnalité pour une application.</span><span class="sxs-lookup"><span data-stu-id="8aa10-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="8aa10-137">Pris en charge dans</span><span class="sxs-lookup"><span data-stu-id="8aa10-137">Supported in</span></span>

<span data-ttu-id="8aa10-138">.NET Framework 4,5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8aa10-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="8aa10-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aa10-139">See also</span></span>

- [<span data-ttu-id="8aa10-140">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="8aa10-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8aa10-141">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8aa10-141">Configuration File Schema</span></span>](../index.md)
