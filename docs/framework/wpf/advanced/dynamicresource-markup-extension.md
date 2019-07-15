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
ms.openlocfilehash: 90768a0c816e790138ba60bd24afee242e41e652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860288"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource, extension de balisage
Fournit une valeur pour tout [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribut de propriété en différant cette valeur pour être une référence à une ressource définie. Le comportement de recherche pour cette ressource est analogue à la recherche au moment de l’exécution.  
  
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
|`key`|Clé pour la ressource demandée. Cette clé a été initialement affectée par le [Directive x : Key](../../xaml-services/x-key-directive.md) si une ressource a été créée dans le balisage ou a été fournie comme le `key` paramètre lors de l’appel <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Notes  
 Un `DynamicResource` créera une expression temporaire pendant la compilation initiale et donc diffèrera la recherche des ressources jusqu'à ce que la valeur de la ressource demandée est réellement nécessaire pour construire un objet. Cela peut potentiellement être après le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page est chargée. La valeur de ressource est trouvée en fonction de recherche de clé par rapport à tous les dictionnaires de ressources actif à partir de la portée de page actuelle et est remplacée par l’expression d’espace réservé à partir de la compilation.  
  
> [!IMPORTANT]
>  En termes de priorité de propriété de dépendance, un `DynamicResource` expression est équivalente à la position où la référence de ressource dynamique est appliquée. Si vous définissez une valeur locale pour une propriété qui avait précédemment un `DynamicResource` expression en tant que la valeur locale, le `DynamicResource` est totalement supprimé. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 Certains scénarios d’accès aux ressources sont particulièrement appropriés pour `DynamicResource` par opposition à un [Extension de balisage StaticResource](staticresource-markup-extension.md). Consultez [XAML ressources](xaml-resources.md) pour une discussion sur les implications en matière de performances de leurs avantages relatifs respectifs `DynamicResource` et `StaticResource`.  
  
 Spécifié <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> doit correspondre à une ressource existante déterminée par [Directive x : Key](../../xaml-services/x-key-directive.md) à un certain niveau dans votre page, application, thèmes de contrôle disponibles et ressources externes ou les ressources système et le recherche de ressources aura lieu dans cet ordre. Pour plus d’informations sur la recherche de ressources pour les ressources statiques et dynamiques, consultez [XAML ressources](xaml-resources.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans le [XamlName, grammaire](../../xaml-services/xamlname-grammar.md). Une clé de ressource peut être également les autres types d’objets, comme un <xref:System.Type>. Un <xref:System.Type> clé est essentielle à la façon dont styles peuvent leur être par des thèmes. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Valeurs des API pour la recherche des ressources, telles que <xref:System.Windows.FrameworkElement.FindResource%2A>, suivent la même logique de recherche de ressources que celles utilisées par `DynamicResource`.  
  
 L’autre moyen déclaratif de référencement d’une ressource est comme un [Extension de balisage StaticResource](staticresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `DynamicResource` est assigné en tant que valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la classe d’extension <xref:System.Windows.DynamicResourceExtension> sous-jacente.  
  
 `DynamicResource` peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> propriété est requise.  
  
 `DynamicResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `DynamicResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.DynamicResourceExtension> classe.  
  
 `DynamicResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](xaml-resources.md)
- [Ressources et code](resources-and-code.md)
- [x:Key, directive](../../xaml-services/x-key-directive.md)
- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [StaticResource, extension de balisage](staticresource-markup-extension.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
