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
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548271"
---
# <a name="xkey-directive"></a>x:Key, directive
Identifie de façon unique les éléments qui sont créés et référencés dans un dictionnaire défini en XAML. L’ajout d’une `x:Key` valeur à un élément objet XAML est le moyen le plus courant d’identifier une ressource dans un dictionnaire de ressources, par exemple dans un WPF <xref:System.Windows.ResourceDictionary> .  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Utilisation d’attributs XAML (spécifique à WPF)  
  
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
|`stringKeyValue`|Chaîne de texte à utiliser comme clé. La chaîne de texte doit être conforme à la [syntaxe XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|Dans les délimiteurs d’extension de balisage, il s’agit d' {} une utilisation d’extension de balisage qui fournit un objet à utiliser comme clé. Consultez la section Notes.|  
  
## <a name="remarks"></a>Notes  
 `x:Key` prend en charge le concept de dictionnaire de ressources XAML. XAML en tant que langage ne définit pas une implémentation de dictionnaire de ressources, qui est conservée dans des infrastructures d’interface utilisateur spécifiques. Pour en savoir plus sur la façon dont les dictionnaires de ressources XAML sont implémentés dans WPF, consultez [ressources XAML](../fundamentals/xaml-resources-define.md).  
  
 Dans XAML 2006 et WPF, `x:Key` doit être fourni en tant qu’attribut. Vous pouvez toujours utiliser des clés qui ne sont pas des chaînes, mais cela nécessite une utilisation d’extension de balisage afin de fournir la valeur de non-chaîne sous forme d’attribut. Si vous utilisez XAML 2009, `x:Key` peut être spécifié comme un élément, pour prendre en charge explicitement des dictionnaires indexés par des types d’objets autres que des chaînes sans nécessiter d’extension de balisage intermédiaire. Consultez la section « XAML 2009 » dans cette rubrique. Le reste de la section Remarques s’applique spécifiquement à l’implémentation XAML 2006.  
  
 La valeur d’attribut de `x:Key` peut être n’importe quelle chaîne définie dans la [grammaire XamlName](xamlname-grammar.md) ou peut être un objet évalué par le biais d’une extension de balisage. Consultez « Remarques sur l’utilisation de WPF » pour obtenir un exemple de WPF.  
  
 Les éléments enfants d’un élément parent qui est une <xref:System.Collections.IDictionary> implémentation doivent généralement inclure un `x:Key` attribut qui spécifie une valeur de clé unique dans ce dictionnaire. Les infrastructures peuvent implémenter des propriétés de clé avec alias pour remplacer `x:Key` sur des types particuliers ; les types qui définissent de telles propriétés doivent être attribués avec <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> .  
  
 Le code équivalent à la spécification `x:Key` est la clé utilisée pour le sous-jacent <xref:System.Collections.IDictionary> . Par exemple, un `x:Key` qui est appliqué dans le balisage pour une ressource dans WPF est équivalent à la valeur du `key` paramètre de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> lorsque vous ajoutez la ressource à un WPF <xref:System.Windows.ResourceDictionary> dans le code.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF  
 Les objets enfants d’un objet parent qui est une <xref:System.Collections.IDictionary> implémentation, tels que WPF <xref:System.Windows.ResourceDictionary> , doivent généralement inclure un `x:Key` attribut, et la valeur de clé doit être unique dans ce dictionnaire. Il existe deux exceptions notables :  
  
- Certains types WPF déclarent une clé implicite pour l’utilisation de dictionnaire. Par exemple, un <xref:System.Windows.Style> avec un <xref:System.Windows.Style.TargetType%2A> , ou un <xref:System.Windows.DataTemplate> avec un <xref:System.Windows.DataTemplate.DataType%2A> , peut être dans un <xref:System.Windows.ResourceDictionary> et utiliser la clé implicite.  
  
- WPF prend en charge un concept de dictionnaire de ressources fusionné. Les clés peuvent être partagées entre les dictionnaires fusionnés, et le comportement de la clé partagée est accessible à l’aide de <xref:System.Windows.FrameworkContentElement.FindResource%2A> . Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).  
  
 Dans l’implémentation générale et le modèle d’application XAML WPF, l’unicité de la clé n’est pas vérifiée par le compilateur de balisage XAML. Au lieu de cela, les valeurs manquantes ou non uniques `x:Key` provoquent des erreurs de l’analyseur XAML au moment du chargement. Toutefois, la gestion de Visual Studio des dictionnaires pour WPF peut souvent noter de telles erreurs dans la phase de conception.  
  
 Notez que dans la syntaxe indiquée, l' <xref:System.Windows.ResourceDictionary> objet est implicite dans la manière dont le processeur XAML WPF produit une collection pour remplir une <xref:System.Windows.FrameworkElement.Resources%2A> collection. Un <xref:System.Windows.ResourceDictionary> n’est généralement pas fourni explicitement comme un élément dans le balisage, bien qu’il puisse être dans certains cas, s’il le souhaite, à des fins de clarté (il s’agit d’un élément objet de collection entre l' <xref:System.Windows.FrameworkElement.Resources%2A> élément de propriété et les éléments dans qui remplissent le dictionnaire). Pour plus d’informations sur la raison pour laquelle un objet de collection est presque toujours un élément implicite dans le balisage, consultez [syntaxe XAML en détail](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail).  
  
 Dans l’implémentation XAML WPF, la gestion des clés de dictionnaire de ressources est définie par la <xref:System.Windows.ResourceKey> classe abstraite. Toutefois, le processeur XAML WPF produit des types d’extension sous-jacents différents pour les clés en fonction de leurs utilisations. Par exemple, la clé d’une <xref:System.Windows.DataTemplate> classe ou d’une classe dérivée est gérée séparément et produit un <xref:System.Windows.DataTemplateKey> objet distinct.  
  
 Les clés et les noms utilisent des directives et des éléments de langage différents ( `x:Key` `x:Name` par rapport à) dans la définition XAML de base. Les clés et les noms sont également utilisés dans différentes situations par la définition WPF et l’application de ces concepts. Pour plus d’informations, consultez portées de [code XAML WPF](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).  
  
 Comme indiqué précédemment, la valeur d’une clé peut être fournie par le biais d’une extension de balisage et peut être différente d’une valeur de chaîne. Un exemple de scénario WPF est que la valeur de `x:Key` peut être un [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension). Certains contrôles exposent une clé de style de ce type pour une ressource de style personnalisée qui influence une partie de l’apparence et du comportement de ce contrôle sans remplacer totalement le style. Un exemple d’une telle clé est <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> .  
  
 La fonctionnalité de dictionnaire fusionné WPF introduit des considérations supplémentaires pour l’unicité des clés et le comportement de recherche de clé. Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 assouplit la restriction qui `x:Key` est toujours fournie sous forme d’attribut.  
  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n’est pas compilé par balisage. Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 Sous XAML 2009, vous pouvez spécifier `x:Key` des éléments par le biais de l’utilisation suivante :  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Utilisation des éléments XAML (XAML 2009 uniquement)  
  
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
|`keyObject`|Élément objet pour l’objet qui est utilisé comme clé pour un donné `object` dans un dictionnaire spécialisé.|  
  
