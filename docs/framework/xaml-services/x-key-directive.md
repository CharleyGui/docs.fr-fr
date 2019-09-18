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
ms.openlocfilehash: eb9f9cc1dfdb802e340123d0d39e9c9ebaa457f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053747"
---
# <a name="xkey-directive"></a>x:Key, directive
Identifie de façon unique les éléments qui sont créés et référencés dans un dictionnaire défini en XAML. L’ajout `x:Key` d’une valeur à un élément objet XAML est le moyen le plus courant d’identifier une ressource dans un dictionnaire de ressources, par <xref:System.Windows.ResourceDictionary>exemple dans un WPF.  
  
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
|`markupExtensionUsage`|Dans les délimiteurs {}d’extension de balisage, il s’agit d’une utilisation d’extension de balisage qui fournit un objet à utiliser comme clé. Consultez la section Notes.|  
  
## <a name="remarks"></a>Notes  
 `x:Key`prend en charge le concept de dictionnaire de ressources XAML. XAML en tant que langage ne définit pas une implémentation de dictionnaire de ressources, qui est conservée dans des infrastructures d’interface utilisateur spécifiques. Pour en savoir plus sur la façon dont les dictionnaires de ressources XAML sont implémentés dans WPF, consultez [ressources XAML](../wpf/advanced/xaml-resources.md).  
  
 Dans XAML 2006 et WPF, `x:Key` doit être fourni en tant qu’attribut. Vous pouvez toujours utiliser des clés qui ne sont pas des chaînes, mais cela nécessite une utilisation d’extension de balisage afin de fournir la valeur de non-chaîne sous forme d’attribut. Si vous utilisez XAML 2009, `x:Key` peut être spécifié comme un élément, pour prendre en charge explicitement des dictionnaires indexés par des types d’objets autres que des chaînes sans nécessiter d’extension de balisage intermédiaire. Consultez la section « XAML 2009 » dans cette rubrique. Le reste de la section Remarques s’applique spécifiquement à l’implémentation XAML 2006.  
  
 La valeur d’attribut `x:Key` de peut être n’importe quelle chaîne définie dans la [grammaire XamlName](xamlname-grammar.md) ou peut être un objet évalué par le biais d’une extension de balisage. Consultez « Remarques sur l’utilisation de WPF » pour obtenir un exemple de WPF.  
  
 Les éléments enfants d’un élément parent qui est <xref:System.Collections.IDictionary> une implémentation doivent généralement inclure `x:Key` un attribut qui spécifie une valeur de clé unique dans ce dictionnaire. Les infrastructures peuvent implémenter des propriétés de clé avec alias `x:Key` pour remplacer sur des types particuliers ; les types qui définissent <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>de telles propriétés doivent être attribués avec.  
  
 Le code équivalent à la `x:Key` spécification est la clé utilisée pour le sous- <xref:System.Collections.IDictionary>jacent. Par exemple, un `x:Key` qui est appliqué dans le balisage pour une ressource dans WPF est équivalent à la valeur `key` du paramètre <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> de lorsque vous ajoutez la ressource à un <xref:System.Windows.ResourceDictionary> WPF dans le code.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 Les objets enfants d’un objet parent qui est <xref:System.Collections.IDictionary> une implémentation, tels que WPF <xref:System.Windows.ResourceDictionary>, doivent généralement inclure un `x:Key` attribut, et la valeur de clé doit être unique dans ce dictionnaire. Il existe deux exceptions notables :  
  
- Certains types WPF déclarent une clé implicite pour l’utilisation de dictionnaire. Par exemple, un <xref:System.Windows.Style> avec un <xref:System.Windows.Style.TargetType%2A>, ou un <xref:System.Windows.DataTemplate> avec un <xref:System.Windows.DataTemplate.DataType%2A>, peut être dans un <xref:System.Windows.ResourceDictionary> et utiliser la clé implicite.  
  
