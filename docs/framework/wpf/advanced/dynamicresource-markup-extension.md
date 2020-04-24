---
title: DynamicResource, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: 5ccda8ba8f41a30e0ce1c832a6d3176b7fb8e8c2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646261"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource, extension de balisage
Fournit une valeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour tout attribut de propriété en reportant cette valeur pour être une référence à une ressource définie. Le comportement de recherche pour cette ressource est analogue à la recherche de temps d’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Utilisation des éléments de propriété XAML  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`key`|Clé pour la ressource demandée. Cette clé a d’abord été attribuée par la [directive x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) si `key` une <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> ressource a été créée en majoration, ou a été fournie comme paramètre lors de l’appel si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Notes  
 A `DynamicResource` créera une expression temporaire au cours de la compilation initiale et reportera ainsi la recherche de ressources jusqu’à ce que la valeur de ressources demandée soit réellement nécessaire pour construire un objet. Cela peut être [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] après la charge de la page. La valeur des ressources sera trouvée en fonction de la recherche clé contre tous les dictionnaires de ressources actifs à partir de la portée actuelle de la page, et est substituée à l’expression des placeholders de la compilation.  
  
> [!IMPORTANT]
> En termes de préséance foncière, une `DynamicResource` expression est équivalente à la position où la référence dynamique des ressources est appliquée. Si vous définissez une valeur locale `DynamicResource` pour une propriété qui `DynamicResource` avait auparavant une expression comme la valeur locale, le est complètement supprimé. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 Certains scénarios d’accès aux `DynamicResource` ressources sont particulièrement appropriés par opposition à une [extension de Markup StaticResource](staticresource-markup-extension.md). Voir [XAML Ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) pour une discussion sur les `DynamicResource` `StaticResource`mérites relatifs et les implications de rendement de et .  
  
 Le <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> spécifié doit correspondre à une ressource existante déterminée par [x: Directive clé](../../../desktop-wpf/xaml-services/xkey-directive.md) à un certain niveau dans votre page, application, les thèmes de contrôle disponibles et les ressources externes, ou les ressources du système, et le plan de ressources se produira dans cet ordre. Pour plus d’informations sur la recherche des ressources pour les ressources statiques et dynamiques, voir [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Une clé de ressource peut également être <xref:System.Type>d’autres types d’objets, tels que un . Une <xref:System.Type> clé est fondamentale pour la façon dont les contrôles peuvent être stylés par des thèmes. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Les API pour la recherche <xref:System.Windows.FrameworkElement.FindResource%2A>des valeurs des ressources, telles `DynamicResource`que , suivent la même logique de recherche de ressources que l’utilisation par .  
  
 Les autres moyens déclaratifs de référencement d’une ressource sont comme une [extension de Markup StaticResource](staticresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `DynamicResource` est assigné en tant que valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la classe d’extension <xref:System.Windows.DynamicResourceExtension> sous-jacente.  
  
 `DynamicResource`peut être utilisé dans la syntaxe d’élément d’objet. Dans ce cas, il faut <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> préciser la valeur de la propriété.  
  
 `DynamicResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `DynamicResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la mise en œuvre du processeur, <xref:System.Windows.DynamicResourceExtension> la manipulation de cette extension de balisage est définie par la classe.  
  
 `DynamicResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Ressources et code](resources-and-code.md)
- [x:Key, directive](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [StaticResource, extension de balisage](staticresource-markup-extension.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
