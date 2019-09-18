---
title: Guide de référence du fichier de configuration des directives runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adfc0ae6d9bdae333daacee525c7775acd5a8029
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049140"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="0c8a3-102">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0c8a3-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="0c8a3-103">Un fichier de directives runtime (.rd.xml) est un fichier de configuration XML qui spécifie si les éléments de programme désignés sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="0c8a3-104">Voici un exemple de fichier de directives runtime :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="0c8a3-105">Structure d'un fichier de directives runtime</span><span class="sxs-lookup"><span data-stu-id="0c8a3-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="0c8a3-106">Le fichier de directives runtime utilise l'espace de noms `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="0c8a3-107">L’élément racine est l’élément [Directives](directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="0c8a3-108">Il peut contenir zéro ou plusieurs éléments [Library](library-element-net-native.md) et zéro ou un élément [Application](application-element-net-native.md), comme indiqué dans la structure suivante.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="0c8a3-109">Les attributs de l’élément [Application](application-element-net-native.md) peuvent définir une stratégie de réflexion runtime à l’échelle de l’application, ou peuvent servir de conteneur pour les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="0c8a3-110">L’élément [Library](library-element-net-native.md), quant à lui, sert simplement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="0c8a3-111">Les enfants des éléments[Application](application-element-net-native.md) et [Library](library-element-net-native.md) définissent les types, méthodes, champs, propriétés et événements qui sont disponibles pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="0c8a3-112">Pour obtenir des informations de référence, choisissez les éléments dans la structure suivante ou consultez [Éléments de directive runtime](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="0c8a3-113">Dans la hiérarchie suivante, les points de suspension marquent une structure récursive.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="0c8a3-114">Les informations entre crochets indiquent si l'élément concerné est facultatif ou obligatoire, et, s'il est utilisé, le nombre d'instances autorisées (une ou plusieurs).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="0c8a3-115">[Directives](directives-element-net-native.md) [1:1] [application](application-element-net-native.md) [0:1] [assembly](assembly-element-net-native.md) [0 : m] [espace de noms](namespace-element-net-native.md) [0 : m].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-116">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-116">.</span></span> <span data-ttu-id="0c8a3-117">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-117">.</span></span>
<span data-ttu-id="0c8a3-118">[Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-119">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-119">.</span></span> <span data-ttu-id="0c8a3-120">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-120">.</span></span>
<span data-ttu-id="0c8a3-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-122">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-122">.</span></span> <span data-ttu-id="0c8a3-123">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-123">.</span></span>
<span data-ttu-id="0c8a3-124">[Espace de noms](namespace-element-net-native.md) [0 : M] [Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-125">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-125">.</span></span> <span data-ttu-id="0c8a3-126">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-126">.</span></span>
<span data-ttu-id="0c8a3-127">[Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-128">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-128">.</span></span> <span data-ttu-id="0c8a3-129">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-129">.</span></span>
<span data-ttu-id="0c8a3-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-131">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-131">.</span></span> <span data-ttu-id="0c8a3-132">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-132">.</span></span>
<span data-ttu-id="0c8a3-133">[Type](type-element-net-native.md) [0 : M] [Sous-types](subtypes-element-net-native.md) (sous-classes du type conteneur) O :1 [Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-134">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-134">.</span></span> <span data-ttu-id="0c8a3-135">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-135">.</span></span>
<span data-ttu-id="0c8a3-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-137">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-137">.</span></span> <span data-ttu-id="0c8a3-138">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-138">.</span></span>
<span data-ttu-id="0c8a3-139">[AttributeImplies](attributeimplies-element-net-native.md) (le type conteneur est un attribut) O :1 [GenericParameter](genericparameter-element-net-native.md) [0 : M] [Méthode](method-element-net-native.md) [0 : M] [Paramètre](parameter-element-net-native.md) [0 : M] [TypeParameter](typeparameter-element-net-native.md) [0 : M] [GenericParameter](genericparameter-element-net-native.md) [0 : M] [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0 : M] [Propriété](property-element-net-native.md) [0 : M] [Champ](field-element-net-native.md) [0 : M] [Événement](event-element-net-native.md) [0 : M] [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M] [Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-140">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-140">.</span></span> <span data-ttu-id="0c8a3-141">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-141">.</span></span>
<span data-ttu-id="0c8a3-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-143">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-143">.</span></span> <span data-ttu-id="0c8a3-144">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-144">.</span></span>
<span data-ttu-id="0c8a3-145">[Méthode](method-element-net-native.md) [0 : M] [Paramètre](parameter-element-net-native.md) [0 : M] [TypeParameter](typeparameter-element-net-native.md) [0 : M] [GenericParameter](genericparameter-element-net-native.md) [0 : M] [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0 : M] [Propriété](property-element-net-native.md) [0 : M] [Champ](field-element-net-native.md) [0 : M] [Événement](event-element-net-native.md) [0 : M] [Bibliothèque](library-element-net-native.md) [0 : M] [Assembly](assembly-element-net-native.md) [0 : M] [Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-146">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-146">.</span></span> <span data-ttu-id="0c8a3-147">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-147">.</span></span>
<span data-ttu-id="0c8a3-148">[Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-149">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-149">.</span></span> <span data-ttu-id="0c8a3-150">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-150">.</span></span>
<span data-ttu-id="0c8a3-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-152">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-152">.</span></span> <span data-ttu-id="0c8a3-153">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-153">.</span></span>
<span data-ttu-id="0c8a3-154">[Espace de noms](namespace-element-net-native.md) [0 : M] [Espace de noms](namespace-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-155">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-155">.</span></span> <span data-ttu-id="0c8a3-156">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-156">.</span></span>
<span data-ttu-id="0c8a3-157">[Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-158">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-158">.</span></span> <span data-ttu-id="0c8a3-159">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-159">.</span></span>
<span data-ttu-id="0c8a3-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-161">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-161">.</span></span> <span data-ttu-id="0c8a3-162">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-162">.</span></span>
<span data-ttu-id="0c8a3-163">[Type](type-element-net-native.md) [0 : M] [Sous-types](subtypes-element-net-native.md) (sous-classes du type conteneur) O :1 [Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-164">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-164">.</span></span> <span data-ttu-id="0c8a3-165">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-165">.</span></span>
<span data-ttu-id="0c8a3-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-167">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-167">.</span></span> <span data-ttu-id="0c8a3-168">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-168">.</span></span>
<span data-ttu-id="0c8a3-169">[AttributeImplies](attributeimplies-element-net-native.md) (le type conteneur est un attribut) O :1 [GenericParameter](genericparameter-element-net-native.md) [0 : M] [Méthode](method-element-net-native.md) [0 : M] [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0 : M] [Propriété](property-element-net-native.md) [0 : M] [Champ](field-element-net-native.md) [0 : M] [Événement](event-element-net-native.md) [0 : M] [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M] [Type](type-element-net-native.md) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="0c8a3-170">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-170">.</span></span> <span data-ttu-id="0c8a3-171">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-171">.</span></span>
<span data-ttu-id="0c8a3-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M].</span><span class="sxs-lookup"><span data-stu-id="0c8a3-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="0c8a3-173">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-173">.</span></span> <span data-ttu-id="0c8a3-174">.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-174">.</span></span>
<span data-ttu-id="0c8a3-175">[Méthode](method-element-net-native.md) [0 : M] [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0 : M] [Propriété](property-element-net-native.md) [0 : M] [Champ](field-element-net-native.md) [0 : M] [Événement](event-element-net-native.md) [0 : M]</span><span class="sxs-lookup"><span data-stu-id="0c8a3-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="0c8a3-176">L’élément [Application](application-element-net-native.md) peut n’avoir aucun attribut, ou peut avoir les attributs de stratégie présentés dans la section [Stratégie et directives runtime](#Directives).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="0c8a3-177">Un élément [Library](library-element-net-native.md) possède un attribut unique (`Name`) qui spécifie le nom d’une bibliothèque ou d’un assembly, sans son extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="0c8a3-178">Par exemple, l’élément [Library](library-element-net-native.md) suivant s’applique à un assembly nommé Extensions.dll.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="0c8a3-179">Stratégie et directives runtime</span><span class="sxs-lookup"><span data-stu-id="0c8a3-179">Runtime directives and policy</span></span>

<span data-ttu-id="0c8a3-180">L’élément [Application](application-element-net-native.md) lui-même et les éléments enfants des éléments [Library](library-element-net-native.md) et [Application](application-element-net-native.md) expriment la stratégie ; autrement dit, ils définissent la façon dont une application peut appliquer la réflexion à un élément de programme.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="0c8a3-181">Le type de stratégie est défini par un attribut de l'élément (par exemple, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="0c8a3-182">La valeur de stratégie est définie par la valeur de l'attribut (par exemple, `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="0c8a3-183">Toute stratégie spécifiée par un attribut d'un élément s'applique à tous les éléments enfants qui ne définissent pas de valeur pour cette stratégie.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="0c8a3-184">Par exemple, si une stratégie est spécifiée par un élément [Type](type-element-net-native.md), elle s’applique à tous les types et membres contenus pour lesquels une stratégie n’est pas explicitement définie.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="0c8a3-185">La stratégie qui peut être exprimée par les éléments [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) et [Type](type-element-net-native.md) diffère de la stratégie qui peut être exprimée pour des membres spécifiques (par les éléments [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), et [Event](event-element-net-native.md)).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="0c8a3-186">Spécification d'une stratégie pour des assemblys, des espaces de noms et des types</span><span class="sxs-lookup"><span data-stu-id="0c8a3-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="0c8a3-187">Les éléments [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) et [Type](type-element-net-native.md) prennent en charge les types de stratégie suivants :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="0c8a3-188">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-188">`Activate`.</span></span> <span data-ttu-id="0c8a3-189">Contrôle l'accès aux constructeurs, pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="0c8a3-190">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-190">`Browse`.</span></span> <span data-ttu-id="0c8a3-191">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="0c8a3-192">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-192">`Dynamic`.</span></span> <span data-ttu-id="0c8a3-193">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="0c8a3-194">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-194">`Serialize`.</span></span> <span data-ttu-id="0c8a3-195">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation des instances de types par des bibliothèques tierces comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="0c8a3-196">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-196">`DataContractSerializer`.</span></span> <span data-ttu-id="0c8a3-197">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="0c8a3-198">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="0c8a3-199">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="0c8a3-200">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-200">`XmlSerializer`.</span></span> <span data-ttu-id="0c8a3-201">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="0c8a3-202">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-202">`MarshalObject`.</span></span> <span data-ttu-id="0c8a3-203">Contrôle la stratégie de marshaling des types référence vers WinRT et COM.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="0c8a3-204">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-204">`MarshalDelegate`.</span></span> <span data-ttu-id="0c8a3-205">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="0c8a3-206">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="0c8a3-206">`MarshalStructure` .</span></span> <span data-ttu-id="0c8a3-207">Stratégie de contrôles pour le marshaling de structures en code natif.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="0c8a3-208">Les paramètres associés à ces types de stratégie sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="0c8a3-209">`All`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-209">`All`.</span></span> <span data-ttu-id="0c8a3-210">Activer la stratégie pour tous les types et membres que la chaîne d'outils ne supprime pas.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="0c8a3-211">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-211">`Auto`.</span></span> <span data-ttu-id="0c8a3-212">Utiliser le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-212">Use the default behavior.</span></span> <span data-ttu-id="0c8a3-213">(Ne pas spécifier une stratégie équivaut à définir cette stratégie sur `Auto` , sauf si elle est substituée, par exemple par un élément parent.)</span><span class="sxs-lookup"><span data-stu-id="0c8a3-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="0c8a3-214">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-214">`Excluded`.</span></span> <span data-ttu-id="0c8a3-215">Désactiver la stratégie pour l'élément de programme.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="0c8a3-216">`Public`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-216">`Public`.</span></span> <span data-ttu-id="0c8a3-217">Activer la stratégie pour les types ou membres publics, sauf si la chaîne d'outils détermine que le membre n'est pas nécessaire et donc le supprime.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="0c8a3-218">(Dans ce dernier cas, vous devez utiliser `Required Public` pour vous assurer que le membre est conservé et dispose de fonctionnalités de réflexion.)</span><span class="sxs-lookup"><span data-stu-id="0c8a3-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="0c8a3-219">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-219">`PublicAndInternal`.</span></span> <span data-ttu-id="0c8a3-220">Activer la stratégie pour les types ou membres publics et internes si la chaîne d'outils ne les supprime pas.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="0c8a3-221">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-221">`Required Public`.</span></span> <span data-ttu-id="0c8a3-222">Obliger la chaîne d'outils à conserver les membres et types publics, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="0c8a3-223">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="0c8a3-224">Obliger la chaîne d'outils à conserver les types et membres publics et internes, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="0c8a3-225">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-225">`Required All`.</span></span> <span data-ttu-id="0c8a3-226">Obliger la chaîne d'outils à conserver tous les membres et types, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="0c8a3-227">Par exemple, le fichier de directives runtime suivant définit la stratégie pour tous les types et membres de l'assembly DataClasses.dll.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="0c8a3-228">Il autorise la réflexion pour la sérialisation de toutes les propriétés publiques, la consultation de tous les types et membres de type, l'activation pour tous les types (en raison de l'attribut `Dynamic`) et la réflexion pour tous les membres et types publics.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="0c8a3-229">Spécification d'une stratégie pour les membres</span><span class="sxs-lookup"><span data-stu-id="0c8a3-229">Specifying policy for members</span></span>

<span data-ttu-id="0c8a3-230">Les éléments [Property](property-element-net-native.md) et [Field](field-element-net-native.md) prennent en charge les types de stratégie suivants :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="0c8a3-231">`Browse` : contrôle la demande d'informations sur le membre concerné, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="0c8a3-232">`Dynamic` : contrôle l'accès au moment de l'exécution à tous les membres de type, y compris aux constructeurs, méthodes, champs, propriétés et événements, pour permettre une programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="0c8a3-233">Contrôle également les requêtes d'informations sur le type conteneur.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="0c8a3-234">`Serialize` : contrôle l'accès au moment de l'exécution au membre pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="0c8a3-235">Cette stratégie peut être appliquée à des constructeurs, des champs et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="0c8a3-236">Les éléments [Method](method-element-net-native.md) et [Event](event-element-net-native.md) prennent en charge les types de stratégie suivants :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="0c8a3-237">`Browse` : contrôle la demande d'informations sur le membre concerné, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="0c8a3-238">`Dynamic` : contrôle l'accès au moment de l'exécution à tous les membres de type, y compris aux constructeurs, méthodes, champs, propriétés et événements, pour permettre une programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="0c8a3-239">Contrôle également les requêtes d'informations sur le type conteneur.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="0c8a3-240">Les paramètres associés à ces types de stratégie sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="0c8a3-241">`Auto` : utiliser le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="0c8a3-242">(Ne pas spécifier une stratégie équivaut à définir cette stratégie sur `Auto`, sauf si quelque chose la substitue.)</span><span class="sxs-lookup"><span data-stu-id="0c8a3-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="0c8a3-243">`Excluded` : ne jamais inclure de métadonnées pour le membre.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="0c8a3-244">`Included` : activer la stratégie si le type de parent est présent dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="0c8a3-245">`Required` : obliger la chaîne d'outils à conserver le membre concerné même s'il semble inutilisé et à activer la stratégie pour lui.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="0c8a3-246">Sémantique du fichier de directives runtime</span><span class="sxs-lookup"><span data-stu-id="0c8a3-246">Runtime directives file semantics</span></span>

<span data-ttu-id="0c8a3-247">La stratégie peut être définie simultanément pour les éléments de niveau supérieur et de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="0c8a3-248">Par exemple, la stratégie peut être définie pour un assembly, ainsi que pour certains des types contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="0c8a3-249">Si un élément particulier de niveau inférieur n'est pas représenté, il hérite la stratégie de son parent.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="0c8a3-250">Par exemple, si un élément `Assembly` est présent, mais que des éléments `Type` sont absents, la stratégie spécifiée dans l'élément `Assembly` s'applique à chaque type dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="0c8a3-251">Plusieurs éléments peuvent aussi appliquer la stratégie au même élément de programme.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="0c8a3-252">Par exemple, des éléments [Assembly](assembly-element-net-native.md) distincts peuvent définir le même élément de stratégie pour le même assembly différemment.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="0c8a3-253">Les sections suivantes expliquent comment la stratégie pour un type particulier est résolue dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="0c8a3-254">Un élément [Type](type-element-net-native.md) ou [Method](method-element-net-native.md) d’une méthode ou type générique applique sa stratégie à toutes les instanciations qui n’ont pas leur propre stratégie.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="0c8a3-255">Par exemple, un élément `Type` qui spécifie une stratégie pour <xref:System.Collections.Generic.List%601> s'applique à toutes les instances construites de ce type générique, sauf s'il est substitué pour un type générique construit particulier (comme `List<Int32>`) par un élément `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="0c8a3-256">Dans le cas contraire, les éléments définissent la stratégie pour l'élément de programme nommé.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="0c8a3-257">Quand un élément est ambigu, le moteur recherche des correspondances, et s'il trouve une correspondance exacte, il l'utilise.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="0c8a3-258">La présence de plusieurs correspondances entraîne un avertissement ou une erreur.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="0c8a3-259">Si deux directives appliquent la stratégie au même élément de programme</span><span class="sxs-lookup"><span data-stu-id="0c8a3-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="0c8a3-260">Si deux éléments dans des fichiers de directives runtime différents essaient de définir sur des valeurs différentes le même type de stratégie pour le même élément de programme (par exemple, un assembly ou un type), le conflit est résolu comme suit :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="0c8a3-261">Si l'élément `Excluded` est présent, il a la priorité.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="0c8a3-262">`Required` est prioritaire sur Not Required`Required`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="0c8a3-263">`All` est prioritaire sur `PublicAndInternal`, lui-même prioritaire sur `Public`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="0c8a3-264">Tout paramètre explicite est prioritaire sur `Auto`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="0c8a3-265">Par exemple, si un projet inclut les deux fichiers de directives runtime suivants, la stratégie de sérialisation pour DataClasses.dll est définie sur `Required Public` et `All`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="0c8a3-266">Dans ce cas, la stratégie de sérialisation est résolue en tant que `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="0c8a3-267">Toutefois, si deux directives dans un même fichier de directives runtime essaient de définir le même type de stratégie pour le même élément de programme, l'outil de définition de schéma XML affiche un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="0c8a3-268">Si des éléments enfants et parents appliquent le même type de stratégie</span><span class="sxs-lookup"><span data-stu-id="0c8a3-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="0c8a3-269">Les éléments enfants se substituent à leurs éléments parents, y compris au paramètre `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="0c8a3-270">La substitution est la principale raison de la spécification du paramètre `Auto`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="0c8a3-271">Dans l'exemple suivant, le paramètre de stratégie de sérialisation pour tous les éléments de `DataClasses` qui ne se trouvent pas dans `DataClasses.ViewModels` serait `Required Public` et tout ce qui se trouve à la fois dans `DataClasses` et `DataClasses.ViewModels` aurait pour paramètre `All`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="0c8a3-272">Si des génériques ouverts et des éléments instanciés appliquent le même type de stratégie</span><span class="sxs-lookup"><span data-stu-id="0c8a3-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="0c8a3-273">Dans l'exemple suivant, `Dictionary<int,int>` ne se voit attribuer la stratégie `Browse` que si le moteur a une autre raison de lui attribuer la stratégie `Browse` (qui serait sinon le comportement par défaut) ; toute autre instanciation de <xref:System.Collections.Generic.Dictionary%602> permet la consultation de tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="0c8a3-274">Mode de déduction de la stratégie</span><span class="sxs-lookup"><span data-stu-id="0c8a3-274">How policy is inferred</span></span>

<span data-ttu-id="0c8a3-275">Chaque type de stratégie possède un ensemble spécifique de règles qui déterminent la façon dont la présence de ce type de stratégie affecte les autres constructions.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="0c8a3-276">Effet de la stratégie Browse</span><span class="sxs-lookup"><span data-stu-id="0c8a3-276">The effect of Browse policy</span></span>

<span data-ttu-id="0c8a3-277">L'application de la stratégie `Browse` à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-278">Le type de base du type est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-279">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-280">Si le type est un délégué, la méthode `Invoke` sur le type est marquée avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-281">Chaque interface du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-282">Le type de chaque attribut appliqué au type est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-283">Si le type est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-284">Si le type est générique, les types sur lesquels il est instancié sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="0c8a3-285">L'application de la stratégie `Browse` à une méthode implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-286">Chaque type de paramètre de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-287">Le type de retour de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-288">Le type conteneur de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-289">Si la méthode est une méthode générique instanciée, la méthode générique non instanciée est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-290">Le type de chaque attribut appliqué à la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-291">Si la méthode est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-292">Si la méthode est générique, les types sur lesquels elle est instanciée sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="0c8a3-293">L'application de la stratégie `Browse` à un champ implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-294">Le type de chaque attribut appliqué au champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-295">Le type du champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-296">Le type auquel appartient le champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="0c8a3-297">Effet de la stratégie Dynamic</span><span class="sxs-lookup"><span data-stu-id="0c8a3-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="0c8a3-298">L'application de la stratégie `Dynamic` à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-299">Le type de base du type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-300">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-301">Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-302">Chaque interface du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-303">Le type de chaque attribut appliqué au type est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-304">Si le type est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-305">Si le type est générique, les types sur lesquels il est instancié sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="0c8a3-306">L'application de la stratégie `Dynamic` à une méthode implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-307">Chaque type de paramètre de la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-308">Le type de retour de la méthode est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-309">Le type conteneur de la méthode est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-310">Si la méthode est une méthode générique instanciée, la méthode générique non instanciée est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-311">Le type de chaque attribut appliqué à la méthode est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-312">Si la méthode est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-313">Si la méthode est générique, les types sur lesquels elle est instanciée sont marqués avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-314">La méthode peut être appelée par `MethodInfo.Invoke`, et la création de délégué par <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> devient possible.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0c8a3-315">L'application de la stratégie `Dynamic` à un champ implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-316">Le type de chaque attribut appliqué au champ est marqué avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-317">Le type du champ est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-318">Le type auquel appartient le champ est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="0c8a3-319">Effet de la stratégie Activation</span><span class="sxs-lookup"><span data-stu-id="0c8a3-319">The effect of Activation policy</span></span>

<span data-ttu-id="0c8a3-320">L'application de la stratégie Activation à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-321">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-322">Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-323">Les constructeurs du type sont marqués avec la stratégie `Activation`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="0c8a3-324">L'application de la stratégie `Activation` à une méthode implique la modification de stratégie suivante :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="0c8a3-325">Le constructeur peut être appelé par les méthodes <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> et <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0c8a3-326">Pour les méthodes, la stratégie `Activation` affecte uniquement les constructeurs.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="0c8a3-327">L'application de la stratégie `Activation` à un champ n'a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="0c8a3-328">Effet de la stratégie Serialize</span><span class="sxs-lookup"><span data-stu-id="0c8a3-328">The effect of Serialize policy</span></span>

<span data-ttu-id="0c8a3-329">La stratégie `Serialize` permet l'utilisation de sérialiseurs courants basés sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="0c8a3-330">Toutefois, comme les modèles d'accès à la réflexion exacts des sérialiseurs non-Microsoft ne sont pas connus de Microsoft, cette stratégie peut manquer d'efficacité.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="0c8a3-331">L'application de la stratégie `Serialize` à un type implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-332">Le type de base du type est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-333">Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="0c8a3-334">Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="0c8a3-335">Si le type est une énumération, un tableau du type est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-336">Si le type implémente <xref:System.Collections.Generic.IEnumerable%601>, `T` est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-337">Si le type est <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601> ou <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` et <xref:System.Collections.Generic.List%601> sont marqués avec la stratégie `Serialize`, mais aucun membre du type d'interface n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-338">Si le type est <xref:System.Collections.Generic.List%601>, aucun de ses membres n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-339">Si le type est <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> est marqué avec la stratégie `Serialize`,</span><span class="sxs-lookup"><span data-stu-id="0c8a3-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="0c8a3-340">mais aucun de ses membres n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-341">Si le type est <xref:System.Collections.Generic.Dictionary%602>, aucun de ses membres n'est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-342">Si le type implémente <xref:System.Collections.Generic.IDictionary%602>, `TKey` et `TValue` sont marqués avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-343">Chaque constructeur, chaque accesseur de propriété et chaque champ sont marqués avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="0c8a3-344">L'application de la stratégie `Serialize` à une méthode implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-345">Le type conteneur est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-346">Le type de retour de la méthode est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="0c8a3-347">L'application de la stratégie `Serialize` à un champ implique les modifications de stratégie suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c8a3-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="0c8a3-348">Le type conteneur est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="0c8a3-349">Le type du champ est marqué avec la stratégie `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="0c8a3-350">Effet des stratégies XmlSerializer, DataContractSerializer et DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="0c8a3-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="0c8a3-351">Contrairement à `Serialize` la stratégie, qui est destinée aux sérialiseurs basés sur la réflexion <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>les stratégies <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , et sont utilisées pour activer un ensemble de sérialiseurs qui sont connus de la chaîne d’outils .net native.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="0c8a3-352">Ces sérialiseurs ne sont pas implémentés à l'aide de la réflexion, mais le jeu de types qui peuvent être sérialisés au moment de l'exécution est déterminé de la même manière que les types pouvant faire l'objet d'une réflexion.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="0c8a3-353">Appliquer une de ces stratégies à un type permet de sérialiser celui-ci avec le sérialiseur correspondant.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="0c8a3-354">En outre, tous les types que le moteur de sérialisation peut déterminer de manière statique comme nécessitant une sérialisation sont également sérialisables.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="0c8a3-355">Ces stratégies n'ont aucun effet sur les méthodes ou champs.</span><span class="sxs-lookup"><span data-stu-id="0c8a3-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="0c8a3-356">Pour plus d’informations, consultez la section « Différences entre les sérialiseurs » dans [Migration de votre application du Windows Store vers .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="0c8a3-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c8a3-357">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c8a3-357">See also</span></span>

- [<span data-ttu-id="0c8a3-358">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="0c8a3-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="0c8a3-359">Réflexion et .NET Native</span><span class="sxs-lookup"><span data-stu-id="0c8a3-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
