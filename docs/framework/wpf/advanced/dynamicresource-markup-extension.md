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
ms.openlocfilehash: f8b05f314be84e6104f1a9c7fe2edfdf826e51da
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559446"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource, extension de balisage
Fournit une valeur pour tout [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribut de propriété en différant cette valeur en tant que référence à une ressource définie. Le comportement de recherche pour cette ressource est analogue à la recherche au moment de l’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation des attributs XAML  
  
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
|`key`|Clé pour la ressource demandée. Cette clé a été initialement assignée par la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) si une ressource a été créée dans le balisage ou si elle a été fournie en tant que paramètre `key` lors de l’appel de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Notes  
 Une `DynamicResource` créera une expression temporaire pendant la compilation initiale et différera donc la recherche des ressources jusqu’à ce que la valeur de ressource demandée soit réellement requise pour construire un objet. Cela peut se faire éventuellement après le chargement de la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. La valeur de ressource est recherchée en fonction de la recherche de clé par rapport à tous les dictionnaires de ressources actifs en commençant par l’étendue de la page actuelle, et remplace l’expression d’espace réservé de la compilation.  
  
> [!IMPORTANT]
> En termes de priorité des propriétés de dépendance, une expression `DynamicResource` est équivalente à la position à laquelle la référence de ressource dynamique est appliquée. Si vous définissez une valeur locale pour une propriété qui avait précédemment une expression `DynamicResource` comme valeur locale, la `DynamicResource` est complètement supprimée. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 Certains scénarios d’accès aux ressources sont particulièrement appropriés pour les `DynamicResource` par opposition à une [extension de balisage StaticResource](staticresource-markup-extension.md). Consultez [ressources XAML](xaml-resources.md) pour une discussion sur les avantages relatifs et les implications sur les performances de `DynamicResource` et `StaticResource`.  
  
 Le <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> spécifié doit correspondre à une ressource existante déterminée par [la directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) à un certain niveau de la page, de l’application, des thèmes de contrôle disponibles et des ressources externes, ou des ressources système, et la recherche de ressources se produira dans cet ordre. Pour plus d’informations sur la recherche de ressources pour les ressources statiques et dynamiques, consultez [ressources XAML](xaml-resources.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Une clé de ressource peut également être d’autres types d’objets, tels qu’un <xref:System.Type>. Une clé de <xref:System.Type> est essentielle à la façon dont les contrôles peuvent être mis en forme par des thèmes. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Les API de recherche de valeurs de ressource, telles que <xref:System.Windows.FrameworkElement.FindResource%2A>, suivent la même logique de recherche de ressource que celle utilisée par `DynamicResource`.  
  
 Les autres méthodes déclaratives de référencement d’une ressource sont en tant qu' [extension de balisage StaticResource](staticresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `DynamicResource` est assigné en tant que valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la classe d’extension <xref:System.Windows.DynamicResourceExtension> sous-jacente.  
  
 `DynamicResource` peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, il est nécessaire de spécifier la valeur de la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>.  
  
 `DynamicResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `DynamicResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans l’implémentation du processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](xaml-resources.md)
- [Ressources et code](resources-and-code.md)
- [x:Key, directive](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [StaticResource, extension de balisage](staticresource-markup-extension.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
