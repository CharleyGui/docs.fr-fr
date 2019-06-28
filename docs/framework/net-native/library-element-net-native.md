---
title: <Library> Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce001ed25d7704301d7f809887a445e3492e93fc
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422534"
---
# <a name="library-element-net-native"></a><span data-ttu-id="a6ebc-102">\<Bibliothèque >, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a6ebc-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="a6ebc-103">Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="a6ebc-104">\<Directives>, élément</span><span class="sxs-lookup"><span data-stu-id="a6ebc-104">\<Directives> Element</span></span>  
<span data-ttu-id="a6ebc-105">\<Library>, élément</span><span class="sxs-lookup"><span data-stu-id="a6ebc-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6ebc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6ebc-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6ebc-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a6ebc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a6ebc-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6ebc-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a6ebc-109">Attributes</span></span>  
  
|<span data-ttu-id="a6ebc-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a6ebc-110">Attribute</span></span>|<span data-ttu-id="a6ebc-111">Description</span><span class="sxs-lookup"><span data-stu-id="a6ebc-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="a6ebc-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-112">Required attribute.</span></span> <span data-ttu-id="a6ebc-113">Spécifie le nom d'un assembly.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="a6ebc-114">Les éléments enfants de cet élément `<Library>` définissent la stratégie de réflexion runtime pour les types et membres de type se trouvant dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a6ebc-115">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="a6ebc-115">Name attribute</span></span>  
  
|<span data-ttu-id="a6ebc-116">Value</span><span class="sxs-lookup"><span data-stu-id="a6ebc-116">Value</span></span>|<span data-ttu-id="a6ebc-117">Description</span><span class="sxs-lookup"><span data-stu-id="a6ebc-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a6ebc-118">*nom_assembly*</span><span class="sxs-lookup"><span data-stu-id="a6ebc-118">*assembly_name*</span></span>|<span data-ttu-id="a6ebc-119">Nom simple de l’assembly, sans son extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="a6ebc-120">Cet attribut correspond à la propriété <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a6ebc-121">Par exemple, le nom d’un assembly nommé Extensions.dll est « Extensions ».</span><span class="sxs-lookup"><span data-stu-id="a6ebc-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="a6ebc-122">Consultez la section Notes pour connaître une forme particulière de *nom_assembly* qui prend en charge l’inclusion conditionnelle de métadonnées à partir de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6ebc-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a6ebc-123">Child Elements</span></span>  
  
|<span data-ttu-id="a6ebc-124">Élément</span><span class="sxs-lookup"><span data-stu-id="a6ebc-124">Element</span></span>|<span data-ttu-id="a6ebc-125">Description</span><span class="sxs-lookup"><span data-stu-id="a6ebc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6ebc-126">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="a6ebc-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="a6ebc-127">Applique la stratégie à tous les types d'un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="a6ebc-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="a6ebc-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="a6ebc-129">Applique la stratégie à tous les types d'un espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="a6ebc-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="a6ebc-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="a6ebc-131">Applique la stratégie à un type particulier, tel qu'une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="a6ebc-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="a6ebc-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="a6ebc-133">Applique la stratégie à un type générique construit.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="a6ebc-134">Par exemple, vous pouvez utiliser un élément [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) afin de définir une stratégie pour un type `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6ebc-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a6ebc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a6ebc-136">Élément</span><span class="sxs-lookup"><span data-stu-id="a6ebc-136">Element</span></span>|<span data-ttu-id="a6ebc-137">Description</span><span class="sxs-lookup"><span data-stu-id="a6ebc-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6ebc-138">\<Directives></span><span class="sxs-lookup"><span data-stu-id="a6ebc-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="a6ebc-139">Élément racine d'un fichier de directives de runtime.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6ebc-140">Notes</span><span class="sxs-lookup"><span data-stu-id="a6ebc-140">Remarks</span></span>  
 <span data-ttu-id="a6ebc-141">L’élément [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) peut contenir zéro, un ou plusieurs éléments `<Library>`.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="a6ebc-142">L'élément `<Library>` sert de conteneur pour la définition des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution ; cet élément n'exprime pas la stratégie.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="a6ebc-143">Au moment de la compilation, les outils du compilateur recherchent uniquement dans la bibliothèque désignée par l'élément `<Library>` les éléments de programme identifiés par ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="a6ebc-144">En revanche, les outils du compilateur recherchent dans toutes les bibliothèques, y compris les bibliothèques principales du Framework .NET, les éléments de programme identifiés par les éléments enfants de l’élément [\<Application>](../../../docs/framework/net-native/application-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a6ebc-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="a6ebc-145">Les directives `<Library>` peuvent être utilisées de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="a6ebc-146">Si le nom de la `<Library>` élément commence et se termine par un astérisque (\*), la `<Library>` directive a un effet uniquement si l’assembly spécifié entre les astérisques est référencé par l’application.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="a6ebc-147">Par exemple, la directive runtime suivante s’applique uniquement si l’assembly Utilities.dll est référencé par l’application.</span><span class="sxs-lookup"><span data-stu-id="a6ebc-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6ebc-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6ebc-148">See also</span></span>

- [<span data-ttu-id="a6ebc-149">\<Application > élément</span><span class="sxs-lookup"><span data-stu-id="a6ebc-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)
- [<span data-ttu-id="a6ebc-150">\<Directives > élément</span><span class="sxs-lookup"><span data-stu-id="a6ebc-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)
- [<span data-ttu-id="a6ebc-151">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a6ebc-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a6ebc-152">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="a6ebc-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
