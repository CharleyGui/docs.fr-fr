---
title: Éléments de directive runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049271"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="f8540-102">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="f8540-102">Runtime Directive Elements</span></span>
<span data-ttu-id="f8540-103">Le format du fichier de directives runtime (rd.xml) prend en charge les éléments de directive runtime suivants.</span><span class="sxs-lookup"><span data-stu-id="f8540-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="f8540-104">Pour voir une représentation hiérarchique, consultez [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="f8540-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="f8540-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="f8540-106">Applique la stratégie de réflexion runtime à tous les types utilisés par l'application et sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f8540-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="f8540-107">Il s’agit d’un enfant de l’élément [\<Directives>](directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="f8540-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="f8540-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="f8540-109">Applique la stratégie runtime à tous les types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="f8540-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="f8540-110">Il s’agit d’un enfant des éléments [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="f8540-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="f8540-112">Si sa directive [\<Type>](type-element-net-native.md) conteneur est un attribut, applique la stratégie runtime aux éléments de code auxquels cet attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="f8540-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="f8540-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="f8540-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="f8540-114">Élément racine dans chaque fichier de directives Runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f8540-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="f8540-115">Ses éléments enfants sont [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="f8540-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="f8540-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="f8540-117">Applique la stratégie runtime à un événement.</span><span class="sxs-lookup"><span data-stu-id="f8540-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="f8540-118">Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="f8540-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="f8540-120">Applique la stratégie runtime à un champ.</span><span class="sxs-lookup"><span data-stu-id="f8540-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="f8540-121">Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="f8540-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="f8540-123">Applique la stratégie runtime au type de paramètre d'un type ou d'une méthode générique.</span><span class="sxs-lookup"><span data-stu-id="f8540-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="f8540-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="f8540-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="f8540-125">Applique la stratégie runtime à un type, si cette stratégie a été appliquée à la méthode ou au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="f8540-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="f8540-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="f8540-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="f8540-127">Applique la stratégie runtime à tous les types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="f8540-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="f8540-128">Il s’agit d’un enfant des éléments [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="f8540-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="f8540-130">Applique la stratégie runtime à une méthode.</span><span class="sxs-lookup"><span data-stu-id="f8540-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="f8540-131">Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="f8540-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="f8540-133">Applique la stratégie runtime à une méthode générique construite.</span><span class="sxs-lookup"><span data-stu-id="f8540-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="f8540-134">Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="f8540-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="f8540-136">Applique la stratégie runtime à tous les types d'un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f8540-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="f8540-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="f8540-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="f8540-138">Applique la stratégie runtime au type de l’argument passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="f8540-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="f8540-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="f8540-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="f8540-140">Applique la stratégie runtime à une propriété.</span><span class="sxs-lookup"><span data-stu-id="f8540-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="f8540-141">Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8540-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="f8540-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="f8540-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="f8540-143">Applique la stratégie runtime à toutes les classes héritées du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="f8540-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="f8540-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="f8540-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="f8540-145">Applique la stratégie runtime à un type.</span><span class="sxs-lookup"><span data-stu-id="f8540-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="f8540-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="f8540-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="f8540-147">Applique la stratégie runtime à un type générique construit.</span><span class="sxs-lookup"><span data-stu-id="f8540-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="f8540-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="f8540-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="f8540-149">Applique la stratégie runtime au type représenté par un argument <xref:System.Type> passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="f8540-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8540-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8540-150">See also</span></span>

- [<span data-ttu-id="f8540-151">Guide de référence du fichier de configuration rd.xml</span><span class="sxs-lookup"><span data-stu-id="f8540-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
