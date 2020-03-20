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
# <a name="templatebinding-markup-extension"></a>TemplateBinding, extension de balisage
Cette extension lie la valeur d'une propriété dans un modèle de contrôle afin de la définir comme valeur d'une autre propriété exposée dans le contrôle basé sur un modèle.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
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
|`sourceProperty`|Autre propriété de dépendance qui existe sur le type basé sur un modèle, spécifiée par <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - ou -<br /><br /> Nom de propriété « dotted-down » défini par un autre type que le type de cible basé sur un modèle. Il s'agit en réalité d'un <xref:System.Windows.PropertyPath>. Voir [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Notes   
 A `TemplateBinding` est une forme optimisée d’une [liaison](binding-markup-extension.md) pour `Binding` les `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`scénarios de modèle, analogue à un construit avec . `TemplateBinding` est toujours une liaison unidirectionnelle, même si les propriétés ont comme valeur par défaut des liaisons bidirectionnelles. Les deux propriétés doivent toutes être des propriétés de dépendance. Afin d’atteindre la liaison bidirectionnel à un `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`parent modélné utiliser l’instruction contraignante suivante à la place .
  
 [RelativeSource](relativesource-markupextension.md) est une autre extension de balisage `TemplateBinding` qui est parfois utilisée en conjonction avec ou au lieu de afin d’effectuer la liaison relative de propriété dans un modèle.  
  
 Décrire les modèles de contrôle comme un concept n’est pas couvert ici; pour plus d’informations, voir [Styles de contrôle et Modèles](../controls/control-styles-and-templates.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `TemplateBinding` est assigné en tant que valeur <xref:System.Windows.TemplateBindingExtension.Property%2A> de la classe d’extension <xref:System.Windows.TemplateBindingExtension> sous-jacente.  
  
 La syntaxe d'élément objet est possible, mais elle n'est pas indiquée car elle ne possède aucune application réaliste. `TemplateBinding` est utilisé pour remplir des valeurs dans des méthodes setter, à l'aide d'expressions évaluées. En outre, l'utilisation de la syntaxe d'élément objet de `TemplateBinding` pour remplir la syntaxe des éléments de propriété `<Setter.Property>` est inutilement détaillée.  
  
 `TemplateBinding` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.TemplateBindingExtension.Property%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `TemplateBinding` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la mise en œuvre du processeur XAML, la manipulation de cette extension de balisage est définie par la <xref:System.Windows.TemplateBindingExtension> classe.  
  
 `TemplateBinding` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage dans XAML utilisent le `{` syntaxe d’attribut, `}` qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Application d’un style et création de modèles](../controls/styling-and-templating.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [RelativeSource, extension de balisage](relativesource-markupextension.md)
- [Binding, extension de balisage](binding-markup-extension.md)
