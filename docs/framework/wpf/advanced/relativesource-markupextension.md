---
title: RelativeSource, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 47117d684a981f31e22cf513fc78e1e2dda73f8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141269"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="f137d-102">RelativeSource, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="f137d-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="f137d-103">Spécifie les propriétés <xref:System.Windows.Data.RelativeSource> d’une source de liaison à utiliser dans une [extension de balisage de liaison](binding-markup-extension.md), <xref:System.Windows.Data.Binding.RelativeSource%2A> ou lors de <xref:System.Windows.Data.Binding> la définition de la propriété d’un élément établi en XAML.</span><span class="sxs-lookup"><span data-stu-id="f137d-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="f137d-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="f137d-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="f137d-105">Utilisation des attributs XAML (imbriqués dans l'extension de liaison)</span><span class="sxs-lookup"><span data-stu-id="f137d-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="f137d-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="f137d-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="f137d-107">-ou-</span><span class="sxs-lookup"><span data-stu-id="f137d-107">-or-</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a><span data-ttu-id="f137d-108">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="f137d-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="f137d-109">Celui-ci peut avoir l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f137d-109">One of the following:</span></span><br /><br /> <span data-ttu-id="f137d-110">-Le jeton `Self`de chaîne ; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété définie sur <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="f137d-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="f137d-111">-Le jeton `TemplatedParent`de chaîne ; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété définie sur <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="f137d-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="f137d-112">-Le jeton `PreviousData`de chaîne ; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété définie sur <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="f137d-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="f137d-113">-Voir ci-dessous pour `FindAncestor` plus d’informations sur le mode.</span><span class="sxs-lookup"><span data-stu-id="f137d-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="f137d-114">Le jeton de chaîne `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f137d-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="f137d-115">L'utilisation de ce jeton accède à un mode dans lequel un `RelativeSource` spécifie un type d'ancêtre et, en option, un niveau d'ancêtre.</span><span class="sxs-lookup"><span data-stu-id="f137d-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="f137d-116">Ce correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="f137d-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="f137d-117">Nécessaire pour le mode `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f137d-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="f137d-118">Le nom d'un type, qui remplit la propriété <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f137d-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="f137d-119">Facultatif pour le mode `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f137d-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="f137d-120">Un niveau d'ancêtre (évalué vers la direction du parent dans l'arborescence logique).</span><span class="sxs-lookup"><span data-stu-id="f137d-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="f137d-121">Notes</span><span class="sxs-lookup"><span data-stu-id="f137d-121">Remarks</span></span>

<span data-ttu-id="f137d-122">`{RelativeSource TemplatedParent}`les utilisations de liaison sont une technique clé qui résout un plus grand concept de séparation de l’interface utilisateur d’un contrôle et d’une logique de contrôle.</span><span class="sxs-lookup"><span data-stu-id="f137d-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="f137d-123">Cela permet la liaison à partir de la définition de modèle au parent basé sur des modèles (instance de l'objet à l'exécution où le modèle est appliqué).</span><span class="sxs-lookup"><span data-stu-id="f137d-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="f137d-124">Dans ce cas, l' [extension de balisage TemplateBinding](templatebinding-markup-extension.md) est en fait un raccourci pour l’expression de `{Binding RelativeSource={RelativeSource TemplatedParent}}`liaison suivante :.</span><span class="sxs-lookup"><span data-stu-id="f137d-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="f137d-125">`TemplateBinding`les `{RelativeSource TemplatedParent}` utilisations ou sont toutes deux uniquement pertinentes dans le code XAML qui définit un modèle.</span><span class="sxs-lookup"><span data-stu-id="f137d-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="f137d-126">Pour plus d’informations, consultez l' [extension de balisage TemplateBinding](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="f137d-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="f137d-127">`{RelativeSource FindAncestor}`est principalement utilisé dans les modèles de contrôle ou les compositions d’interface utilisateur autonomes prévisibles, pour les cas où un contrôle est toujours supposé être dans une arborescence d’éléments visuels d’un certain type d’ancêtre.</span><span class="sxs-lookup"><span data-stu-id="f137d-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="f137d-128">Par exemple, les éléments d'un contrôle d'éléments peuvent utiliser des utilisations de `FindAncestor` pour les lier aux propriétés de leur ancêtre parent du contrôle d'éléments.</span><span class="sxs-lookup"><span data-stu-id="f137d-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="f137d-129">Ou les éléments qui font partie de la composition de contrôle dans un modèle peuvent utiliser des liaisons de `FindAncestor` aux éléments parents dans cette même structure de composition.</span><span class="sxs-lookup"><span data-stu-id="f137d-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="f137d-130">Dans la syntaxe d'élément objet du mode `FindAncestor` indiqué dans les sections de syntaxe XAML, la deuxième syntaxe d'élément objet est utilisée spécifiquement pour le mode `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f137d-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="f137d-131">Le mode `FindAncestor` requiert une valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f137d-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="f137d-132">Vous devez définir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> en tant qu’attribut à l’aide d’une référence d' [extension de balisage x :type](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) au type d’ancêtre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="f137d-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="f137d-133">La valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A> est utilisée lorsque la demande de liaison est traitée lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f137d-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="f137d-134">Pour le mode `FindAncestor`, la propriété <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> facultative peut contribuer à désambiguïser la recherche d'ancêtre dans les cas où il existe peut-être plusieurs ancêtres de ce type présents dans l'arborescence d'éléments.</span><span class="sxs-lookup"><span data-stu-id="f137d-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="f137d-135">Pour plus d'informations sur l'utilisation du mode `FindAncestor`, consultez <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="f137d-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="f137d-136">`{RelativeSource Self}`est utile pour les scénarios où une propriété d’une instance doit dépendre de la valeur d’une autre propriété de la même instance, et qu’aucune relation de propriété de dépendance générale (telle que la contrainte) n’existe déjà entre ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="f137d-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="f137d-137">Bien qu’il soit rare que deux propriétés existent sur un objet de telle sorte que les valeurs soient littéralement identiques (et sont de type identique), vous pouvez `Converter` également appliquer un paramètre à une `{RelativeSource Self}`liaison qui a, et utiliser le convertisseur pour effectuer une conversion entre des types source et cible.</span><span class="sxs-lookup"><span data-stu-id="f137d-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="f137d-138">Un autre scénario `{RelativeSource Self}` pour est dans le cadre <xref:System.Windows.MultiDataTrigger>d’un.</span><span class="sxs-lookup"><span data-stu-id="f137d-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="f137d-139">Par exemple, le code XAML suivant définit un élément <xref:System.Windows.Shapes.Rectangle> tels que tout ce que la valeur est entrée pour <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> est toujours angle droit : `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="f137d-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="f137d-140">`{RelativeSource PreviousData}`est utile dans les modèles de données ou dans les cas où des liaisons utilisent une collection comme source de données.</span><span class="sxs-lookup"><span data-stu-id="f137d-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="f137d-141">Vous pouvez utiliser `{RelativeSource PreviousData}` pour mettre en surbrillance les relations entre des éléments de données adjacents dans la collection.</span><span class="sxs-lookup"><span data-stu-id="f137d-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="f137d-142">Une technique connexe est de générer <xref:System.Windows.Data.MultiBinding> entre des éléments actuels et précédents dans la source de données, et d'utiliser un convertisseur sur cette liaison pour déterminer la différence entre les deux éléments et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="f137d-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="f137d-143">Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> dans le modèle d'éléments affiche le numéro actuel.</span><span class="sxs-lookup"><span data-stu-id="f137d-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="f137d-144">La deuxième <xref:System.Windows.Controls.TextBlock> liaison est un <xref:System.Windows.Data.MultiBinding> qui a nominalement deux <xref:System.Windows.Data.Binding> constituants : l’enregistrement actif et une liaison qui utilise délibérément l’enregistrement de données précédent `{RelativeSource PreviousData}`à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="f137d-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="f137d-145">Ensuite, un convertisseur sur <xref:System.Windows.Data.MultiBinding> calcule la différence et la retourne à la liaison.</span><span class="sxs-lookup"><span data-stu-id="f137d-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox>
```

<span data-ttu-id="f137d-146">La description de la liaison de données comme concept n’est pas abordée ici, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="f137d-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="f137d-147">Dans l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation du processeur XAML, la gestion de cette extension de balisage est <xref:System.Windows.Data.RelativeSource> définie par la classe.</span><span class="sxs-lookup"><span data-stu-id="f137d-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="f137d-148">`RelativeSource` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="f137d-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="f137d-149">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="f137d-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f137d-150">Toutes les extensions de balisage en `{` XAML `}` utilisent les caractères et dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="f137d-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f137d-151">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f137d-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f137d-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f137d-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="f137d-153">Application d'un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="f137d-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f137d-154">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f137d-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="f137d-155">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="f137d-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f137d-156">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="f137d-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f137d-157">Vue d’ensemble des déclarations de liaison</span><span class="sxs-lookup"><span data-stu-id="f137d-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="f137d-158">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="f137d-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
