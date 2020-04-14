---
title: ComponentResourceKey, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243360"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey, extension de balisage
Définit et référence les clés pour les ressources chargées à partir d’assemblages externes. Cela permet à une recherche de ressources de spécifier un type cible dans un assemblage, plutôt qu’un dictionnaire de ressources explicite dans une assemblée ou sur une classe.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Utilisation d’attributs XAML (clé de réglage, compacte)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Utilisation d’attributs XAML (clé de réglage, verbose)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Utilisation d’attributs XAML (ressource demandée, compacte)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Utilisation d’attributs XAML (demande de ressources, verbose)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`targetTypeName`|Le nom du type public de l’heure courante de langue (CLR) qui est défini dans l’assemblage des ressources.|  
|`targetID`|La clé de la ressource. Lorsque les ressources `targetID` seront examinées, elles seront analogues à la [directive x: Key](../../../desktop-wpf/xaml-services/xkey-directive.md) de la ressource.|  
  
## <a name="remarks"></a>Notes  
 Comme on le voit dans`ComponentResourceKey`les utilisations ci-dessus, l’utilisation d’une extension de balisage se trouve à deux endroits :  
  
- La définition d’une clé dans un dictionnaire de ressources thématiques, telle qu’fournie par un auteur de contrôle.  
  
- Accéder à une ressource thématique de l’assemblée, lorsque vous retemplating le contrôle, mais que vous voulez utiliser les valeurs de propriété qui proviennent des ressources fournies par les thèmes du contrôle.  
  
 Pour le référencement des ressources de composants qui `{DynamicResource}` proviennent `{StaticResource}`de thèmes, il est généralement recommandé que vous utilisiez plutôt que . Ceci est indiqué dans les usages. `{DynamicResource}`est recommandé parce que le thème lui-même peut être changé par l’utilisateur. Si vous voulez que la ressource de composants qui correspond le plus étroitement à l’intention de l’auteur de contrôle pour soutenir un thème, vous devriez permettre à votre référence de ressource de composant d’être dynamique également.  
  
 Le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifie un type qui existe dans l’assemblage cible où la ressource est effectivement définie. A `ComponentResourceKey` peut être défini et utilisé indépendamment <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> de savoir exactement où le est défini, mais doit éventuellement résoudre le type par des assemblages référencés.  
  
 Une utilisation <xref:System.Windows.ComponentResourceKey> courante est de définir les clés qui sont ensuite exposées en tant que membres d’une classe. Pour cette utilisation, <xref:System.Windows.ComponentResourceKey> vous utilisez le constructeur de classe, pas l’extension de balisage. Pour plus d’informations, voir <xref:System.Windows.ComponentResourceKey>, ou la section " Définir et se référer des clés pour les ressources thématiques " du sujet Contrôle [Authoring Overview](../controls/control-authoring-overview.md).  
  
 Pour établir des clés et faire référence aux ressources clés, la syntaxe d’attribut est couramment utilisée pour l’extension de `ComponentResourceKey` balisage.  
  
 La syntaxe compacte <xref:System.Windows.ComponentResourceKey.%23ctor%2A> indiquée repose sur la signature du constructeur et l’utilisation des paramètres de position d’une extension de balisage. L’ordre dans `targetTypeName` `targetID` lequel le et sont donnés est important. La syntaxe verbeuse <xref:System.Windows.ComponentResourceKey.%23ctor%2A> repose sur le constructeur <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> sans <xref:System.Windows.ComponentResourceKey.ResourceId%2A> paramètres, puis définit le et d’une manière qui est analogue à une syntaxe d’attribut réel sur un élément d’objet. Dans la syntaxe verbeuse, l’ordre dans lequel les propriétés sont définies n’est pas important. La relation et les mécanismes de ces deux alternatives (compactes et verbeuses) sont décrits plus en détail dans le thème [Markup Extensions et WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Techniquement, la `targetID` valeur pour peut être n’importe quel objet, il n’a pas besoin d’être une chaîne. Cependant, l’utilisation la plus courante `targetID` dans WPF est d’aligner la valeur avec les formes qui sont des chaînes, et lorsque ces chaînes sont valides dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`peut être utilisé dans la syntaxe d’élément d’objet. Dans ce cas, il est <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> nécessaire <xref:System.Windows.ComponentResourceKey.ResourceId%2A> de préciser la valeur de la valeur et des propriétés pour l’initialisation appropriée de l’extension.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] l’implémentation du lecteur, la <xref:System.Windows.ComponentResourceKey> manipulation de cette extension de balisage est définie par la classe.  
  
 `ComponentResourceKey` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
