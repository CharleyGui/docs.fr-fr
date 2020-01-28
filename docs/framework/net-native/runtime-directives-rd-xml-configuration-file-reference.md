---
title: Guide de référence du fichier de configuration des directives runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738409"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="a2016-102">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a2016-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="a2016-103">Un fichier de directives runtime (.rd.xml) est un fichier de configuration XML qui spécifie si les éléments de programme désignés sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="a2016-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="a2016-104">Voici un exemple de fichier de directives runtime :</span><span class="sxs-lookup"><span data-stu-id="a2016-104">Here’s an example of a runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
    <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
    <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
    <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

    <Namespace Name="System.Collections.ObjectModel" >
      <TypeInstantiation Name="ObservableCollection"
            Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
      <TypeInstantiation Name="ReadOnlyObservableCollection"
            Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
    </Namespace>
  </Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="a2016-105">Structure d'un fichier de directives runtime</span><span class="sxs-lookup"><span data-stu-id="a2016-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="a2016-106">Le fichier de directives runtime utilise l'espace de noms `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span><span class="sxs-lookup"><span data-stu-id="a2016-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="a2016-107">L’élément racine est l’élément [Directives](directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a2016-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="a2016-108">Il peut contenir zéro ou plusieurs éléments [Library](library-element-net-native.md) et zéro ou un élément [Application](application-element-net-native.md), comme indiqué dans la structure suivante.</span><span class="sxs-lookup"><span data-stu-id="a2016-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="a2016-109">Les attributs de l’élément [Application](application-element-net-native.md) peuvent définir une stratégie de réflexion runtime à l’échelle de l’application, ou peuvent servir de conteneur pour les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="a2016-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="a2016-110">L’élément [Library](library-element-net-native.md), quant à lui, sert simplement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="a2016-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="a2016-111">Les enfants des éléments[Application](application-element-net-native.md) et [Library](library-element-net-native.md) définissent les types, méthodes, champs, propriétés et événements qui sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="a2016-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="a2016-112">Pour obtenir des informations de référence, choisissez les éléments dans la structure suivante ou consultez [Éléments de directive runtime](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="a2016-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="a2016-113">Dans la hiérarchie suivante, les points de suspension marquent une structure récursive.</span><span class="sxs-lookup"><span data-stu-id="a2016-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="a2016-114">Les informations entre crochets indiquent si l'élément concerné est facultatif ou obligatoire, et, s'il est utilisé, le nombre d'instances autorisées (une ou plusieurs).</span><span class="sxs-lookup"><span data-stu-id="a2016-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="a2016-115">[Directives](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="a2016-115">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="a2016-116">[Application](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="a2016-116">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="a2016-117">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-117">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-118">[Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-118">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-119">.</span><span class="sxs-lookup"><span data-stu-id="a2016-119">.</span></span> <span data-ttu-id="a2016-120">.</span><span class="sxs-lookup"><span data-stu-id="a2016-120">.</span></span>
      - <span data-ttu-id="a2016-121">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-121">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-122">.</span><span class="sxs-lookup"><span data-stu-id="a2016-122">.</span></span> <span data-ttu-id="a2016-123">.</span><span class="sxs-lookup"><span data-stu-id="a2016-123">.</span></span>
      - <span data-ttu-id="a2016-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-125">.</span><span class="sxs-lookup"><span data-stu-id="a2016-125">.</span></span> <span data-ttu-id="a2016-126">.</span><span class="sxs-lookup"><span data-stu-id="a2016-126">.</span></span>
    - <span data-ttu-id="a2016-127">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-127">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-128">[Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-128">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-129">.</span><span class="sxs-lookup"><span data-stu-id="a2016-129">.</span></span> <span data-ttu-id="a2016-130">.</span><span class="sxs-lookup"><span data-stu-id="a2016-130">.</span></span>
      - <span data-ttu-id="a2016-131">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-131">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-132">.</span><span class="sxs-lookup"><span data-stu-id="a2016-132">.</span></span> <span data-ttu-id="a2016-133">.</span><span class="sxs-lookup"><span data-stu-id="a2016-133">.</span></span>
      - <span data-ttu-id="a2016-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-135">.</span><span class="sxs-lookup"><span data-stu-id="a2016-135">.</span></span> <span data-ttu-id="a2016-136">.</span><span class="sxs-lookup"><span data-stu-id="a2016-136">.</span></span>
    - <span data-ttu-id="a2016-137">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-137">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-138">[Subtypes](subtypes-element-net-native.md) (sous-classes du type conteneur) [O:1]</span><span class="sxs-lookup"><span data-stu-id="a2016-138">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="a2016-139">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-139">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-140">.</span><span class="sxs-lookup"><span data-stu-id="a2016-140">.</span></span> <span data-ttu-id="a2016-141">.</span><span class="sxs-lookup"><span data-stu-id="a2016-141">.</span></span>
      - <span data-ttu-id="a2016-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-143">.</span><span class="sxs-lookup"><span data-stu-id="a2016-143">.</span></span> <span data-ttu-id="a2016-144">.</span><span class="sxs-lookup"><span data-stu-id="a2016-144">.</span></span>
      - <span data-ttu-id="a2016-145">[AttributeImplies](attributeimplies-element-net-native.md) (le type conteneur est un attribut) [O:1]</span><span class="sxs-lookup"><span data-stu-id="a2016-145">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="a2016-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-147">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-147">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="a2016-148">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-148">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="a2016-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="a2016-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="a2016-152">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-152">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-153">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-153">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-154">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-154">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="a2016-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="a2016-156">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-156">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-157">.</span><span class="sxs-lookup"><span data-stu-id="a2016-157">.</span></span> <span data-ttu-id="a2016-158">.</span><span class="sxs-lookup"><span data-stu-id="a2016-158">.</span></span>
      - <span data-ttu-id="a2016-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-160">.</span><span class="sxs-lookup"><span data-stu-id="a2016-160">.</span></span> <span data-ttu-id="a2016-161">.</span><span class="sxs-lookup"><span data-stu-id="a2016-161">.</span></span>
      - <span data-ttu-id="a2016-162">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-162">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="a2016-163">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-163">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="a2016-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="a2016-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="a2016-167">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-167">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-168">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-168">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-169">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-169">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="a2016-170">[Library](library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-170">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="a2016-171">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-171">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-172">[Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-172">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-173">.</span><span class="sxs-lookup"><span data-stu-id="a2016-173">.</span></span> <span data-ttu-id="a2016-174">.</span><span class="sxs-lookup"><span data-stu-id="a2016-174">.</span></span>
      - <span data-ttu-id="a2016-175">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-175">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-176">.</span><span class="sxs-lookup"><span data-stu-id="a2016-176">.</span></span> <span data-ttu-id="a2016-177">.</span><span class="sxs-lookup"><span data-stu-id="a2016-177">.</span></span>
      - <span data-ttu-id="a2016-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-179">.</span><span class="sxs-lookup"><span data-stu-id="a2016-179">.</span></span> <span data-ttu-id="a2016-180">.</span><span class="sxs-lookup"><span data-stu-id="a2016-180">.</span></span>
    - <span data-ttu-id="a2016-181">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-181">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-182">[Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-182">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-183">.</span><span class="sxs-lookup"><span data-stu-id="a2016-183">.</span></span> <span data-ttu-id="a2016-184">.</span><span class="sxs-lookup"><span data-stu-id="a2016-184">.</span></span>
      - <span data-ttu-id="a2016-185">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-185">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-186">.</span><span class="sxs-lookup"><span data-stu-id="a2016-186">.</span></span> <span data-ttu-id="a2016-187">.</span><span class="sxs-lookup"><span data-stu-id="a2016-187">.</span></span>
      - <span data-ttu-id="a2016-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-189">.</span><span class="sxs-lookup"><span data-stu-id="a2016-189">.</span></span> <span data-ttu-id="a2016-190">.</span><span class="sxs-lookup"><span data-stu-id="a2016-190">.</span></span>
    - <span data-ttu-id="a2016-191">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-191">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-192">[Subtypes](subtypes-element-net-native.md) (sous-classes du type conteneur) [O:1]</span><span class="sxs-lookup"><span data-stu-id="a2016-192">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="a2016-193">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-193">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-194">.</span><span class="sxs-lookup"><span data-stu-id="a2016-194">.</span></span> <span data-ttu-id="a2016-195">.</span><span class="sxs-lookup"><span data-stu-id="a2016-195">.</span></span>
      - <span data-ttu-id="a2016-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-197">.</span><span class="sxs-lookup"><span data-stu-id="a2016-197">.</span></span> <span data-ttu-id="a2016-198">.</span><span class="sxs-lookup"><span data-stu-id="a2016-198">.</span></span>
      - <span data-ttu-id="a2016-199">[AttributeImplies](attributeimplies-element-net-native.md) (le type conteneur est un attribut) [O:1]</span><span class="sxs-lookup"><span data-stu-id="a2016-199">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="a2016-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-201">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-201">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="a2016-203">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-203">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-204">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-204">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-205">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-205">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="a2016-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="a2016-207">[Tapez](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-207">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="a2016-208">.</span><span class="sxs-lookup"><span data-stu-id="a2016-208">.</span></span> <span data-ttu-id="a2016-209">.</span><span class="sxs-lookup"><span data-stu-id="a2016-209">.</span></span>
      - <span data-ttu-id="a2016-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="a2016-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="a2016-211">.</span><span class="sxs-lookup"><span data-stu-id="a2016-211">.</span></span> <span data-ttu-id="a2016-212">.</span><span class="sxs-lookup"><span data-stu-id="a2016-212">.</span></span>
      - <span data-ttu-id="a2016-213">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-213">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="a2016-215">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-215">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-216">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-216">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="a2016-217">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="a2016-217">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="a2016-218">L’élément [Application](application-element-net-native.md) peut n’avoir aucun attribut, ou peut avoir les attributs de stratégie présentés dans la section [Stratégie et directives runtime](#Directives).</span><span class="sxs-lookup"><span data-stu-id="a2016-218">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="a2016-219">Un élément [Library](library-element-net-native.md) possède un attribut unique (`Name`) qui spécifie le nom d’une bibliothèque ou d’un assembly, sans son extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="a2016-219">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="a2016-220">Par exemple, l’élément [Library](library-element-net-native.md) suivant s’applique à un assembly nommé Extensions.dll.</span><span class="sxs-lookup"><span data-stu-id="a2016-220">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="a2016-221">Stratégie et directives runtime</span><span class="sxs-lookup"><span data-stu-id="a2016-221">Runtime directives and policy</span></span>

<span data-ttu-id="a2016-222">L’élément [Application](application-element-net-native.md) lui-même et les éléments enfants des éléments [Library](library-element-net-native.md) et [Application](application-element-net-native.md) expriment la stratégie ; autrement dit, ils définissent la façon dont une application peut appliquer la réflexion à un élément de programme.</span><span class="sxs-lookup"><span data-stu-id="a2016-222">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="a2016-223">Le type de stratégie est défini par un attribut de l'élément (par exemple, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="a2016-223">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="a2016-224">La valeur de stratégie est définie par la valeur de l'attribut (par exemple, `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="a2016-224">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="a2016-225">Toute stratégie spécifiée par un attribut d'un élément s'applique à tous les éléments enfants qui ne définissent pas de valeur pour cette stratégie.</span><span class="sxs-lookup"><span data-stu-id="a2016-225">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="a2016-226">Par exemple, si une stratégie est spécifiée par un élément [Type](type-element-net-native.md), elle s’applique à tous les types et membres contenus pour lesquels une stratégie n’est pas explicitement définie.</span><span class="sxs-lookup"><span data-stu-id="a2016-226">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="a2016-227">La stratégie qui peut être exprimée par les éléments [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) et [Type](type-element-net-native.md) diffère de la stratégie qui peut être exprimée pour des membres spécifiques (par les éléments [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), et [Event](event-element-net-native.md)).</span><span class="sxs-lookup"><span data-stu-id="a2016-227">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="a2016-228">Spécification d'une stratégie pour des assemblys, des espaces de noms et des types</span><span class="sxs-lookup"><span data-stu-id="a2016-228">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="a2016-229">Les éléments [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) et [Type](type-element-net-native.md) prennent en charge les types de stratégie suivants :</span><span class="sxs-lookup"><span data-stu-id="a2016-229">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="a2016-230">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="a2016-230">`Activate`.</span></span> <span data-ttu-id="a2016-231">Contrôle l'accès aux constructeurs, pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a2016-231">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="a2016-232">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-232">`Browse`.</span></span> <span data-ttu-id="a2016-233">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a2016-233">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="a2016-234">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-234">`Dynamic`.</span></span> <span data-ttu-id="a2016-235">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="a2016-235">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="a2016-236">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-236">`Serialize`.</span></span> <span data-ttu-id="a2016-237">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation des instances de types par des bibliothèques tierces comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="a2016-237">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="a2016-238">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="a2016-238">`DataContractSerializer`.</span></span> <span data-ttu-id="a2016-239">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2016-239">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="a2016-240">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="a2016-240">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="a2016-241">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2016-241">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="a2016-242">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="a2016-242">`XmlSerializer`.</span></span> <span data-ttu-id="a2016-243">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2016-243">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="a2016-244">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="a2016-244">`MarshalObject`.</span></span> <span data-ttu-id="a2016-245">Contrôle la stratégie de marshaling des types référence vers WinRT et COM.</span><span class="sxs-lookup"><span data-stu-id="a2016-245">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="a2016-246">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="a2016-246">`MarshalDelegate`.</span></span> <span data-ttu-id="a2016-247">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="a2016-247">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="a2016-248">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="a2016-248">`MarshalStructure` .</span></span> <span data-ttu-id="a2016-249">Stratégie de contrôles pour le marshaling de structures en code natif.</span><span class="sxs-lookup"><span data-stu-id="a2016-249">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="a2016-250">Les paramètres associés à ces types de stratégie sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a2016-250">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="a2016-251">`All`.</span><span class="sxs-lookup"><span data-stu-id="a2016-251">`All`.</span></span> <span data-ttu-id="a2016-252">Activer la stratégie pour tous les types et membres que la chaîne d'outils ne supprime pas.</span><span class="sxs-lookup"><span data-stu-id="a2016-252">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="a2016-253">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="a2016-253">`Auto`.</span></span> <span data-ttu-id="a2016-254">Utiliser le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2016-254">Use the default behavior.</span></span> <span data-ttu-id="a2016-255">(Ne pas spécifier une stratégie équivaut à définir cette stratégie sur `Auto` , sauf si elle est substituée, par exemple par un élément parent.)</span><span class="sxs-lookup"><span data-stu-id="a2016-255">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="a2016-256">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="a2016-256">`Excluded`.</span></span> <span data-ttu-id="a2016-257">Désactiver la stratégie pour l'élément de programme.</span><span class="sxs-lookup"><span data-stu-id="a2016-257">Disable the policy for the program element.</span></span>

