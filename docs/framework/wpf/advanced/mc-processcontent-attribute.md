---
title: mc:ProcessContent, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: dde304cc2b9db9cb01f9264ca1359b8979512cfa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458783"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="6c0fd-102">mc:ProcessContent, attribut</span><span class="sxs-lookup"><span data-stu-id="6c0fd-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="6c0fd-103">Spécifie les éléments de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doivent toujours avoir un contenu traité par des éléments parents pertinents, même si l’élément parent immédiat peut être ignoré par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en raison de la spécification de l' [attribut MC : Ignorable](mc-ignorable-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="6c0fd-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="6c0fd-104">L’attribut `mc:ProcessContent` prend en charge la compatibilité du balisage pour le mappage d’espace de noms personnalisé et pour le contrôle de version [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c0fd-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="6c0fd-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="6c0fd-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6c0fd-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="6c0fd-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c0fd-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="6c0fd-107">*ignorablePrefix*</span></span>|<span data-ttu-id="6c0fd-108">Toute chaîne de préfixe valide, conformément à la spécification XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="6c0fd-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="6c0fd-109">*ignorableUri*</span></span>|<span data-ttu-id="6c0fd-110">Tout URI valide pour la désignation d’un espace de noms, conformément à la spécification XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="6c0fd-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="6c0fd-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="6c0fd-112">Élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implémentations du processeur, si le type sous-jacent ne peut pas être résolu.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="6c0fd-113">*humidité*</span><span class="sxs-lookup"><span data-stu-id="6c0fd-113">*[content]*</span></span>|<span data-ttu-id="6c0fd-114">*ThisElementCanBeIgnored* est marqué comme étant ignoré.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="6c0fd-115">Si le processeur ignore cet élément, *[content]* est traité par l' *objet*.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c0fd-116">Notes</span><span class="sxs-lookup"><span data-stu-id="6c0fd-116">Remarks</span></span>  
 <span data-ttu-id="6c0fd-117">Par défaut, un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignore le contenu d’un élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="6c0fd-118">Vous pouvez spécifier un élément spécifique par `mc:ProcessContent`, et un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] continuera à traiter le contenu dans l’élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="6c0fd-119">Cela est généralement utilisé si le contenu est imbriqué dans plusieurs balises, au moins l’une d’entre elles pouvant être Ignorable et au moins l’une d’entre elles ne peut pas être ignorée.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="6c0fd-120">Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un séparateur d’espace, par exemple : `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="6c0fd-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="6c0fd-121">L’espace de noms `http://schemas.openxmlformats.org/markup-compatibility/2006` définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="6c0fd-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="6c0fd-122">Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="6c0fd-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0fd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c0fd-123">See also</span></span>

- [<span data-ttu-id="6c0fd-124">mc:Ignorable, attribut</span><span class="sxs-lookup"><span data-stu-id="6c0fd-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="6c0fd-125">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="6c0fd-125">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
