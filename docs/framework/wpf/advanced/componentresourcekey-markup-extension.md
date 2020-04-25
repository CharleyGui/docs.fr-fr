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
ms.openlocfilehash: f86b7000b97bbc1287347947a9244c24a7de74c2
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141135"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey, extension de balisage
Définit et référence des clés pour les ressources qui sont chargées à partir d’assemblys externes. Cela permet à une recherche de ressource de spécifier un type de cible dans un assembly, plutôt qu’un dictionnaire de ressources explicite dans un assembly ou une classe.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Utilisation des attributs XAML (clé de paramètre, compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Utilisation des attributs XAML (clé de paramètre, verbose)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Utilisation des attributs XAML (demande de ressources, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Utilisation des attributs XAML (demande de ressource, commentaires)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" ... />  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nom du type de common language runtime public (CLR) défini dans l’assembly de ressource.|  
|`targetID`|Clé pour la ressource. Lorsque les ressources sont recherchées, `targetID` est analogue à la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) de la ressource.|  
  
## <a name="remarks"></a>Notes  
 Comme indiqué dans les utilisations ci-dessus, une`ComponentResourceKey`utilisation d’extension de balisage {} se trouve à deux emplacements :  
  
- Définition d’une clé dans un dictionnaire de ressources de thème, telle qu’elle est fournie par un auteur de contrôle.  
  
- Accès à une ressource de thème à partir de l’assembly, lorsque vous recréationez le contrôle, mais que vous souhaitez utiliser des valeurs de propriété provenant de ressources fournies par les thèmes du contrôle.  
  
 Pour référencer des ressources de composant provenant de thèmes, il est généralement recommandé d' `{DynamicResource}` utiliser plutôt `{StaticResource}`que. Cela est illustré dans les utilisations. `{DynamicResource}`est recommandé, car le thème lui-même peut être modifié par l’utilisateur. Si vous souhaitez que la ressource de composant corresponde le mieux à l’intention de l’auteur du contrôle pour la prise en charge d’un thème, vous devez également activer la référence de ressource de votre composant comme étant dynamique.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identifie un type qui existe dans l’assembly cible où la ressource est réellement définie. Un `ComponentResourceKey` peut être défini et utilisé indépendamment de savoir exactement où le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> est défini, mais qui finit par résoudre le type par le biais d’assemblys référencés.  
  
 Une utilisation courante de <xref:System.Windows.ComponentResourceKey> est de définir des clés qui sont ensuite exposées comme membres d’une classe. Pour cette utilisation, vous utilisez le <xref:System.Windows.ComponentResourceKey> constructeur de classe, pas l’extension de balisage. Pour plus d’informations, <xref:System.Windows.ComponentResourceKey>consultez ou la section « Définition et référencement de clés pour les ressources de thème » de la rubrique [vue d’ensemble](../controls/control-authoring-overview.md)de la création de contrôles.  
  
 Pour la création de clés et le référencement de ressources de clé, la syntaxe `ComponentResourceKey` d’attribut est couramment utilisée pour l’extension de balisage.  
  
 La syntaxe compact indiquée s’appuie sur la <xref:System.Windows.ComponentResourceKey.%23ctor%2A> signature du constructeur et l’utilisation des paramètres positionnels d’une extension de balisage. L’ordre dans lequel les `targetTypeName` et `targetID` sont donnés est important. La syntaxe détaillée s’appuie sur le <xref:System.Windows.ComponentResourceKey.%23ctor%2A> constructeur sans paramètre, puis définit le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> d’une manière analogue à une syntaxe d’attribut vraie sur un élément objet. Dans la syntaxe détaillée, l’ordre dans lequel les propriétés sont définies n’est pas important. La relation et les mécanismes de ces deux solutions (compact et détaillé) sont décrits plus en détail dans la rubrique [extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Techniquement, la valeur de `targetID` peut être n’importe quel objet, il n’est pas nécessaire qu’il s’agit d’une chaîne. Toutefois, l’utilisation la plus courante dans WPF consiste à aligner `targetID` la valeur avec les formulaires qui sont des chaînes et où ces chaînes sont valides dans la [grammaire XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, la spécification de la valeur des <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> propriétés <xref:System.Windows.ComponentResourceKey.ResourceId%2A> et est requise pour initialiser correctement l’extension.  
  
 Dans l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du lecteur, la gestion de cette extension de balisage est <xref:System.Windows.ComponentResourceKey> définie par la classe.  
  
 `ComponentResourceKey` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
