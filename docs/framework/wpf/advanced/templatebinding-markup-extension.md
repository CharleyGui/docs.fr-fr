---
title: TemplateBinding, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 8cebbf717f66b072bc84b2068193ff2fe76ea87b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187281"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="4bab6-102">TemplateBinding, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="4bab6-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="4bab6-103">Cette extension lie la valeur d'une propriété dans un modèle de contrôle afin de la définir comme valeur d'une autre propriété exposée dans le contrôle basé sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="4bab6-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4bab6-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="4bab6-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="4bab6-105">Utilisation d'attributs XAML (pour la propriété de méthode setter dans le modèle ou le style)</span><span class="sxs-lookup"><span data-stu-id="4bab6-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4bab6-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="4bab6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="4bab6-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> de la propriété définie dans la syntaxe de méthode setter.</span><span class="sxs-lookup"><span data-stu-id="4bab6-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="4bab6-108">Autre propriété de dépendance qui existe sur le type basé sur un modèle, spécifiée par <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4bab6-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="4bab6-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="4bab6-109">- or -</span></span><br /><br /> <span data-ttu-id="4bab6-110">Nom de propriété « dotted-down » défini par un autre type que le type de cible basé sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="4bab6-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="4bab6-111">Il s'agit en réalité d'un <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="4bab6-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="4bab6-112">Voir [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="4bab6-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bab6-113">Notes </span><span class="sxs-lookup"><span data-stu-id="4bab6-113">Remarks</span></span>  
 <span data-ttu-id="4bab6-114">A `TemplateBinding` est une forme optimisée d’une [liaison](binding-markup-extension.md) pour `Binding` les `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`scénarios de modèle, analogue à un construit avec .</span><span class="sxs-lookup"><span data-stu-id="4bab6-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`.</span></span> <span data-ttu-id="4bab6-115">`TemplateBinding` est toujours une liaison unidirectionnelle, même si les propriétés ont comme valeur par défaut des liaisons bidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="4bab6-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="4bab6-116">Les deux propriétés doivent toutes être des propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="4bab6-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="4bab6-117">Afin d’atteindre la liaison bidirectionnel à un `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`parent modélné utiliser l’instruction contraignante suivante à la place .</span><span class="sxs-lookup"><span data-stu-id="4bab6-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span>
  
 <span data-ttu-id="4bab6-118">[RelativeSource](relativesource-markupextension.md) est une autre extension de balisage `TemplateBinding` qui est parfois utilisée en conjonction avec ou au lieu de afin d’effectuer la liaison relative de propriété dans un modèle.</span><span class="sxs-lookup"><span data-stu-id="4bab6-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="4bab6-119">Décrire les modèles de contrôle comme un concept n’est pas couvert ici; pour plus d’informations, voir [Styles de contrôle et Modèles](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4bab6-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="4bab6-120">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="4bab6-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="4bab6-121">Le jeton de chaîne fourni après la chaîne d’identificateur `TemplateBinding` est assigné en tant que valeur <xref:System.Windows.TemplateBindingExtension.Property%2A> de la classe d’extension <xref:System.Windows.TemplateBindingExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="4bab6-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="4bab6-122">La syntaxe d'élément objet est possible, mais elle n'est pas indiquée car elle ne possède aucune application réaliste.</span><span class="sxs-lookup"><span data-stu-id="4bab6-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="4bab6-123">`TemplateBinding` est utilisé pour remplir des valeurs dans des méthodes setter, à l'aide d'expressions évaluées. En outre, l'utilisation de la syntaxe d'élément objet de `TemplateBinding` pour remplir la syntaxe des éléments de propriété `<Setter.Property>` est inutilement détaillée.</span><span class="sxs-lookup"><span data-stu-id="4bab6-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="4bab6-124">`TemplateBinding` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.TemplateBindingExtension.Property%2A> en tant que paire propriété=valeur :</span><span class="sxs-lookup"><span data-stu-id="4bab6-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="4bab6-125">L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="4bab6-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="4bab6-126">`TemplateBinding` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.</span><span class="sxs-lookup"><span data-stu-id="4bab6-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="4bab6-127">Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la mise en œuvre du processeur XAML, la manipulation de cette extension de balisage est définie par la <xref:System.Windows.TemplateBindingExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="4bab6-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="4bab6-128">`TemplateBinding` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="4bab6-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="4bab6-129">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="4bab6-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="4bab6-130">Toutes les extensions de balisage dans XAML utilisent le `{` syntaxe d’attribut, `}` qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="4bab6-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="4bab6-131">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4bab6-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bab6-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bab6-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="4bab6-133">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="4bab6-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="4bab6-134">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="4bab6-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="4bab6-135">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="4bab6-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="4bab6-136">RelativeSource, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="4bab6-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="4bab6-137">Binding, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="4bab6-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
