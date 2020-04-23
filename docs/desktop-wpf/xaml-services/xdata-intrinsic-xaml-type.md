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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071541"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="24938-102">x:XData, type XAML intrinsèque</span><span class="sxs-lookup"><span data-stu-id="24938-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="24938-103">Permet le placement d’îles de données XML dans une production XAML.</span><span class="sxs-lookup"><span data-stu-id="24938-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="24938-104">Les éléments `x:XData` XML à l’intérieur ne doivent pas être traités par les processeurs XAML comme s’ils faisaient partie de l’espace de nom XAML par défaut d’action ou tout autre espace de nom XAML.</span><span class="sxs-lookup"><span data-stu-id="24938-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="24938-105">`x:XData`peut contenir un XML arbitraire bien formé.</span><span class="sxs-lookup"><span data-stu-id="24938-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="24938-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="24938-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="24938-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="24938-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="24938-108">L’élément racine unique de l’île de données fermée.</span><span class="sxs-lookup"><span data-stu-id="24938-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="24938-109">Pour la plupart des consommateurs éventuels, XML qui n’a pas une seule racine est considéré comme invalide.</span><span class="sxs-lookup"><span data-stu-id="24938-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="24938-110">En particulier, une seule racine `x:XData` est nécessaire si l’est destiné comme une source de données XML pour WPF ou de nombreuses autres technologies qui utilisent des sources XML pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="24938-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="24938-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="24938-111">Optional.</span></span> <span data-ttu-id="24938-112">XML qui représente les données XML.</span><span class="sxs-lookup"><span data-stu-id="24938-112">XML that represents the XML data.</span></span> <span data-ttu-id="24938-113">N’importe quel nombre d’éléments peut être contenu comme données d’éléments et les éléments imbriqués peuvent être contenus dans d’autres éléments; cependant, les règles générales de XML s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="24938-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="24938-114">Notes</span><span class="sxs-lookup"><span data-stu-id="24938-114">Remarks</span></span>

<span data-ttu-id="24938-115">Les éléments XML `x:XData` d’un objet peuvent re-déclarer tous les espaces de nom possibles et les préfixes du XMLDOM contenant dans les données.</span><span class="sxs-lookup"><span data-stu-id="24938-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="24938-116">L’accès programmatique aux `x:XData` données XML et au type XAML intrinsèque <xref:System.Windows.Markup.XData> est possible dans .NET XAML Services à travers la classe.</span><span class="sxs-lookup"><span data-stu-id="24938-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="24938-117">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="24938-117">WPF Usage Notes</span></span>

<span data-ttu-id="24938-118">L’objet `x:XData` est principalement utilisé comme <xref:System.Windows.Data.XmlDataProvider>objet enfant d’un , ou <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> alternativement, comme l’objet enfant de la propriété (dans XAML, cela est généralement exprimé dans la syntaxe élément de propriété).</span><span class="sxs-lookup"><span data-stu-id="24938-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="24938-119">Les données doivent généralement redéfinir l’espace de nom XML de base dans l’île de données pour être un nouvel espace de nom XML par défaut (réglé sur une chaîne vide).</span><span class="sxs-lookup"><span data-stu-id="24938-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="24938-120">Ceci est plus facile pour <xref:System.Windows.Data.Binding.XPath%2A> les îles de données simples parce que les expressions qui sont utilisées pour référencer et se lier aux données peuvent éviter l’inclusion de préfixes.</span><span class="sxs-lookup"><span data-stu-id="24938-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="24938-121">Des îles de données plus complexes peuvent définir plusieurs préfixes pour les données et utiliser un préfixe spécifique pour l’espace de nom XML à la racine.</span><span class="sxs-lookup"><span data-stu-id="24938-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="24938-122">Dans ce cas, toutes les <xref:System.Windows.Data.Binding.XPath%2A> références d’expression doivent inclure le préfixe approprié cartographié par l’espace de nom.</span><span class="sxs-lookup"><span data-stu-id="24938-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="24938-123">Pour plus d’informations, voir [Aperçu de la liaison des données](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="24938-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="24938-124">Techniquement, `x:XData` peut être utilisé comme le <xref:System.Xml.Serialization.IXmlSerializable>contenu de toute propriété de type .</span><span class="sxs-lookup"><span data-stu-id="24938-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="24938-125">Cependant, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> est la seule mise en œuvre importante.</span><span class="sxs-lookup"><span data-stu-id="24938-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="24938-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24938-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="24938-127">Aperçu de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="24938-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="24938-128">Binding, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="24938-128">Binding Markup Extension</span></span>](../../framework/wpf/advanced/binding-markup-extension.md)
