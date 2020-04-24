---
title: ThemeDictionary, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646188"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary, extension de balisage
Cette extension offre un moyen aux auteurs de contrôles personnalisés ou aux applications qui intègrent des contrôles tiers de charger les dictionnaires de ressources de thème utilisés pour appliquer un style à un contrôle.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`assemblyUri`|L’identifiant de ressource uniforme (URI) de l’assemblage qui contient des informations thématiques. Il s’agit généralement d’un URI à en-tête pack qui référence un assembly dans le package plus large. Les ressources d’assembly et les URI à en-tête pack simplifient le déploiement. Pour plus d’informations voir [Pack URIs dans WPF](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Notes  
 Cette extension est destinée à combler une seule <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>valeur de propriété spécifique: une valeur pour .  
  
 En utilisant cette extension, vous pouvez spécifier un seul assemblage de ressources uniquement qui contient certains styles à utiliser uniquement lorsque le thème Windows Aero est appliqué au système de l’utilisateur, d’autres styles seulement lorsque le thème Luna est actif, et ainsi de suite. Quand vous utilisez cette extension, le contenu d’un dictionnaire de ressources d’un contrôle peut être automatiquement invalidé et rechargé pour un autre thème spécifique, si nécessaire.  
  
 La `assemblyUri` chaîne<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> (valeur de propriété) constitue la base d’une convention de nommage qui identifie quel dictionnaire s’applique pour un thème particulier. La <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logique `ThemeDictionary` pour compléter la convention en générant un identifiant de ressource uniforme (URI) qui indique une variante particulière de dictionnaire de thème, tel qu’il est contenu dans un assemblage de ressources précompilé. La description de cette convention, ou des interactions de thème à l’aide du style de contrôle général et du style de niveau page/application en tant que concept, n’est pas examinée de manière approfondie dans cette rubrique. Le scénario de `ThemeDictionary` base pour <xref:System.Windows.ResourceDictionary.Source%2A> l’utilisation est de spécifier la propriété d’un `ResourceDictionary` déclaré au niveau de l’application. Lorsque vous fournissez une URI `ThemeDictionary` pour l’assemblage par le biais d’une extension plutôt que comme une URI directe, la logique d’extension fournira la logique d’invalidation qui s’applique chaque fois que le thème du système change.  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `ThemeDictionary` est assigné en tant que valeur <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> de la classe d’extension <xref:System.Windows.ThemeDictionaryExtension> sous-jacente.  
  
 `ThemeDictionary` peut également être utilisé dans la syntaxe de l’élément objet. Dans ce cas, il faut <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> préciser la valeur de la propriété.  
  
 `ThemeDictionary` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.Markup.StaticExtension.Member%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. `ThemeDictionary` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la mise en œuvre du processeur, <xref:System.Windows.ThemeDictionaryExtension> la manipulation de cette extension de balisage est définie par la classe.  
  
 `ThemeDictionary` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Fichiers de ressources, de contenu et de données d’une application WPF](../app-development/wpf-application-resource-content-and-data-files.md)
