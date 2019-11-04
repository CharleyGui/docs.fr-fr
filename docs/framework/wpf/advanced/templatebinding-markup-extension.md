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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458671"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding, extension de balisage
Cette extension lie la valeur d'une propriété dans un modèle de contrôle afin de la définir comme valeur d'une autre propriété exposée dans le contrôle basé sur un modèle.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>Utilisation d'attributs XAML (pour la propriété de méthode setter dans le modèle ou le style)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> de la propriété définie dans la syntaxe de méthode setter.|  
|`sourceProperty`|Autre propriété de dépendance qui existe sur le type basé sur un modèle, spécifiée par <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> ou<br /><br /> Nom de propriété « dotted-down » défini par un autre type que le type de cible basé sur un modèle. Il s'agit en réalité d'un <xref:System.Windows.PropertyPath>. Consultez [syntaxe XAML PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Notes  
 Une `TemplateBinding` est une forme optimisée d’une [liaison](binding-markup-extension.md) pour les scénarios de modèle, analogue à une `Binding` construite avec `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` est toujours une liaison unidirectionnelle, même si les propriétés ont comme valeur par défaut des liaisons bidirectionnelles. Les deux propriétés doivent toutes être des propriétés de dépendance. Pour obtenir une liaison bidirectionnelle à un parent basé sur un modèle, utilisez l’instruction de liaison suivante à la place `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](relativesource-markupextension.md) est une autre extension de balisage qui est parfois utilisée conjointement avec ou au lieu de `TemplateBinding` pour effectuer une liaison de propriété relative dans un modèle.  
  
 La description des modèles de contrôle en tant que concept n’est pas abordée ici. Pour plus d’informations, consultez [styles et modèles de contrôle](../controls/control-styles-and-templates.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `TemplateBinding` est assigné en tant que valeur <xref:System.Windows.TemplateBindingExtension.Property%2A> de la classe d’extension <xref:System.Windows.TemplateBindingExtension> sous-jacente.  
  
 La syntaxe d'élément objet est possible, mais elle n'est pas indiquée car elle ne possède aucune application réaliste. `TemplateBinding` est utilisé pour remplir des valeurs dans des méthodes setter, à l'aide d'expressions évaluées. En outre, l'utilisation de la syntaxe d'élément objet de `TemplateBinding` pour remplir la syntaxe des éléments de propriété `<Setter.Property>` est inutilement détaillée.  
  
 `TemplateBinding` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.TemplateBindingExtension.Property%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `TemplateBinding` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans l’implémentation du processeur XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.TemplateBindingExtension>.  
  
 `TemplateBinding` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage en XAML utilisent les caractères `{` et `}` dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Application d’un style et création de modèles](../controls/styling-and-templating.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [RelativeSource, extension de balisage](relativesource-markupextension.md)
- [Binding, extension de balisage](binding-markup-extension.md)
