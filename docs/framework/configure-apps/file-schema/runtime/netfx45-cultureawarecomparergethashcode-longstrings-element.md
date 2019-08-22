---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd59d1bcc489f248cbeb397afffb638071df17b6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663585"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="222a7-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >, élément</span><span class="sxs-lookup"><span data-stu-id="222a7-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="222a7-103">Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="222a7-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="222a7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="222a7-104">\<configuration></span></span>\
<span data-ttu-id="222a7-105">\<> du runtime </span><span class="sxs-lookup"><span data-stu-id="222a7-105">\<runtime></span></span>\
<span data-ttu-id="222a7-106">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="222a7-106">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>

## <a name="syntax"></a><span data-ttu-id="222a7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="222a7-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="222a7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="222a7-108">Attributes and Elements</span></span>

<span data-ttu-id="222a7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="222a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="222a7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="222a7-110">Attributes</span></span>

|<span data-ttu-id="222a7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="222a7-111">Attribute</span></span>|<span data-ttu-id="222a7-112">Description</span><span class="sxs-lookup"><span data-stu-id="222a7-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="222a7-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="222a7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="222a7-114">Spécifie si le CLR (Common Langage Runtime) alloue une quantité de mémoire fixe lors du calcul des codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="222a7-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="222a7-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="222a7-115">enabled Attribute</span></span>

|<span data-ttu-id="222a7-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="222a7-116">Value</span></span>|<span data-ttu-id="222a7-117">Description</span><span class="sxs-lookup"><span data-stu-id="222a7-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="222a7-118">0</span><span class="sxs-lookup"><span data-stu-id="222a7-118">0</span></span>|<span data-ttu-id="222a7-119">Le Common Langage Runtime alloue une quantité de mémoire variable à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pour calculer les codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="222a7-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="222a7-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="222a7-120">This is the default.</span></span>|
|<span data-ttu-id="222a7-121">1</span><span class="sxs-lookup"><span data-stu-id="222a7-121">1</span></span>|<span data-ttu-id="222a7-122">Le Common Langage Runtime alloue une quantité de mémoire fixe à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pour calculer les codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="222a7-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="222a7-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="222a7-123">Child Elements</span></span>

<span data-ttu-id="222a7-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="222a7-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="222a7-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="222a7-125">Parent Elements</span></span>

|<span data-ttu-id="222a7-126">Élément</span><span class="sxs-lookup"><span data-stu-id="222a7-126">Element</span></span>|<span data-ttu-id="222a7-127">Description</span><span class="sxs-lookup"><span data-stu-id="222a7-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="222a7-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="222a7-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="222a7-129">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="222a7-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="222a7-130">Notes</span><span class="sxs-lookup"><span data-stu-id="222a7-130">Remarks</span></span>

<span data-ttu-id="222a7-131">Par défaut, le CLR alloue une quantité de mémoire variable à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> , et une exception <xref:System.ArgumentException> peut être levée lorsque la méthode tente de calculer le code de hachage de chaînes très longues (de plusieurs millions de caractères).</span><span class="sxs-lookup"><span data-stu-id="222a7-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="222a7-132">Ajouter cet élément dans un fichier de configuration de l'application et affecter la valeur « 1 » à son attribut `enabled` vous permet de spécifier que la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> utilise un autre algorithme qui alloue une quantité de mémoire fixe au calcul du code de hachage.</span><span class="sxs-lookup"><span data-stu-id="222a7-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="222a7-133">L'élément `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` n'est pas utilisé dans [!INCLUDE[win8](../../../../../includes/win8-md.md)] et ses versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="222a7-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="222a7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="222a7-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="222a7-135">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="222a7-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="222a7-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="222a7-136">Configuration File Schema</span></span>](../index.md)
