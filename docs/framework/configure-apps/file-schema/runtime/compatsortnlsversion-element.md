---
title: Élément <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 575d44ad9ecf445ba5d4b7fbe47032127ccb33ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252734"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="d72d5-102">\<CompatSortNLSVersion >, élément</span><span class="sxs-lookup"><span data-stu-id="d72d5-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="d72d5-103">Spécifie que le runtime doit utiliser des ordres de tri hérités lors de l'exécution de comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="d72d5-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
<span data-ttu-id="d72d5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d72d5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d72d5-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d72d5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d72d5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion>**</span><span class="sxs-lookup"><span data-stu-id="d72d5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d72d5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d72d5-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d72d5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d72d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d72d5-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d72d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d72d5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d72d5-110">Attributes</span></span>  
  
|<span data-ttu-id="d72d5-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d72d5-111">Attribute</span></span>|<span data-ttu-id="d72d5-112">Description</span><span class="sxs-lookup"><span data-stu-id="d72d5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d72d5-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="d72d5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d72d5-114">Spécifie l'ID de paramètres régionaux dont l'ordre de tri doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="d72d5-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d72d5-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="d72d5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d72d5-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="d72d5-116">Value</span></span>|<span data-ttu-id="d72d5-117">Description</span><span class="sxs-lookup"><span data-stu-id="d72d5-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d72d5-118">4096</span><span class="sxs-lookup"><span data-stu-id="d72d5-118">4096</span></span>|<span data-ttu-id="d72d5-119">ID de paramètres régionaux qui représente un ordre de tri secondaire.</span><span class="sxs-lookup"><span data-stu-id="d72d5-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="d72d5-120">Dans ce cas, 4096 représente l’ordre de tri des .NET Framework 3,5 et des versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="d72d5-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d72d5-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d72d5-121">Child Elements</span></span>  
 <span data-ttu-id="d72d5-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d72d5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d72d5-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d72d5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d72d5-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d72d5-124">Element</span></span>|<span data-ttu-id="d72d5-125">Description</span><span class="sxs-lookup"><span data-stu-id="d72d5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d72d5-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d72d5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d72d5-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="d72d5-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d72d5-128">Notes</span><span class="sxs-lookup"><span data-stu-id="d72d5-128">Remarks</span></span>  
 <span data-ttu-id="d72d5-129">Étant donné que les opérations de comparaison de chaînes, de tri <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> et de respect de la casse effectuées par la classe dans le .NET Framework 4 sont conformes à la norme Unicode <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> 5,1 <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> , les résultats des méthodes de comparaison de chaînes telles que et peuvent différer de versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d72d5-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="d72d5-130">Si votre application dépend d’un comportement hérité, vous pouvez restaurer la comparaison de chaînes et les règles de tri utilisées dans le .NET Framework 3,5 et les `<CompatSortNLSVersion>` versions antérieures en incluant l’élément dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="d72d5-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d72d5-131">La restauration de la comparaison de chaînes héritées et des règles de tri requiert également que la bibliothèque de liens dynamiques sort00001000.dll soit disponible sur le système local.</span><span class="sxs-lookup"><span data-stu-id="d72d5-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="d72d5-132">Vous pouvez également utiliser des règles de tri et de comparaison de chaîne héritées dans un domaine d'application spécifique en passant la chaîne « NetFx40_Legacy20SortingBehavior » à la méthode <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> lorsque vous créez le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d72d5-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d72d5-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="d72d5-133">Example</span></span>  
 <span data-ttu-id="d72d5-134">L'exemple suivant instancie deux objets <xref:System.String> et appelle la méthode <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> pour les comparer en utilisant les conventions de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="d72d5-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="d72d5-135">Lorsque vous exécutez l’exemple sur le .NET Framework 4, il affiche la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="d72d5-135">When you run the example on the .NET Framework 4, it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="d72d5-136">Cela est complètement différent de la sortie qui s’affiche lorsque vous exécutez l’exemple sur la .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="d72d5-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5.</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="d72d5-137">Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple, puis exécutez l’exemple sur le .NET Framework 4, la sortie est identique à celle produite par l’exemple lorsqu’elle est exécutée sur le .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="d72d5-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d72d5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d72d5-138">See also</span></span>

- [<span data-ttu-id="d72d5-139">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="d72d5-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d72d5-140">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d72d5-140">Configuration File Schema</span></span>](../index.md)
