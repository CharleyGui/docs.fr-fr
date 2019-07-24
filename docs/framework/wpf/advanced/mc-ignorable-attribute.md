---
title: mc:Ignorable, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: 40c1a8513608728a84b6b605f9ad18603123ea2e
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401533"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="89796-102">mc:Ignorable, attribut</span><span class="sxs-lookup"><span data-stu-id="89796-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="89796-103">Spécifie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les préfixes d’espaces de noms rencontrés dans un fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage qui peuvent être ignorés par un processeur.</span><span class="sxs-lookup"><span data-stu-id="89796-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="89796-104">L' `mc:Ignorable` attribut prend en charge la compatibilité du balisage pour le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mappage d’espace de noms personnalisé et pour le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="89796-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="89796-105">Utilisation des attributs XAML (préfixe unique)</span><span class="sxs-lookup"><span data-stu-id="89796-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="89796-106">Utilisation des attributs XAML (deux préfixes)</span><span class="sxs-lookup"><span data-stu-id="89796-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="89796-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="89796-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89796-108">*ignorablePrefix, ignorablePrefix1, etc.*</span><span class="sxs-lookup"><span data-stu-id="89796-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="89796-109">Toute chaîne de préfixe valide, conformément à la spécification XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="89796-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="89796-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="89796-110">*ignorableUri*</span></span>|<span data-ttu-id="89796-111">Tout URI valide pour la désignation d’un espace de noms, conformément à la spécification XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="89796-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="89796-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="89796-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="89796-113">Élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] les implémentations de processeur, si le type sous-jacent ne peut pas être résolu.</span><span class="sxs-lookup"><span data-stu-id="89796-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89796-114">Notes</span><span class="sxs-lookup"><span data-stu-id="89796-114">Remarks</span></span>  
 <span data-ttu-id="89796-115">Le `mc` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]préfixe d’espace de noms est la Convention de préfixe recommandée à utiliser lors du mappage de l’espace de noms de compatibilité. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89796-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="89796-116">Les éléments ou les attributs où la partie préfixe du nom d’élément `mc:Ignorable` est identifiée comme ne déclenchent pas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’erreurs lorsqu’elles sont traitées par un processeur.</span><span class="sxs-lookup"><span data-stu-id="89796-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="89796-117">Si cet attribut n’a pas pu être résolu en un type sous-jacent ou une construction de programmation, cet élément est ignoré.</span><span class="sxs-lookup"><span data-stu-id="89796-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="89796-118">Notez cependant que les éléments ignorés peuvent toujours générer des erreurs d’analyse supplémentaires pour des spécifications d’éléments supplémentaires qui sont des effets secondaires de cet élément qui ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="89796-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="89796-119">Par exemple, un modèle de contenu d’élément particulier peut nécessiter exactement un élément enfant, mais si l’élément enfant spécifié `mc:Ignorable` se trouvait dans un préfixe et que l’élément enfant spécifié n’a pas pu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] être résolu en un type, le processeur peut génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="89796-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="89796-120">`mc:Ignorable`s’applique uniquement aux mappages d’espaces de noms aux chaînes d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="89796-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="89796-121">`mc:Ignorable`ne s’applique pas aux mappages d’espaces de noms dans les assemblys, qui spécifient un espace de noms CLR et un assembly (ou l’exécutable actuel comme assembly).</span><span class="sxs-lookup"><span data-stu-id="89796-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="89796-122">Si vous implémentez un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur, votre implémentation de processeur ne doit pas déclencher d’erreurs d’analyse ou de traitement sur la résolution de type pour tout élément ou attribut qualifié par un préfixe identifié comme. `mc:Ignorable`</span><span class="sxs-lookup"><span data-stu-id="89796-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="89796-123">Toutefois, votre implémentation de processeur peut toujours lever des exceptions qui sont un résultat secondaire d’un élément qui n’a pas pu être chargé ou traité, tel que l’exemple d’élément enfant donné précédemment.</span><span class="sxs-lookup"><span data-stu-id="89796-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="89796-124">Par défaut, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ignore le contenu d’un élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="89796-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="89796-125">Toutefois, vous pouvez spécifier un attribut supplémentaire, [MC: ProcessContent](mc-processcontent-attribute.md), pour exiger le traitement continu du contenu dans un élément ignoré par l’élément parent disponible suivant.</span><span class="sxs-lookup"><span data-stu-id="89796-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="89796-126">Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un ou de plusieurs espaces blancs comme séparateur, `mc:Ignorable="ignore1 ignore2"`par exemple:.</span><span class="sxs-lookup"><span data-stu-id="89796-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="89796-127">L' [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] espace[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]de noms définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone du.</span><span class="sxs-lookup"><span data-stu-id="89796-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="89796-128">Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="89796-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89796-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89796-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="89796-130">PresentationOptions:Freeze, attribut</span><span class="sxs-lookup"><span data-stu-id="89796-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="89796-131">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="89796-131">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="89796-132">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="89796-132">Documents in WPF</span></span>](documents-in-wpf.md)