- Le conteneur/parent de ce type d’utilisation n’est pas indiqué ici. `object` est supposé être un enfant d’un élément objet qui représente une implémentation de dictionnaire spécialisée. `keyObject` est supposé être une instance d’objet (ou une valeur d’un type valeur) qui est appropriée comme clé pour cette implémentation de dictionnaire spécialisé particulière.  
  
- WPF n’implémente pas les dictionnaires qui requièrent cette utilisation. Les clés d’objet sont plus une fonctionnalité générale du langage XAML, qui peut s’avérer utile pour certains scénarios de dictionnaires personnalisés où la création du dictionnaire en XAML est souhaitable. Pour les fonctionnalités WPF telles que les styles implicites qui utilisent des clés de non-chaîne pour les ressources, d’autres techniques permettant d’établir ou de spécifier les clés existent, l’utilisation d’une clé d’objet n’est donc pas nécessaire.  
  
- `keyObject` peut également être une utilisation d’extension de balisage dans un formulaire d’élément objet, plutôt qu’une instance d’objet directe.  
  
## <a name="silverlight-usage-notes"></a>Remarques sur l’utilisation de Silverlight  
 `x:Key` pour Silverlight est documenté séparément. Pour plus d’informations, consultez [espace de noms XAML (x :) Fonctionnalités de langage (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../fundamentals/xaml-resources-define.md)
- [Ressources et code](/dotnet/desktop/wpf/advanced/resources-and-code)
- [StaticResource, extension de balisage](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