- <span data-ttu-id="a2016-258">`Public`.</span><span class="sxs-lookup"><span data-stu-id="a2016-258">`Public`.</span></span> <span data-ttu-id="a2016-259">Activer la stratégie pour les types ou membres publics, sauf si la chaîne d'outils détermine que le membre n'est pas nécessaire et donc le supprime.</span><span class="sxs-lookup"><span data-stu-id="a2016-259">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="a2016-260">(Dans ce dernier cas, vous devez utiliser `Required Public` pour vous assurer que le membre est conservé et dispose de fonctionnalités de réflexion.)</span><span class="sxs-lookup"><span data-stu-id="a2016-260">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="a2016-261">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="a2016-261">`PublicAndInternal`.</span></span> <span data-ttu-id="a2016-262">Activer la stratégie pour les types ou membres publics et internes si la chaîne d'outils ne les supprime pas.</span><span class="sxs-lookup"><span data-stu-id="a2016-262">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="a2016-263">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="a2016-263">`Required Public`.</span></span> <span data-ttu-id="a2016-264">Obliger la chaîne d'outils à conserver les membres et types publics, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.</span><span class="sxs-lookup"><span data-stu-id="a2016-264">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="a2016-265">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="a2016-265">`Required PublicAndInternal`.</span></span> <span data-ttu-id="a2016-266">Obliger la chaîne d'outils à conserver les types et membres publics et internes, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.</span><span class="sxs-lookup"><span data-stu-id="a2016-266">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="a2016-267">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="a2016-267">`Required All`.</span></span> <span data-ttu-id="a2016-268">Obliger la chaîne d'outils à conserver tous les membres et types, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.</span><span class="sxs-lookup"><span data-stu-id="a2016-268">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="a2016-269">Par exemple, le fichier de directives runtime suivant définit la stratégie pour tous les types et membres de l'assembly DataClasses.dll.</span><span class="sxs-lookup"><span data-stu-id="a2016-269">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="a2016-270">Il autorise la réflexion pour la sérialisation de toutes les propriétés publiques, la consultation de tous les types et membres de type, l'activation pour tous les types (en raison de l'attribut `Dynamic`) et la réflexion pour tous les membres et types publics.</span><span class="sxs-lookup"><span data-stu-id="a2016-270">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a><span data-ttu-id="a2016-271">Spécification d'une stratégie pour les membres</span><span class="sxs-lookup"><span data-stu-id="a2016-271">Specifying policy for members</span></span>

<span data-ttu-id="a2016-272">Les éléments [Property](property-element-net-native.md) et [Field](field-element-net-native.md) prennent en charge les types de stratégie suivants :</span><span class="sxs-lookup"><span data-stu-id="a2016-272">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="a2016-273">`Browse` : contrôle la demande d'informations sur le membre concerné, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a2016-273">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="a2016-274">`Dynamic` : contrôle l'accès au moment de l'exécution à tous les membres de type, y compris aux constructeurs, méthodes, champs, propriétés et événements, pour permettre une programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="a2016-274">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="a2016-275">Contrôle également les requêtes d'informations sur le type conteneur.</span><span class="sxs-lookup"><span data-stu-id="a2016-275">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="a2016-276">`Serialize` : contrôle l'accès au moment de l'exécution au membre pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="a2016-276">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="a2016-277">Cette stratégie peut être appliquée à des constructeurs, des champs et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="a2016-277">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="a2016-278">Les éléments [Method](method-element-net-native.md) et [Event](event-element-net-native.md) prennent en charge les types de stratégie suivants :</span><span class="sxs-lookup"><span data-stu-id="a2016-278">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="a2016-279">`Browse` : contrôle la demande d'informations sur le membre concerné, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a2016-279">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="a2016-280">`Dynamic` : contrôle l'accès au moment de l'exécution à tous les membres de type, y compris aux constructeurs, méthodes, champs, propriétés et événements, pour permettre une programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="a2016-280">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="a2016-281">Contrôle également les requêtes d'informations sur le type conteneur.</span><span class="sxs-lookup"><span data-stu-id="a2016-281">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="a2016-282">Les paramètres associés à ces types de stratégie sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a2016-282">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="a2016-283">`Auto` : utiliser le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2016-283">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="a2016-284">(Ne pas spécifier une stratégie équivaut à définir cette stratégie sur `Auto`, sauf si quelque chose la substitue.)</span><span class="sxs-lookup"><span data-stu-id="a2016-284">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="a2016-285">`Excluded` : ne jamais inclure de métadonnées pour le membre.</span><span class="sxs-lookup"><span data-stu-id="a2016-285">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="a2016-286">`Included` : activer la stratégie si le type de parent est présent dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="a2016-286">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="a2016-287">`Required` : obliger la chaîne d'outils à conserver le membre concerné même s'il semble inutilisé et à activer la stratégie pour lui.</span><span class="sxs-lookup"><span data-stu-id="a2016-287">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="a2016-288">Sémantique du fichier de directives runtime</span><span class="sxs-lookup"><span data-stu-id="a2016-288">Runtime directives file semantics</span></span>

<span data-ttu-id="a2016-289">La stratégie peut être définie simultanément pour les éléments de niveau supérieur et de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="a2016-289">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="a2016-290">Par exemple, la stratégie peut être définie pour un assembly, ainsi que pour certains des types contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="a2016-290">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="a2016-291">Si un élément particulier de niveau inférieur n'est pas représenté, il hérite la stratégie de son parent.</span><span class="sxs-lookup"><span data-stu-id="a2016-291">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="a2016-292">Par exemple, si un élément `Assembly` est présent, mais que des éléments `Type` sont absents, la stratégie spécifiée dans l'élément `Assembly` s'applique à chaque type dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="a2016-292">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="a2016-293">Plusieurs éléments peuvent aussi appliquer la stratégie au même élément de programme.</span><span class="sxs-lookup"><span data-stu-id="a2016-293">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="a2016-294">Par exemple, des éléments [Assembly](assembly-element-net-native.md) distincts peuvent définir le même élément de stratégie pour le même assembly différemment.</span><span class="sxs-lookup"><span data-stu-id="a2016-294">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="a2016-295">Les sections suivantes expliquent comment la stratégie pour un type particulier est résolue dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="a2016-295">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="a2016-296">Un élément [Type](type-element-net-native.md) ou [Method](method-element-net-native.md) d’une méthode ou type générique applique sa stratégie à toutes les instanciations qui n’ont pas leur propre stratégie.</span><span class="sxs-lookup"><span data-stu-id="a2016-296">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="a2016-297">Par exemple, un élément `Type` qui spécifie une stratégie pour <xref:System.Collections.Generic.List%601> s'applique à toutes les instances construites de ce type générique, sauf s'il est substitué pour un type générique construit particulier (comme `List<Int32>`) par un élément `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="a2016-297">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="a2016-298">Dans le cas contraire, les éléments définissent la stratégie pour l'élément de programme nommé.</span><span class="sxs-lookup"><span data-stu-id="a2016-298">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="a2016-299">Quand un élément est ambigu, le moteur recherche des correspondances, et s'il trouve une correspondance exacte, il l'utilise.</span><span class="sxs-lookup"><span data-stu-id="a2016-299">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="a2016-300">La présence de plusieurs correspondances entraîne un avertissement ou une erreur.</span><span class="sxs-lookup"><span data-stu-id="a2016-300">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="a2016-301">Si deux directives appliquent la stratégie au même élément de programme</span><span class="sxs-lookup"><span data-stu-id="a2016-301">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="a2016-302">Si deux éléments dans des fichiers de directives runtime différents essaient de définir sur des valeurs différentes le même type de stratégie pour le même élément de programme (par exemple, un assembly ou un type), le conflit est résolu comme suit :</span><span class="sxs-lookup"><span data-stu-id="a2016-302">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="a2016-303">Si l'élément `Excluded` est présent, il a la priorité.</span><span class="sxs-lookup"><span data-stu-id="a2016-303">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="a2016-304">`Required` est prioritaire sur Not Required`Required`.</span><span class="sxs-lookup"><span data-stu-id="a2016-304">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="a2016-305">`All` est prioritaire sur `PublicAndInternal`, lui-même prioritaire sur `Public`.</span><span class="sxs-lookup"><span data-stu-id="a2016-305">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="a2016-306">Tout paramètre explicite est prioritaire sur `Auto`.</span><span class="sxs-lookup"><span data-stu-id="a2016-306">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="a2016-307">Par exemple, si un projet inclut les deux fichiers de directives runtime suivants, la stratégie de sérialisation pour DataClasses.dll est définie sur `Required Public` et `All`.</span><span class="sxs-lookup"><span data-stu-id="a2016-307">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="a2016-308">Dans ce cas, la stratégie de sérialisation est résolue en tant que `Required All`.</span><span class="sxs-lookup"><span data-stu-id="a2016-308">In this case, the serialization policy would be resolved as `Required All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

<span data-ttu-id="a2016-309">Toutefois, si deux directives dans un même fichier de directives runtime essaient de définir le même type de stratégie pour le même élément de programme, l'outil de définition de schéma XML affiche un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a2016-309">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="a2016-310">Si des éléments enfants et parents appliquent le même type de stratégie</span><span class="sxs-lookup"><span data-stu-id="a2016-310">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="a2016-311">Les éléments enfants se substituent à leurs éléments parents, y compris au paramètre `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="a2016-311">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="a2016-312">La substitution est la principale raison de la spécification du paramètre `Auto`.</span><span class="sxs-lookup"><span data-stu-id="a2016-312">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="a2016-313">Dans l'exemple suivant, le paramètre de stratégie de sérialisation pour tous les éléments de `DataClasses` qui ne se trouvent pas dans `DataClasses.ViewModels` serait `Required Public` et tout ce qui se trouve à la fois dans `DataClasses` et `DataClasses.ViewModels` aurait pour paramètre `All`.</span><span class="sxs-lookup"><span data-stu-id="a2016-313">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="a2016-314">Si des génériques ouverts et des éléments instanciés appliquent le même type de stratégie</span><span class="sxs-lookup"><span data-stu-id="a2016-314">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="a2016-315">Dans l'exemple suivant, `Dictionary<int,int>` ne se voit attribuer la stratégie `Browse` que si le moteur a une autre raison de lui attribuer la stratégie `Browse` (qui serait sinon le comportement par défaut) ; toute autre instanciation de <xref:System.Collections.Generic.Dictionary%602> permet la consultation de tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="a2016-315">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a><span data-ttu-id="a2016-316">Mode de déduction de la stratégie</span><span class="sxs-lookup"><span data-stu-id="a2016-316">How policy is inferred</span></span>

<span data-ttu-id="a2016-317">Chaque type de stratégie possède un ensemble spécifique de règles qui déterminent la façon dont la présence de ce type de stratégie affecte les autres constructions.</span><span class="sxs-lookup"><span data-stu-id="a2016-317">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="a2016-318">Effet de la stratégie Browse</span><span class="sxs-lookup"><span data-stu-id="a2016-318">The effect of Browse policy</span></span>

<span data-ttu-id="a2016-319">L'application de la stratégie `Browse` à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-319">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-320">Le type de base du type est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-320">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-321">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-322">Si le type est un délégué, la méthode `Invoke` sur le type est marquée avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-322">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-323">Chaque interface du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-323">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-324">Le type de chaque attribut appliqué au type est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-324">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-325">Si le type est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-325">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-326">Si le type est générique, les types sur lesquels il est instancié sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-326">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="a2016-327">L'application de la stratégie `Browse` à une méthode implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-327">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-328">Chaque type de paramètre de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-328">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-329">Le type de retour de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-329">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-330">Le type conteneur de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-330">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-331">Si la méthode est une méthode générique instanciée, la méthode générique non instanciée est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-331">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-332">Le type de chaque attribut appliqué à la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-332">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-333">Si la méthode est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-333">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-334">Si la méthode est générique, les types sur lesquels elle est instanciée sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-334">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="a2016-335">L'application de la stratégie `Browse` à un champ implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-335">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-336">Le type de chaque attribut appliqué au champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-336">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-337">Le type du champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-337">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-338">Le type auquel appartient le champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-338">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="a2016-339">Effet de la stratégie Dynamic</span><span class="sxs-lookup"><span data-stu-id="a2016-339">The effect of Dynamic policy</span></span>

<span data-ttu-id="a2016-340">L'application de la stratégie `Dynamic` à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-340">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-341">Le type de base du type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-341">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-342">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-342">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-343">Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-343">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-344">Chaque interface du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-344">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-345">Le type de chaque attribut appliqué au type est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-345">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-346">Si le type est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-346">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-347">Si le type est générique, les types sur lesquels il est instancié sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-347">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="a2016-348">L'application de la stratégie `Dynamic` à une méthode implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-348">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-349">Chaque type de paramètre de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-349">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-350">Le type de retour de la méthode est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-350">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-351">Le type conteneur de la méthode est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-351">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-352">Si la méthode est une méthode générique instanciée, la méthode générique non instanciée est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-352">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-353">Le type de chaque attribut appliqué à la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-353">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-354">Si la méthode est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-354">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-355">Si la méthode est générique, les types sur lesquels elle est instanciée sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-355">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-356">La méthode peut être appelée par `MethodInfo.Invoke`, et la création de délégué par <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> devient possible.</span><span class="sxs-lookup"><span data-stu-id="a2016-356">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a2016-357">L'application de la stratégie `Dynamic` à un champ implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-357">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-358">Le type de chaque attribut appliqué au champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-358">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-359">Le type du champ est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-359">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-360">Le type auquel appartient le champ est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-360">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="a2016-361">Effet de la stratégie Activation</span><span class="sxs-lookup"><span data-stu-id="a2016-361">The effect of Activation policy</span></span>

<span data-ttu-id="a2016-362">L'application de la stratégie Activation à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-362">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-363">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-363">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-364">Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-364">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-365">Les constructeurs du type sont marqués avec la stratégie `Activation`.</span><span class="sxs-lookup"><span data-stu-id="a2016-365">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="a2016-366">L'application de la stratégie `Activation` à une méthode implique la modification de stratégie suivante :</span><span class="sxs-lookup"><span data-stu-id="a2016-366">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="a2016-367">Le constructeur peut être appelé par les méthodes <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> et <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2016-367">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="a2016-368">Pour les méthodes, la stratégie `Activation` affecte uniquement les constructeurs.</span><span class="sxs-lookup"><span data-stu-id="a2016-368">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="a2016-369">L'application de la stratégie `Activation` à un champ n'a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="a2016-369">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="a2016-370">Effet de la stratégie Serialize</span><span class="sxs-lookup"><span data-stu-id="a2016-370">The effect of Serialize policy</span></span>

<span data-ttu-id="a2016-371">La stratégie `Serialize` permet l'utilisation de sérialiseurs courants basés sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="a2016-371">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="a2016-372">Toutefois, comme les modèles d'accès à la réflexion exacts des sérialiseurs non-Microsoft ne sont pas connus de Microsoft, cette stratégie peut manquer d'efficacité.</span><span class="sxs-lookup"><span data-stu-id="a2016-372">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="a2016-373">L'application de la stratégie `Serialize` à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-373">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-374">Le type de base du type est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-374">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-375">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="a2016-375">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="a2016-376">Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="a2016-376">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="a2016-377">Si le type est une énumération, un tableau du type est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-377">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-378">Si le type implémente <xref:System.Collections.Generic.IEnumerable%601>, `T` est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-378">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-379">Si le type est <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601> ou <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` et <xref:System.Collections.Generic.List%601> sont marqués avec la stratégie `Serialize`, mais aucun membre du type d'interface n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-379">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-380">Si le type est <xref:System.Collections.Generic.List%601>, aucun de ses membres n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-380">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-381">Si le type est <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> est marqué avec la stratégie `Serialize`,</span><span class="sxs-lookup"><span data-stu-id="a2016-381">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="a2016-382">mais aucun de ses membres n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-382">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-383">Si le type est <xref:System.Collections.Generic.Dictionary%602>, aucun de ses membres n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-383">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-384">Si le type implémente <xref:System.Collections.Generic.IDictionary%602>, `TKey` et `TValue` sont marqués avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-384">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-385">Chaque constructeur, chaque accesseur de propriété et chaque champ sont marqués avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-385">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="a2016-386">L'application de la stratégie `Serialize` à une méthode implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-386">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-387">Le type conteneur est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-387">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-388">Le type de retour de la méthode est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-388">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="a2016-389">L'application de la stratégie `Serialize` à un champ implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2016-389">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="a2016-390">Le type conteneur est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-390">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="a2016-391">Le type du champ est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="a2016-391">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="a2016-392">Effet des stratégies XmlSerializer, DataContractSerializer et DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="a2016-392">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="a2016-393">Contrairement à la stratégie de `Serialize`, qui est destinée aux sérialiseurs basés sur la réflexion, les stratégies <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sont utilisées pour activer un ensemble de sérialiseurs connus de la chaîne d’outils .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a2016-393">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="a2016-394">Ces sérialiseurs ne sont pas implémentés à l'aide de la réflexion, mais le jeu de types qui peuvent être sérialisés au moment de l'exécution est déterminé de la même manière que les types pouvant faire l'objet d'une réflexion.</span><span class="sxs-lookup"><span data-stu-id="a2016-394">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="a2016-395">Appliquer une de ces stratégies à un type permet de sérialiser celui-ci avec le sérialiseur correspondant.</span><span class="sxs-lookup"><span data-stu-id="a2016-395">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="a2016-396">En outre, tous les types que le moteur de sérialisation peut déterminer de manière statique comme nécessitant une sérialisation sont également sérialisables.</span><span class="sxs-lookup"><span data-stu-id="a2016-396">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="a2016-397">Ces stratégies n'ont aucun effet sur les méthodes ou champs.</span><span class="sxs-lookup"><span data-stu-id="a2016-397">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="a2016-398">Pour plus d’informations, consultez la section « Différences entre les sérialiseurs » dans [Migration de votre application du Windows Store vers .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a2016-398">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2016-399">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2016-399">See also</span></span>

- [<span data-ttu-id="a2016-400">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="a2016-400">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a2016-401">Réflexion et .NET Native</span><span class="sxs-lookup"><span data-stu-id="a2016-401">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
