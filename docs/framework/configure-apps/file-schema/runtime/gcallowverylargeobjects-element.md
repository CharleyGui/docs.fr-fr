---
title: Élément <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154125"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="28ff5-102">Élément \<gcAllowVeryLargeObjects></span><span class="sxs-lookup"><span data-stu-id="28ff5-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="28ff5-103">Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="28ff5-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="28ff5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28ff5-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28ff5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="28ff5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="28ff5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="28ff5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28ff5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="28ff5-107">Attributes</span></span>  
  
|<span data-ttu-id="28ff5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="28ff5-108">Attribute</span></span>|<span data-ttu-id="28ff5-109">Description</span><span class="sxs-lookup"><span data-stu-id="28ff5-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="28ff5-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="28ff5-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="28ff5-111">Spécifie si les tableaux dont la taille totale est supérieure à 2 Go sont activés sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="28ff5-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="28ff5-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="28ff5-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="28ff5-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="28ff5-113">Value</span></span>|<span data-ttu-id="28ff5-114">Description</span><span class="sxs-lookup"><span data-stu-id="28ff5-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="28ff5-115">Les tableaux d’une taille totale supérieure à 2 Go ne sont pas activés.</span><span class="sxs-lookup"><span data-stu-id="28ff5-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="28ff5-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="28ff5-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="28ff5-117">Les tableaux d’une taille totale supérieure à 2 Go sont activés sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="28ff5-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28ff5-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="28ff5-118">Child Elements</span></span>  
 <span data-ttu-id="28ff5-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="28ff5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28ff5-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="28ff5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="28ff5-121">Élément</span><span class="sxs-lookup"><span data-stu-id="28ff5-121">Element</span></span>|<span data-ttu-id="28ff5-122">Description</span><span class="sxs-lookup"><span data-stu-id="28ff5-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28ff5-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28ff5-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28ff5-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="28ff5-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28ff5-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="28ff5-125">Remarks</span></span>  
 <span data-ttu-id="28ff5-126">L’utilisation de cet élément dans le fichier de configuration de votre application permet aux tableaux dont la taille est supérieure à 2 Go, mais ne modifie pas les autres limites de taille d’objet ou de taille de tableau :</span><span class="sxs-lookup"><span data-stu-id="28ff5-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="28ff5-127">Le nombre maximal d’éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="28ff5-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="28ff5-128">L’index maximal dans une dimension unique est 2 147 483 591 (0x7FFFFFC7) pour les tableaux d’octets et les tableaux de structures sur un octet, et 2 146 435 071 (0X7FEFFFFF) pour d’autres types.</span><span class="sxs-lookup"><span data-stu-id="28ff5-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="28ff5-129">La taille maximale des chaînes et d’autres objets non-tableau est inchangée.</span><span class="sxs-lookup"><span data-stu-id="28ff5-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="28ff5-130">Avant d’activer cette fonctionnalité, assurez-vous que votre application n’inclut pas de code non sécurisé qui suppose que la taille de tous les tableaux est inférieure à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="28ff5-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="28ff5-131">Par exemple, le code unsafe qui utilise des tableaux comme mémoires tampons peut être vulnérable aux dépassements de mémoire tampon s’il est écrit en supposant que les tableaux ne dépasseront pas 2 Go.</span><span class="sxs-lookup"><span data-stu-id="28ff5-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28ff5-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="28ff5-132">Example</span></span>  
 <span data-ttu-id="28ff5-133">L’exemple suivant montre comment activer cette fonctionnalité pour une application.</span><span class="sxs-lookup"><span data-stu-id="28ff5-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="28ff5-134">Pris en charge dans</span><span class="sxs-lookup"><span data-stu-id="28ff5-134">Supported in</span></span>

<span data-ttu-id="28ff5-135">.NET Framework 4,5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="28ff5-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="28ff5-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28ff5-136">See also</span></span>

- [<span data-ttu-id="28ff5-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="28ff5-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="28ff5-138">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="28ff5-138">Configuration File Schema</span></span>](../index.md)