- WPF prend en charge un concept de dictionnaire de ressources fusionné. Les clés peuvent être partagées entre les dictionnaires fusionnés, et le comportement de la clé partagée <xref:System.Windows.FrameworkContentElement.FindResource%2A>est accessible à l’aide de. Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](../wpf/advanced/merged-resource-dictionaries.md).  
  
 Dans l’implémentation générale et le modèle d’application XAML WPF, l’unicité de la clé n’est pas vérifiée par le compilateur de balisage XAML. Au lieu de cela, les `x:Key` valeurs manquantes ou non uniques provoquent des erreurs de l’analyseur XAML au moment du chargement. Toutefois, la gestion de Visual Studio des dictionnaires pour WPF peut souvent noter de telles erreurs dans la phase de conception.  
  
 Notez que dans la syntaxe indiquée, l' <xref:System.Windows.ResourceDictionary> objet est implicite dans la manière dont le processeur XAML WPF produit une collection <xref:System.Windows.FrameworkElement.Resources%2A> pour remplir une collection. Un <xref:System.Windows.ResourceDictionary> n’est généralement pas fourni explicitement en tant qu’élément dans le balisage, bien qu’il puisse être dans certains cas souhaités pour plus de clarté (il s' <xref:System.Windows.FrameworkElement.Resources%2A> agit d’un élément objet de collection entre l’élément de propriété et les éléments dans qui remplissent le dictionnaire). Pour plus d’informations sur la raison pour laquelle un objet de collection est presque toujours un élément implicite dans le balisage, consultez [syntaxe XAML en détail](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 Dans l’implémentation XAML WPF, la gestion des clés de dictionnaire de ressources est définie <xref:System.Windows.ResourceKey> par la classe abstraite. Toutefois, le processeur XAML WPF produit des types d’extension sous-jacents différents pour les clés en fonction de leurs utilisations. Par exemple, la clé d’une <xref:System.Windows.DataTemplate> classe ou d’une classe dérivée est gérée séparément et <xref:System.Windows.DataTemplateKey> produit un objet distinct.  
  
 Les clés et les noms utilisent des directives et des`x:Key` éléments `x:Name`de langage différents (par rapport à) dans la définition XAML de base. Les clés et les noms sont également utilisés dans différentes situations par la définition WPF et l’application de ces concepts. Pour plus d’informations, consultez portées de [code XAML WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Comme indiqué précédemment, la valeur d’une clé peut être fournie par le biais d’une extension de balisage et peut être différente d’une valeur de chaîne. Un exemple de scénario WPF est que la valeur `x:Key` de peut être un [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Certains contrôles exposent une clé de style de ce type pour une ressource de style personnalisée qui influence une partie de l’apparence et du comportement de ce contrôle sans remplacer totalement le style. Un exemple d’une telle clé est <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 La fonctionnalité de dictionnaire fusionné WPF introduit des considérations supplémentaires pour l’unicité des clés et le comportement de recherche de clé. Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 assouplit la restriction qui `x:Key` est toujours fournie sous forme d’attribut.  
  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n’est pas compilé par balisage. Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 Sous XAML 2009, vous pouvez spécifier `x:Key` des éléments par le biais de l’utilisation suivante :  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Utilisation des éléments XAML (XAML 2009 uniquement)  
  
```  
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
  
- Le conteneur/parent de ce type d’utilisation n’est pas indiqué ici. `object`est supposé être un enfant d’un élément objet qui représente une implémentation de dictionnaire spécialisée. `keyObject`est supposé être une instance d’objet (ou une valeur d’un type valeur) qui est appropriée comme clé pour cette implémentation de dictionnaire spécialisé particulière.  
  
- WPF n’implémente pas les dictionnaires qui requièrent cette utilisation. Les clés d’objet sont plus une fonctionnalité générale du langage XAML, qui peut s’avérer utile pour certains scénarios de dictionnaires personnalisés où la création du dictionnaire en XAML est souhaitable. Pour les fonctionnalités WPF telles que les styles implicites qui utilisent des clés de non-chaîne pour les ressources, d’autres techniques permettant d’établir ou de spécifier les clés existent, l’utilisation d’une clé d’objet n’est donc pas nécessaire.  
  
- *keyObject* peut également être une utilisation d’extension de balisage dans un formulaire d’élément objet, plutôt qu’une instance d’objet directe.  
  
## <a name="silverlight-usage-notes"></a>Remarques sur l’utilisation de Silverlight  
 `x:Key`pour Silverlight est documenté séparément. Pour plus d’informations, [consultez espace de noms XAML (x:) Fonctionnalités de langage (Silverlight](https://go.microsoft.com/fwlink/?LinkId=199081)).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../wpf/advanced/xaml-resources.md)
- [Ressources et code](../wpf/advanced/resources-and-code.md)
- [StaticResource, extension de balisage](../wpf/advanced/staticresource-markup-extension.md)
