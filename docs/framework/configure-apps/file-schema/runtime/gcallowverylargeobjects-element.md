---
title: gcAllowVeryLargeObjects (élément)
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058127"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="f8f89-102">\<gcAllowVeryLargeObjects>, élément</span><span class="sxs-lookup"><span data-stu-id="f8f89-102">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="f8f89-103">Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="f8f89-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="f8f89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8f89-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="f8f89-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="f8f89-105">Attributes</span></span>
  
|<span data-ttu-id="f8f89-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="f8f89-106">Attribute</span></span>|<span data-ttu-id="f8f89-107">Description</span><span class="sxs-lookup"><span data-stu-id="f8f89-107">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f8f89-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f8f89-108">Required attribute.</span></span><br /><br /> <span data-ttu-id="f8f89-109">Spécifie si les tableaux dont la taille totale est supérieure à 2 Go sont activés sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f8f89-109">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="f8f89-110">attribut activé</span><span class="sxs-lookup"><span data-stu-id="f8f89-110">enabled attribute</span></span>  
  
|<span data-ttu-id="f8f89-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="f8f89-111">Value</span></span>|<span data-ttu-id="f8f89-112">Description</span><span class="sxs-lookup"><span data-stu-id="f8f89-112">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f8f89-113">Les tableaux d’une taille totale supérieure à 2 Go ne sont pas activés.</span><span class="sxs-lookup"><span data-stu-id="f8f89-113">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="f8f89-114">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f8f89-114">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f8f89-115">Les tableaux d’une taille totale supérieure à 2 Go sont activés sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f8f89-115">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="f8f89-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f8f89-116">Child elements</span></span>  

<span data-ttu-id="f8f89-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f8f89-117">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="f8f89-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f8f89-118">Parent elements</span></span>
  
|<span data-ttu-id="f8f89-119">Élément</span><span class="sxs-lookup"><span data-stu-id="f8f89-119">Element</span></span>|<span data-ttu-id="f8f89-120">Description</span><span class="sxs-lookup"><span data-stu-id="f8f89-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8f89-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8f89-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f8f89-122">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="f8f89-122">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8f89-123">Notes</span><span class="sxs-lookup"><span data-stu-id="f8f89-123">Remarks</span></span>  

 <span data-ttu-id="f8f89-124">L’utilisation de cet élément dans le fichier de configuration de votre application permet aux tableaux dont la taille est supérieure à 2 Go, mais ne modifie pas les autres limites de taille d’objet ou de taille de tableau :</span><span class="sxs-lookup"><span data-stu-id="f8f89-124">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="f8f89-125">Le nombre maximal d’éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f8f89-125">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f8f89-126">La taille maximale d’une dimension unique est 2 147 483 591 (0x7FFFFFC7) pour les tableaux d’octets et les tableaux de structures sur un octet, et 2 146 435 071 (0X7FEFFFFF) pour les tableaux qui contiennent d’autres types.</span><span class="sxs-lookup"><span data-stu-id="f8f89-126">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="f8f89-127">La taille maximale des chaînes et d’autres objets non-tableau est inchangée.</span><span class="sxs-lookup"><span data-stu-id="f8f89-127">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f8f89-128">Avant d’activer cette fonctionnalité, assurez-vous que votre application n’inclut pas de code non sécurisé qui suppose que la taille de tous les tableaux est inférieure à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="f8f89-128">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="f8f89-129">Par exemple, le code unsafe qui utilise des tableaux comme mémoires tampons peut être vulnérable aux dépassements de mémoire tampon s’il est écrit en supposant que les tableaux ne dépasseront pas 2 Go.</span><span class="sxs-lookup"><span data-stu-id="f8f89-129">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8f89-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8f89-130">Example</span></span>  

 <span data-ttu-id="f8f89-131">L’exemple suivant montre comment activer cette fonctionnalité pour une application.</span><span class="sxs-lookup"><span data-stu-id="f8f89-131">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="f8f89-132">Pris en charge dans</span><span class="sxs-lookup"><span data-stu-id="f8f89-132">Supported in</span></span>

<span data-ttu-id="f8f89-133">.NET Framework 4,5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f8f89-133">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="f8f89-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8f89-134">See also</span></span>

- [<span data-ttu-id="f8f89-135">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="f8f89-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f8f89-136">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f8f89-136">Configuration File Schema</span></span>](../index.md)
