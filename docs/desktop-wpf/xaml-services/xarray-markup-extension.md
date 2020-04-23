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
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072045"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="3f827-102">x:Array, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="3f827-102">x:Array Markup Extension</span></span>

<span data-ttu-id="3f827-103">Fournit un support général pour les tableaux d’objets dans XAML grâce à une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="3f827-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="3f827-104">Cela correspond au `x:ArrayExtension` type XAML dans [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="3f827-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="3f827-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="3f827-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="3f827-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="3f827-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="3f827-107">Le nom du type `x:Array` que vous contiendra.</span><span class="sxs-lookup"><span data-stu-id="3f827-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="3f827-108">`typeName`peut être (et est souvent) préfixé pour un espace de nom XAML qui contient les définitions de type XAML.</span><span class="sxs-lookup"><span data-stu-id="3f827-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="3f827-109">Le contenu des éléments qui `ArrayExtension.Items` est attribué à la propriété intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="3f827-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="3f827-110">En règle générale, ces éléments sont spécifiés `x:Array` comme un ou plusieurs éléments d’objet contenus dans les balises d’ouverture et de fermeture.</span><span class="sxs-lookup"><span data-stu-id="3f827-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="3f827-111">Les objets spécifiés ici devraient être attribués au `typeName`type XAML spécifié dans .</span><span class="sxs-lookup"><span data-stu-id="3f827-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f827-112">Notes</span><span class="sxs-lookup"><span data-stu-id="3f827-112">Remarks</span></span>

<span data-ttu-id="3f827-113">`Type`est un attribut `x:Array` requis pour tous les éléments d’objets.</span><span class="sxs-lookup"><span data-stu-id="3f827-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="3f827-114">Une `Type` valeur de paramètre `x:Type` n’a pas besoin d’utiliser une extension de balisage; le nom court du type est un type XAML, qui peut être spécifié comme une chaîne.</span><span class="sxs-lookup"><span data-stu-id="3f827-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="3f827-115">Dans la mise en œuvre de .NET XAML Services, <xref:System.Type> la relation entre le type XAML d’entrée et le CLR de sortie du tableau créé est influencée par le contexte de service pour les extensions de balisage.</span><span class="sxs-lookup"><span data-stu-id="3f827-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="3f827-116">La <xref:System.Type> sortie <xref:System.Xaml.XamlType.UnderlyingType%2A> est le type XAML d’entrée, après avoir examiné le <xref:System.Xaml.XamlType> <xref:System.Windows.Markup.IXamlTypeResolver> nécessaire en fonction du contexte schéma XAML et du service fourni par le contexte.</span><span class="sxs-lookup"><span data-stu-id="3f827-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="3f827-117">Lorsqu’il est traité, le `ArrayExtension.Items` contenu du tableau est attribué à la propriété intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="3f827-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="3f827-118">Dans <xref:System.Windows.Markup.ArrayExtension> la mise en œuvre, cela est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f827-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3f827-119">Dans la mise en œuvre de .NET XAML <xref:System.Windows.Markup.ArrayExtension> Services, le traitement de cette extension de balisage est défini par la classe.</span><span class="sxs-lookup"><span data-stu-id="3f827-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="3f827-120"><xref:System.Windows.Markup.ArrayExtension>n’est pas scellé et pourrait servir de base à une mise en œuvre d’extension de balisage pour un type de tableau personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3f827-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="3f827-121">`x:Array`est plus destiné à l’extéabilité générale de la langue dans XAML.</span><span class="sxs-lookup"><span data-stu-id="3f827-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="3f827-122">Mais `x:Array` peut également être utile pour spécifier les valeurs XAML de certaines propriétés qui prennent XAML-soutenu collections comme leur contenu de propriété structurée.</span><span class="sxs-lookup"><span data-stu-id="3f827-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="3f827-123">Par exemple, vous pouvez spécifier le contenu d’une <xref:System.Collections.IEnumerable> propriété avec une `x:Array` utilisation.</span><span class="sxs-lookup"><span data-stu-id="3f827-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="3f827-124">`x:Array` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="3f827-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="3f827-125">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="3f827-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3f827-126">`x:Array`est en partie une exception à cette règle `x:Array` parce qu’au lieu de fournir une manipulation alternative de la valeur d’attribut, fournit la manipulation alternative de son contenu de texte intérieur.</span><span class="sxs-lookup"><span data-stu-id="3f827-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="3f827-127">Ce comportement permet aux types qui pourraient ne pas être pris en charge par un modèle de contenu existant d’être regroupés dans un tableau et référencé plus tard dans le code-derrière en accédant à la grille nommée; vous pouvez <xref:System.Array> appeler des méthodes pour obtenir des éléments de tableau individuels.</span><span class="sxs-lookup"><span data-stu-id="3f827-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="3f827-128">Toutes les extensions de balisage dans{,} `)` XAML utilisent les accolades (dans leur syntaxe d’attribut, qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter la valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="3f827-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="3f827-129">Pour plus d’informations sur les extensions de balisage en général, voir [Les convertisseurs de type et extensions de balisage pour XAML](type-converters-and-markup-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="3f827-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="3f827-130">Dans XAML 2009, `x:Array` est défini comme une langue primitive au lieu d’une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="3f827-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="3f827-131">Pour plus d’informations, voir [Types intégrés pour les Primitifs en langue XAML communs](types-for-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="3f827-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="3f827-132">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="3f827-132">WPF Usage Notes</span></span>

<span data-ttu-id="3f827-133">Typiquement, les éléments d’objet qui peuplent un ne sont pas des `x:Array` éléments qui existent dans l’espace [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] de nom XAML, et nécessitent une cartographie préfixe à un espace de nom XAML non-défaut.</span><span class="sxs-lookup"><span data-stu-id="3f827-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="3f827-134">Par exemple, ce qui suit est un simple `sys` tableau de `x`deux cordes, avec le préfixe (et aussi ) défini au niveau du tableau.</span><span class="sxs-lookup"><span data-stu-id="3f827-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="3f827-135">Pour les types personnalisés qui sont utilisés comme éléments de tableau, la classe doit également prendre en charge les exigences pour être instantanée dans XAML comme éléments d’objet.</span><span class="sxs-lookup"><span data-stu-id="3f827-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="3f827-136">Pour plus d’informations, voir [XAML et Custom Classes pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="3f827-136">For more information, see [XAML and Custom Classes for WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f827-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f827-137">See also</span></span>

- [<span data-ttu-id="3f827-138">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="3f827-138">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="3f827-139">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="3f827-139">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
