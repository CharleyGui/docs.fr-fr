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
ms.openlocfilehash: 579fae46a7c53a61b728d7526ef397eb371abb74
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141068"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource, extension de balisage
Fournit une valeur pour n' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] importe quel attribut de propriété en différant cette valeur en tant que référence à une ressource définie. Le comportement de recherche pour cette ressource est analogue à la recherche au moment de l’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{DynamicResource key}" ... />  
```  
  
## <a name="xaml-property-element-usage"></a>Utilisation des éléments de propriété XAML  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`key`|Clé pour la ressource demandée. Cette clé a été initialement assignée par la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) si une ressource a été créée dans le `key` balisage ou si elle <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> a été fournie en tant que paramètre lors de l’appel de si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Notes   
 Un `DynamicResource` crée une expression temporaire pendant la compilation initiale et par conséquent, la recherche des ressources est différée jusqu’à ce que la valeur de ressource demandée soit réellement requise pour construire un objet. Cela peut se faire éventuellement après [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le chargement de la page. La valeur de ressource est recherchée en fonction de la recherche de clé par rapport à tous les dictionnaires de ressources actifs en commençant par l’étendue de la page actuelle, et remplace l’expression d’espace réservé de la compilation.  
  
> [!IMPORTANT]
> En termes de priorité des propriétés de dépendance `DynamicResource` , une expression est équivalente à la position à laquelle la référence de ressource dynamique est appliquée. Si vous définissez une valeur locale pour une propriété qui avait précédemment une `DynamicResource` expression comme valeur locale, le `DynamicResource` est complètement supprimé. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 Certains scénarios d’accès aux ressources sont particulièrement `DynamicResource` appropriés pour, par opposition à une [extension de balisage StaticResource](staticresource-markup-extension.md). Consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) pour une discussion sur les avantages relatifs et les implications relatives `DynamicResource` aux `StaticResource`performances de et.  
  
 Le spécifié <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> doit correspondre à une ressource existante déterminée par la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) à un certain niveau de la page, de l’application, des thèmes de contrôle disponibles et des ressources externes, ou des ressources système, et la recherche de ressources se produira dans cet ordre. Pour plus d’informations sur la recherche de ressources pour les ressources statiques et dynamiques, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Une clé de ressource peut également être d’autres types d’objets, <xref:System.Type>tels qu’un. Une <xref:System.Type> clé est essentielle à la façon dont les contrôles peuvent être mis en forme par des thèmes. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Les API de recherche de valeurs de ressource, <xref:System.Windows.FrameworkElement.FindResource%2A>telles que, suivent la même logique de recherche de `DynamicResource`ressource que celle utilisée par.  
  
 Les autres méthodes déclaratives de référencement d’une ressource sont en tant qu' [extension de balisage StaticResource](staticresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `DynamicResource` est assigné en tant que valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la classe d’extension <xref:System.Windows.DynamicResourceExtension> sous-jacente.  
  
 `DynamicResource`peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, la spécification de la valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la propriété est obligatoire.  
  
 `DynamicResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" ... />  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `DynamicResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est <xref:System.Windows.DynamicResourceExtension> définie par la classe.  
  
 `DynamicResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Ressources et code](resources-and-code.md)
- [x:Key, directive](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [StaticResource, extension de balisage](staticresource-markup-extension.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
