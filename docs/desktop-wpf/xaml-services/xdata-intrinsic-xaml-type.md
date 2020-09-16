---
title: x:XData, type XAML intrinsèque
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: d78c2fd63192dc499b119e5b038b92555511a695
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544802"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="7bdb4-102">x:XData, type XAML intrinsèque</span><span class="sxs-lookup"><span data-stu-id="7bdb4-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="7bdb4-103">Active le placement des îlots de données XML dans une production XAML.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="7bdb4-104">Les éléments XML dans `x:XData` ne doivent pas être traités par les processeurs XAML comme s’ils font partie de l’espace de noms XAML par défaut en cours d’action ou de tout autre espace de noms XAML.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="7bdb4-105">`x:XData` peut contenir du code XML bien formé arbitrairement.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="7bdb4-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="7bdb4-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="7bdb4-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="7bdb4-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="7bdb4-108">Élément racine unique de l’îlot de données délimité.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="7bdb4-109">Pour la plupart des consommateurs éventuels, le XML qui n’a pas de racine unique est considéré comme non valide.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="7bdb4-110">En particulier, une racine unique est requise si le `x:XData` est destiné à être une source de données XML pour WPF ou de nombreuses autres technologies qui utilisent des sources XML pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="7bdb4-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-111">Optional.</span></span> <span data-ttu-id="7bdb4-112">XML qui représente les données XML.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-112">XML that represents the XML data.</span></span> <span data-ttu-id="7bdb4-113">Vous pouvez faire figurer un nombre quelconque d’éléments en tant que données d’élément et les éléments imbriqués peuvent être contenus dans d’autres éléments ; Toutefois, les règles générales de XML s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7bdb4-114">Notes</span><span class="sxs-lookup"><span data-stu-id="7bdb4-114">Remarks</span></span>

<span data-ttu-id="7bdb4-115">Les éléments XML dans un `x:XData` objet peuvent redéclarer tous les espaces de noms et préfixes possibles de l’objet XMLDOM contenant les données.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="7bdb4-116">L’accès par programme aux données XML et au `x:XData` type XAML intrinsèque est possible dans les services XAML .NET par le biais de la <xref:System.Windows.Markup.XData> classe.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="7bdb4-117">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="7bdb4-117">WPF Usage Notes</span></span>

<span data-ttu-id="7bdb4-118">L' `x:XData` objet est principalement utilisé comme un objet enfant d’un objet <xref:System.Windows.Data.XmlDataProvider> , ou, en tant qu’objet enfant de la <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriété (en XAML, il est généralement exprimé dans la syntaxe d’élément de propriété).</span><span class="sxs-lookup"><span data-stu-id="7bdb4-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="7bdb4-119">Les données doivent généralement redéfinir l’espace de noms XML de base dans l’îlot de données pour qu’il s’agit d’un nouvel espace de noms XML par défaut (défini sur une chaîne vide).</span><span class="sxs-lookup"><span data-stu-id="7bdb4-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="7bdb4-120">Cela est plus facile pour les îlots de données simples, car les <xref:System.Windows.Data.Binding.XPath%2A> expressions utilisées pour référencer les données et les lier aux données peuvent éviter l’inclusion de préfixes.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="7bdb4-121">Des îlots de données plus complexes peuvent définir plusieurs préfixes pour les données et utiliser un préfixe spécifique pour l’espace de noms XML à la racine.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="7bdb4-122">Dans ce cas, toutes les <xref:System.Windows.Data.Binding.XPath%2A> références d’expression doivent inclure le préfixe mappé à l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="7bdb4-123">Pour plus d’informations, consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="7bdb4-124">Techniquement, `x:XData` peut être utilisé comme contenu de n’importe quelle propriété de type <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="7bdb4-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="7bdb4-125">Toutefois, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> est la seule implémentation évidente.</span><span class="sxs-lookup"><span data-stu-id="7bdb4-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bdb4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bdb4-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="7bdb4-127">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="7bdb4-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="7bdb4-128">Liaison avec l’extension de balisage</span><span class="sxs-lookup"><span data-stu-id="7bdb4-128">Binding Markup Extension</span></span>](/dotnet/desktop/wpf/advanced/binding-markup-extension)
