---
title: x:Key, directive
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071499"
---
# <a name="xkey-directive"></a>x:Key, directive
Identifie de façon unique les éléments qui sont créés et référencés dans un dictionnaire XAML défini. L’ajout d’une `x:Key` valeur à un élément d’objet XAML est le moyen <xref:System.Windows.ResourceDictionary>le plus courant d’identifier une ressource dans un dictionnaire de ressources, par exemple dans un WPF .  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Utilisation d’attributs XAML (spécifique au FMM)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`stringKeyValue`|Une chaîne de texte à utiliser comme clé. La chaîne de texte doit se conformer à la [grammaire XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|Dans l’extension de balisage délimite , une utilisation d’extension de balisage {}qui fournit un objet à utiliser comme clé. Consultez la section Notes.|  
  
## <a name="remarks"></a>Notes  
 `x:Key`prend en charge le concept de dictionnaire de ressources XAML. XAML en tant que langue ne définit pas une implémentation de dictionnaire de ressources, qui est laissée à des cadres spécifiques d’interface utilisateur. Pour en savoir plus sur la façon dont les dictionnaires de ressources XAML sont mis en œuvre dans WPF, voir [XAML Resources](../fundamentals/xaml-resources-define.md).  
  
 Dans XAML 2006 et `x:Key` WPF, doit être fourni comme un attribut. Vous pouvez toujours utiliser des touches noncordantes, mais cela nécessite une utilisation d’extension de balisage afin de fournir la valeur non-corde sous forme d’attribut. Si vous utilisez XAML 2009, `x:Key` peut être spécifié comme un élément, pour prendre explicitement en charge les dictionnaires clés par des types d’objets autres que les chaînes sans nécessiter une extension de balisage intermédiaire. Voir la section "XAML 2009" dans ce sujet. Le reste de la section Remarques s’applique spécifiquement à la mise en œuvre de XAML 2006.  
  
 La valeur `x:Key` d’attribut de peut être n’importe quelle chaîne définie dans la [grammaire XamlName](xamlname-grammar.md) ou peut être un objet évalué par une extension de balisage. Voir "WPF Usage Notes" par exemple de WPF.  
  
 Les éléments pour enfants d’un élément parent qui est une <xref:System.Collections.IDictionary> mise en œuvre doivent généralement inclure un `x:Key` attribut qui spécifie une valeur clé unique dans ce dictionnaire. Les cadres peuvent mettre en œuvre des propriétés clés alias pour `x:Key` remplacer certains types; les types qui définissent ces <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>propriétés doivent être attribués avec .  
  
 Le code équivalent `x:Key` à la spécifier <xref:System.Collections.IDictionary>est la clé qui est utilisée pour le sous-jacent . Par exemple, `x:Key` un qui est appliqué en marge pour une ressource `key` dans <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> WPF est équivalent à <xref:System.Windows.ResourceDictionary> la valeur du paramètre de quand vous ajoutez la ressource à un WPF dans le code.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF  
 Les objets pour enfants d’un objet parent qui est une <xref:System.Collections.IDictionary> implémentation, comme le WPF <xref:System.Windows.ResourceDictionary>, doivent généralement inclure un `x:Key` attribut, et la valeur clé doit être unique dans ce dictionnaire. Il y a deux exceptions notables :  
  
- Certains types WPF déclarent une clé implicite pour l’utilisation du dictionnaire. Par exemple, <xref:System.Windows.Style> un <xref:System.Windows.Style.TargetType%2A>avec <xref:System.Windows.DataTemplate> un <xref:System.Windows.DataTemplate.DataType%2A>, ou un <xref:System.Windows.ResourceDictionary> avec un , peut être dans un et utiliser la clé implicite.  
  
- WPF prend en charge un concept de dictionnaire de ressources fusionné. Les clés peuvent être partagées entre les dictionnaires fusionnés, et <xref:System.Windows.FrameworkContentElement.FindResource%2A>le comportement clé partagé peut être consulté à l’aide de . Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Dans le modèle global de mise en œuvre et d’application WPF XAML, l’unicité des clés n’est pas vérifiée par le compilateur de balisage XAML. Au lieu de cela, les valeurs manquantes ou non ponctuelles `x:Key` causent des erreurs de parsion XAML à temps de charge. Cependant, la manipulation visual Studio des dictionnaires pour WPF peut souvent noter de telles erreurs dans la phase de conception.  
  
 Notez que dans la <xref:System.Windows.ResourceDictionary> syntaxe montrée, l’objet est implicite dans la <xref:System.Windows.FrameworkElement.Resources%2A> façon dont le processeur WPF XAML produit une collection pour remplir une collection. A <xref:System.Windows.ResourceDictionary> n’est généralement pas fourni explicitement comme élément de majoration, bien qu’il puisse être <xref:System.Windows.FrameworkElement.Resources%2A> dans certains cas si elle est voulue pour la clarté (il s’agirait d’un élément objet de collecte entre l’élément de propriété et les éléments qui peuplent le dictionnaire). Pour plus d’informations sur les raisons pour lesquelles un objet de collecte est presque toujours un élément implicite dans la balisage, voir [XAML Syntax In Detail](../../framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Dans la mise en œuvre de WPF XAML, la manipulation des clés de dictionnaire des ressources est définie par la <xref:System.Windows.ResourceKey> classe abstraite. Toutefois, le processeur WPF XAML produit différents types d’extension sous-jacent pour les touches en fonction de leurs utilisations. Par exemple, la <xref:System.Windows.DataTemplate> clé d’une ou de n’importe <xref:System.Windows.DataTemplateKey> quelle classe dérivée est manipulée séparément et produit un objet distinct.  
  
 Les clés et les noms`x:Key` utilisent `x:Name`différentes directives et éléments de langage (par rapport) dans la définition de base XAML. Les clés et les noms sont également utilisés dans différentes situations par la définition et l’application de ces concepts. Pour plus de détails, voir [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Comme indiqué précédemment, la valeur d’une clé peut être fournie par une extension de balisage et peut être autre qu’une valeur de chaîne. Un exemple WPF scénario est `x:Key` que la valeur de peut être un [ComponentResourceKey](../../framework/wpf/advanced/componentresourcekey-markup-extension.md). Certains contrôles exposent une clé de style de ce type pour une ressource de style personnalisé qui influence une partie de l’apparence et le comportement de ce contrôle sans remplacer totalement le style. Un exemple d’une <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>telle clé est .  
  
 La fonction de dictionnaire fusionné WPF introduit des considérations supplémentaires pour l’unicité clé et le comportement de recherche clé. Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 assouplit `x:Key` la restriction qui est toujours fournie sous forme d’attribut.  
  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour XAML qui n’est pas compilée. Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 Dans le cadre de XAML 2009, vous pouvez spécifier `x:Key` des éléments grâce à l’utilisation suivante :  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Utilisation d’éléments XAML (XAML 2009 seulement)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`keyObject`|Élément d’objet pour l’objet qui `object` est utilisé comme clé pour un donné dans un dictionnaire spécialisé.|  
  
- Le conteneur /parent pour ce type d’utilisation n’est pas montré ici. `object`on s’attend à ce qu’il soit un enfant d’un élément d’objet qui représente une mise en œuvre spécialisée de dictionnaire. `keyObject`on s’attend à ce qu’il s’propri été soit une instance d’objet (ou une valeur d’un type de valeur) qui soit appropriée comme clé pour cette mise en œuvre particulière de dictionnaire spécialisé.  
  
- WPF ne met pas en œuvre les dictionnaires qui nécessitent cette utilisation. Les touches d’objet sont plus une caractéristique générale de la langue XAML, peut-être utile pour certains scénarios de dictionnaire personnalisé où la création du dictionnaire dans XAML est souhaitable. Pour les fonctionnalités WPF telles que les styles implicites qui utilisent des touches non-cordes pour les ressources, d’autres techniques pour établir ou spécifier les clés existent, de sorte que l’utilisation d’une clé d’objet n’est pas nécessaire.  
  
- `keyObject`pourrait également être une utilisation d’extension de balisage sous forme d’élément d’objet, plutôt qu’une instance d’objet direct.  
  
## <a name="silverlight-usage-notes"></a>Notes d’utilisation Silverlight  
 `x:Key`pour Silverlight est documenté séparément. Pour plus d’informations, voir [XAML Namespace (x:) Caractéristiques linguistiques (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../fundamentals/xaml-resources-define.md)
- [Ressources et code](../../framework/wpf/advanced/resources-and-code.md)
- [StaticResource, extension de balisage](../../framework/wpf/advanced/staticresource-markup-extension.md)
