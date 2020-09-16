---
title: x:Array, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555170"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="74b70-102">x:Array, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="74b70-102">x:Array Markup Extension</span></span>

<span data-ttu-id="74b70-103">Fournit la prise en charge générale des tableaux d’objets en XAML par le biais d’une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="74b70-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="74b70-104">Cela correspond au `x:ArrayExtension` type XAML dans [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="74b70-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="74b70-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="74b70-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="74b70-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="74b70-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="74b70-107">Nom du type que votre `x:Array` contiendra.</span><span class="sxs-lookup"><span data-stu-id="74b70-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="74b70-108">`typeName` peut être (et est souvent) préfixé pour un espace de noms XAML qui contient les définitions de type XAML.</span><span class="sxs-lookup"><span data-stu-id="74b70-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="74b70-109">Contenu des éléments qui est assigné à la `ArrayExtension.Items` propriété intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="74b70-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="74b70-110">En règle générale, ces éléments sont spécifiés sous la forme d’un ou plusieurs éléments objet contenus dans les `x:Array` balises d’ouverture et de fermeture.</span><span class="sxs-lookup"><span data-stu-id="74b70-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="74b70-111">Les objets spécifiés ici sont censés être assignés au type XAML spécifié dans `typeName` .</span><span class="sxs-lookup"><span data-stu-id="74b70-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74b70-112">Notes</span><span class="sxs-lookup"><span data-stu-id="74b70-112">Remarks</span></span>

<span data-ttu-id="74b70-113">`Type` est un attribut requis pour tous les `x:Array` éléments objet.</span><span class="sxs-lookup"><span data-stu-id="74b70-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="74b70-114">Une `Type` valeur de paramètre n’a pas besoin d’utiliser une `x:Type` extension de balisage ; le nom abrégé du type est un type XAML, qui peut être spécifié sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="74b70-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="74b70-115">Dans l’implémentation des services XAML .NET, la relation entre le type XAML d’entrée et le CLR <xref:System.Type> de sortie du tableau créé est influencée par le contexte de service pour les extensions de balisage.</span><span class="sxs-lookup"><span data-stu-id="74b70-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="74b70-116">La sortie <xref:System.Type> est le <xref:System.Xaml.XamlType.UnderlyingType%2A> du type XAML d’entrée, après avoir cherché le nécessaire <xref:System.Xaml.XamlType> en fonction du contexte de schéma XAML et du <xref:System.Windows.Markup.IXamlTypeResolver> service fourni par le contexte.</span><span class="sxs-lookup"><span data-stu-id="74b70-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="74b70-117">Lorsqu’il est traité, le contenu du tableau est affecté à la `ArrayExtension.Items` propriété intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="74b70-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="74b70-118">Dans l' <xref:System.Windows.Markup.ArrayExtension> implémentation, il est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74b70-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="74b70-119">Dans l’implémentation des services XAML .NET, la gestion de cette extension de balisage est définie par la <xref:System.Windows.Markup.ArrayExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="74b70-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="74b70-120"><xref:System.Windows.Markup.ArrayExtension> n’est pas sealed et peut être utilisé comme base pour une implémentation d’extension de balisage pour un type de tableau personnalisé.</span><span class="sxs-lookup"><span data-stu-id="74b70-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="74b70-121">`x:Array` est plus destiné à l’extensibilité de langage générale en XAML.</span><span class="sxs-lookup"><span data-stu-id="74b70-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="74b70-122">Mais `x:Array` peut également être utile pour spécifier des valeurs XAML de certaines propriétés qui prennent des collections prises en charge en XAML comme contenu de propriété structurée.</span><span class="sxs-lookup"><span data-stu-id="74b70-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="74b70-123">Par exemple, vous pouvez spécifier le contenu d’une <xref:System.Collections.IEnumerable> propriété avec une `x:Array` utilisation.</span><span class="sxs-lookup"><span data-stu-id="74b70-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="74b70-124">`x:Array` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="74b70-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="74b70-125">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="74b70-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="74b70-126">`x:Array` est partiellement une exception à cette règle, car au lieu de fournir une autre gestion des valeurs d’attribut, `x:Array` fournit une autre gestion de son contenu de texte interne.</span><span class="sxs-lookup"><span data-stu-id="74b70-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="74b70-127">Ce comportement permet aux types qui ne sont pas pris en charge par un modèle de contenu existant d’être regroupés dans un tableau et référencés ultérieurement dans le code-behind en accédant au tableau nommé ; vous pouvez appeler <xref:System.Array> des méthodes pour récupérer des éléments de tableau individuels.</span><span class="sxs-lookup"><span data-stu-id="74b70-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="74b70-128">Toutes les extensions de balisage en XAML utilisent les accolades ( {,} `)` dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter la valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="74b70-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="74b70-129">Pour plus d’informations sur les extensions de balisage en général, consultez [convertisseurs de type et extensions de balisage pour XAML](type-converters-and-markup-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="74b70-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="74b70-130">En XAML 2009, `x:Array` est défini comme une primitive de langage au lieu d’une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="74b70-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="74b70-131">Pour plus d’informations, consultez [types intégrés pour les primitives de langage XAML courantes](types-for-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="74b70-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="74b70-132">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="74b70-132">WPF Usage Notes</span></span>

<span data-ttu-id="74b70-133">En général, les éléments objets qui remplissent un `x:Array` ne sont pas des éléments qui existent dans l' [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] espace de noms XAML et requièrent un mappage de préfixe à un espace de noms XAML non défini par défaut.</span><span class="sxs-lookup"><span data-stu-id="74b70-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="74b70-134">Par exemple, le code suivant est un tableau simple de deux chaînes, avec le `sys` préfixe (et également `x` ) défini au niveau du tableau.</span><span class="sxs-lookup"><span data-stu-id="74b70-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="74b70-135">Pour les types personnalisés utilisés comme éléments de tableau, la classe doit également prendre en charge les spécifications pour être instanciées en XAML en tant qu’éléments objet.</span><span class="sxs-lookup"><span data-stu-id="74b70-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="74b70-136">Pour plus d’informations, consultez [XAML et classes personnalisées pour WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span><span class="sxs-lookup"><span data-stu-id="74b70-136">For more information, see [XAML and Custom Classes for WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span></span>

## <a name="see-also"></a><span data-ttu-id="74b70-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74b70-137">See also</span></span>

- [<span data-ttu-id="74b70-138">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="74b70-138">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [<span data-ttu-id="74b70-139">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="74b70-139">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
