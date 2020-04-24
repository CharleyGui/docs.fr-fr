---
title: StaticResource, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646215"
---
# <a name="staticresource-markup-extension"></a>StaticResource, extension de balisage
Fournit une valeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour n’importe quel attribut de propriété en recherchant vers le haut une référence à une ressource déjà définie. Le comportement de recherche pour cette ressource est analogue à la recherche de temps de charge, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui cherchera des ressources qui ont été précédemment chargées à partir de la majoration de la page actuelle ainsi que d’autres sources d’application, et générera cette valeur de ressource comme valeur de propriété dans les objets de run-time.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`key`|Clé pour la ressource demandée. Cette clé a d’abord été attribuée par la [directive x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) si `key` une <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> ressource a été créée en majoration, ou a été fournie comme paramètre lors de l’appel si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> Il `StaticResource` ne faut pas tenter de faire une référence prospective à [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] une ressource qui est définie plus loin dans le fichier. La tentative de le faire n’est pas prise en charge, et même si une telle référence n’échoue <xref:System.Windows.ResourceDictionary> pas, tenter la référence avant entraînera une pénalité de performance de temps de charge lorsque les tables internes de hachage représentant un sont recherchées. Pour de meilleurs résultats, ajustez la composition de vos dictionnaires de ressources de façon à éviter les références avant. Si vous ne pouvez pas éviter une référence avant, utilisez [l’extension De Markup DynamicResource](dynamicresource-markup-extension.md) à la place.  
  
 Le <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> spécifié doit correspondre à une ressource existante, identifiée avec une [directive x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) à un certain niveau dans votre page, application, les thèmes de contrôle disponibles et les ressources externes, ou les ressources du système. La recherche des ressources se produit dans cet ordre. Pour plus d’informations sur le comportement de recherche de ressources pour les ressources statiques et dynamiques, voir [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Une clé de ressource peut également être <xref:System.Type>d’autres types d’objets, tels que un . Une <xref:System.Type> clé est fondamentale pour la façon dont les contrôles peuvent être stylés par des thèmes, à travers une clé de style implicite. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Le moyen déclaratif alternatif de référencement d’une ressource est comme une [extension De Markup DynamicResource](dynamicresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `StaticResource` est assigné en tant que valeur <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> de la classe d’extension <xref:System.Windows.StaticResourceExtension> sous-jacente.  
  
 `StaticResource`peut être utilisé dans la syntaxe d’élément d’objet. Dans ce cas, il faut <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> préciser la valeur de la propriété.  
  
 `StaticResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `StaticResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la mise en œuvre du processeur, <xref:System.Windows.StaticResourceExtension> la manipulation de cette extension de balisage est définie par la classe.  
  
 `StaticResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Ressources et code](resources-and-code.md)
