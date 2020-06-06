---
title: Éléments de directive runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128171"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="7cf11-102">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="7cf11-102">Runtime Directive Elements</span></span>
<span data-ttu-id="7cf11-103">Le format du fichier de directives runtime (rd.xml) prend en charge les éléments de directive runtime suivants.</span><span class="sxs-lookup"><span data-stu-id="7cf11-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="7cf11-104">Pour voir une représentation hiérarchique, consultez [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="7cf11-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="7cf11-105">Applique la stratégie de réflexion runtime à tous les types utilisés par l'application et sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7cf11-105">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="7cf11-106">Il s’agit d’un enfant de l' [\<Directives>](directives-element-net-native.md) élément.</span><span class="sxs-lookup"><span data-stu-id="7cf11-106">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="7cf11-107">Applique la stratégie runtime à tous les types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="7cf11-107">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="7cf11-108">Il s’agit d’un enfant [\<Application>](application-element-net-native.md) des [\<Library>](library-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-108">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="7cf11-109">Si sa [\<Type>](type-element-net-native.md) directive conteneur est un attribut, applique la stratégie Runtime aux éléments de code auxquels cet attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="7cf11-109">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="7cf11-110">Élément racine dans chaque fichier de directives Runtime pour .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7cf11-110">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="7cf11-111">Ses éléments enfants sont [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="7cf11-111">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="7cf11-112">Applique la stratégie runtime à un événement.</span><span class="sxs-lookup"><span data-stu-id="7cf11-112">Applies runtime policy to an event.</span></span> <span data-ttu-id="7cf11-113">Il s’agit d’un enfant [\<Type>](type-element-net-native.md) des [\<TypeInstantiation>](typeinstantiation-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-113">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="7cf11-114">Applique la stratégie runtime à un champ.</span><span class="sxs-lookup"><span data-stu-id="7cf11-114">Applies runtime policy to a field.</span></span> <span data-ttu-id="7cf11-115">Il s’agit d’un enfant [\<Type>](type-element-net-native.md) des [\<TypeInstantiation>](typeinstantiation-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-115">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="7cf11-116">Applique la stratégie runtime au type de paramètre d'un type ou d'une méthode générique.</span><span class="sxs-lookup"><span data-stu-id="7cf11-116">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="7cf11-117">Applique la stratégie runtime à un type, si cette stratégie a été appliquée à la méthode ou au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="7cf11-117">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="7cf11-118">Applique la stratégie runtime à tous les types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="7cf11-118">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="7cf11-119">Il s’agit d’un enfant [\<Application>](application-element-net-native.md) des [\<Library>](library-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-119">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="7cf11-120">Applique la stratégie runtime à une méthode.</span><span class="sxs-lookup"><span data-stu-id="7cf11-120">Applies runtime policy to a method.</span></span> <span data-ttu-id="7cf11-121">Il s’agit d’un enfant [\<Type>](type-element-net-native.md) des [\<TypeInstantiation>](typeinstantiation-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="7cf11-122">Applique la stratégie runtime à une méthode générique construite.</span><span class="sxs-lookup"><span data-stu-id="7cf11-122">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="7cf11-123">Il s’agit d’un enfant [\<Type>](type-element-net-native.md) des [\<TypeInstantiation>](typeinstantiation-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-123">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="7cf11-124">Applique la stratégie runtime à tous les types d'un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7cf11-124">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="7cf11-125">Applique la stratégie runtime au type de l’argument passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="7cf11-125">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="7cf11-126">Applique la stratégie runtime à une propriété.</span><span class="sxs-lookup"><span data-stu-id="7cf11-126">Applies runtime policy to a property.</span></span> <span data-ttu-id="7cf11-127">Il s’agit d’un enfant [\<Type>](type-element-net-native.md) des [\<TypeInstantiation>](typeinstantiation-element-net-native.md) éléments et.</span><span class="sxs-lookup"><span data-stu-id="7cf11-127">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="7cf11-128">Applique la stratégie runtime à toutes les classes héritées du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="7cf11-128">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="7cf11-129">Applique la stratégie runtime à un type.</span><span class="sxs-lookup"><span data-stu-id="7cf11-129">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="7cf11-130">Applique la stratégie runtime à un type générique construit.</span><span class="sxs-lookup"><span data-stu-id="7cf11-130">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="7cf11-131">Applique la stratégie runtime au type représenté par un argument <xref:System.Type> passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="7cf11-131">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf11-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cf11-132">See also</span></span>

- [<span data-ttu-id="7cf11-133">Guide de référence du fichier de configuration rd.xml</span><span class="sxs-lookup"><span data-stu-id="7cf11-133">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
