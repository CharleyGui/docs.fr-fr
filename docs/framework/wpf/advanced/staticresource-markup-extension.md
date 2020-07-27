---
title: StaticResource, extension de balisage
description: Fournit une valeur pour n’importe quel attribut de propriété XAML en recherchant une référence à une ressource déjà définie.
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 77396c1867dcbe279d7ba158ed9e6f5f833f17b5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164681"
---
# <a name="staticresource-markup-extension"></a>StaticResource, extension de balisage
Fournit une valeur pour n’importe quel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribut de propriété en recherchant une référence à une ressource déjà définie. Le comportement de recherche pour cette ressource est analogue à la recherche au moment du chargement, qui recherche les ressources qui ont été chargées précédemment à partir du balisage de la page actuelle, ainsi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que d’autres sources d’application, et qui génère cette valeur de ressource en tant que valeur de propriété dans les objets d’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`key`|Clé pour la ressource demandée. Cette clé a été initialement assignée par la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) si une ressource a été créée dans le balisage ou si elle a été fournie en tant que `key` paramètre lors de l’appel de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> Un `StaticResource` ne doit pas tenter de créer une référence avant à une ressource qui est définie de manière lexicale dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier. Toute tentative de ce type n’est pas prise en charge, et même si une telle référence n’échoue pas, toute tentative de référence anticipée entraîne une altération des performances du temps de chargement lors de la recherche des tables de hachage internes représentant un <xref:System.Windows.ResourceDictionary> . Pour de meilleurs résultats, ajustez la composition de vos dictionnaires de ressources de sorte que les références anticipées puissent être évitées. Si vous ne pouvez pas éviter une référence avant, utilisez l' [extension de balisage DynamicResource](dynamicresource-markup-extension.md) à la place.  
  
 Le spécifié <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> doit correspondre à une ressource existante, identifiée par une [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) à un certain niveau de la page, de l’application, des thèmes de contrôle disponibles et des ressources externes, ou des ressources système. La recherche de ressources se produit dans cet ordre. Pour plus d’informations sur le comportement de recherche de ressources pour les ressources statiques et dynamiques, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Une clé de ressource peut également être d’autres types d’objets, tels qu’un <xref:System.Type> . Une <xref:System.Type> clé est fondamentale pour la façon dont les contrôles peuvent être mis en forme par thèmes, à l’aide d’une clé de style implicite. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).  
  
 Les autres méthodes déclaratives de référencement d’une ressource sont en tant qu' [extension de balisage DynamicResource](dynamicresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `StaticResource` est assigné en tant que valeur <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> de la classe d’extension <xref:System.Windows.StaticResourceExtension> sous-jacente.  
  
 `StaticResource`peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, la spécification de la valeur de la <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> propriété est obligatoire.  
  
 `StaticResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `StaticResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par la <xref:System.Windows.StaticResourceExtension> classe.  
  
 `StaticResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Ressources et code](resources-and-code.md)
