---
title: Binding, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 6776c89db474668b3aed0e38a3e18359bf93399d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991481"
---
# <a name="binding-markup-extension"></a>Binding, extension de balisage
Diffère une valeur de propriété comme une valeur liée aux données, en créant un objet d’expression intermédiaire et en interprétant le contexte de données qui s’applique à l’élément et à sa liaison au moment de l’exécution.  
  
## <a name="binding-expression-usage"></a>Utilisation des expressions de liaison  
  
```xaml  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Remarques sur la syntaxe  
 Dans ces syntaxes, `[]` et `*` ne sont pas des littéraux. Elles font partie d’une notation pour indiquer qu’aucune ou plusieurs`=`paires de*valeurs* bindProp peuvent être utilisées, avec `,` un séparateur entre elles et les paires de*valeurs* *bindProp*`=`précédentes.  
  
 Toutes les propriétés listées dans la section « Propriétés de liaison qui peuvent être définies avec l’extension de liaison » peuvent être définies à la place à <xref:System.Windows.Data.Binding> l’aide des attributs d’un élément objet. Toutefois, il ne s’agit pas véritablement de l’utilisation <xref:System.Windows.Data.Binding>de l’extension de balisage de, il s’agit simplement du traitement XAML général <xref:System.Windows.Data.Binding> des attributs qui définissent les propriétés de la classe CLR. En d’autres termes `<Binding` , *bindProp1*`="`*value1* `"[` <xref:System.Windows.Data.Binding> *bindPropN* *ValueN* est une syntaxe équivalente pour les attributs d’utilisation d’élément objet`"]*/>` `="` au lieu d' `Binding` une utilisation d’expression. Pour en savoir plus sur l’utilisation des attributs XAML des <xref:System.Windows.Data.Binding>propriétés spécifiques de, consultez la section « utilisation des attributs XAML » de <xref:System.Windows.Data.Binding> la propriété appropriée de dans la bibliothèque de classes .NET Framework.  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nom de la <xref:System.Windows.Data.Binding> propriété ou <xref:System.Windows.Data.BindingBase> à définir. Toutes <xref:System.Windows.Data.Binding> les propriétés ne peuvent pas être définies `Binding` avec l’extension, et certaines propriétés peuvent être `Binding` définies dans une expression uniquement à l’aide d’extensions de balisage imbriquées supplémentaires. Consultez la section « Propriétés de liaison qui peuvent être définies avec l’extension de liaison ».|  
|`value1, valueN`|Valeur à attribuer à la propriété. La gestion de la valeur d’attribut est en définitive spécifique au type et à la logique <xref:System.Windows.Data.Binding> de la propriété spécifique qui est définie.|  
|`path`|Chaîne de chemin d’accès qui définit <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> la propriété implicite. Voir aussi [syntaxe XAML PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} non qualifié  
 L' `{Binding}` utilisation indiquée dans « Binding expression usage » crée un <xref:System.Windows.Data.Binding> objet avec les valeurs par défaut, qui comprend <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> un `null`initial de. Cela est toujours utile dans de nombreux scénarios, car le <xref:System.Windows.Data.Binding> créé peut reposer sur des propriétés de liaison de données clés <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> telles <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> que et qui sont définies dans le contexte de données au moment de l’exécution. Pour plus d’informations sur le concept de contexte de données, consultez [liaison de données](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Chemin d’accès implicite  
 L' `Binding` extension de balisage utilise <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> comme « propriété par défaut » conceptuelle `Path=` , où ne doit pas apparaître dans l’expression. Si vous spécifiez `Binding` une expression avec un chemin d’accès implicite, le chemin d’accès implicite doit apparaître en premier `bindProp` dans l’expression <xref:System.Windows.Data.Binding> , avant toute autre = `value` paire où la propriété est spécifiée par nom. Par exemple : `{Binding PathString}`, où `PathString` est une chaîne qui est évaluée comme étant la valeur <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> de dans <xref:System.Windows.Data.Binding> le créé par l’utilisation d’une extension de balisage. Vous pouvez ajouter un chemin d’accès implicite avec d’autres propriétés nommées après le séparateur `{Binding LastName, Mode=TwoWay}`de virgules, par exemple.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Propriétés de liaison qui peuvent être définies avec l’extension de liaison  
 La syntaxe indiquée dans cette rubrique utilise la approximation `bindProp` générique <xref:System.Windows.Data.Binding> = `value` , car il existe de nombreuses propriétés de lecture/ <xref:System.Windows.Data.BindingBase> écriture de ou qui peuvent être définies `Binding` via l’extension de balisage/ syntaxe de l’expression. Ils peuvent être définis dans n’importe quel ordre, à l’exception d' <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>un implicite. (Vous avez la possibilité de spécifier `Path=`explicitement, auquel cas elle peut être définie dans n’importe quel ordre). En fait, vous pouvez définir zéro, une ou plusieurs des propriétés dans la liste ci `bindProp` -dessous, en utilisant = `value` des paires séparées par des virgules.  
  
 Plusieurs de ces valeurs de propriété requièrent des types d’objet qui ne prennent pas en charge une conversion de type native à partir d’une syntaxe de texte en XAML, et nécessitent donc des extensions de balisage pour être définies en tant que valeur d’attribut. Pour plus d’informations, consultez la section utilisation des attributs XAML dans la bibliothèque de classes .NET Framework pour chaque propriété. la chaîne que vous utilisez pour la syntaxe d’attribut XAML avec ou sans plus d’utilisation d’extension de balisage est fondamentalement identique à `Binding` la valeur que vous spécifiez dans une expression, à l’exception près `bindProp` que vous ne placez pas de guillemets autour de chaque =dans l' expression`Binding` . `value`  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: chaîne qui identifie un groupe de liaisons possible. Il s’agit d’un concept de liaison relativement avancé. consultez la page de <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>référence de.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: peut être défini en tant `bindProp` que = `value` chaîne dans l’expression, mais pour ce faire, requiert une référence d’objet pour la valeur, telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md). La valeur dans ce cas est une instance d’une classe de convertisseur personnalisée.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: définissable dans l’expression comme identificateur basé sur des normes ; consultez la rubrique de référence <xref:System.Windows.Data.Binding.ConverterCulture%2A>pour.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: peut être défini en tant `bindProp` que = `value` chaîne dans l’expression, mais il dépend du type du paramètre passé. En cas de passage d’un type référence pour la valeur, cette utilisation requiert une référence d’objet telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md)imbriquée.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: mutuellement exclusif par <xref:System.Windows.Data.Binding.RelativeSource%2A> rapport <xref:System.Windows.Data.Binding.Source%2A>à et ; chacune de ces propriétés de liaison représente une méthodologie de liaison particulière. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: peut être défini en tant `bindProp` que = `value` chaîne dans l’expression, mais il dépend du type de la valeur passée. En cas de passage d’un type référence, requiert une référence d’objet telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md)imbriquée.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: la *valeur* est un nom de constante <xref:System.Windows.Data.BindingMode> de l’énumération. Par exemple, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: chaîne qui décrit un chemin d’accès dans un objet de données ou un modèle objet général. Le format fournit plusieurs conventions différentes pour parcourir un modèle objet qui ne peuvent pas être décrites de manière appropriée dans cette rubrique. Consultez [syntaxe XAML PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuellement exclusif par rapport <xref:System.Windows.Data.Binding.ElementName%2A> à <xref:System.Windows.Data.Binding.Source%2A>et ; chacune de ces propriétés de liaison représente une méthodologie de liaison particulière. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données. Requiert une utilisation de [RelativeSource MarkupExtension](relativesource-markupextension.md) imbriquée pour spécifier la valeur.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: mutuellement exclusif par <xref:System.Windows.Data.Binding.RelativeSource%2A> rapport <xref:System.Windows.Data.Binding.ElementName%2A>à et ; chacune de ces propriétés de liaison représente une méthodologie de liaison particulière. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données. Requiert une utilisation d’extension imbriquée, en général une [extension de balisage StaticResource](staticresource-markup-extension.md) qui fait référence à une source de données d’objet à partir d’un dictionnaire de ressources de clé.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: chaîne qui décrit une convention de format de chaîne pour les données liées. Il s’agit d’un concept de liaison relativement avancé. consultez la page de <xref:System.Windows.Data.BindingBase.StringFormat%2A>référence de.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: peut être défini en tant `bindProp` que = `value` chaîne dans l’expression, mais il dépend du type du paramètre passé. En cas de passage d’un type référence pour la valeur, requiert une référence d’objet telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md)imbriquée.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: la *valeur* est un nom de constante <xref:System.Windows.Data.UpdateSourceTrigger> de l’énumération. Par exemple, `{Binding UpdateSourceTrigger=LostFocus}`. Des contrôles spécifiques peuvent avoir des valeurs par défaut différentes pour cette propriété de liaison. Consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`. Consultez la section Notes.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Booléen, peut être `true` ou. `false` Par défaut, il s’agit de `false`. Consultez la section Notes.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: chaîne qui décrit un chemin d’accès dans le XMLDOM d’une source de données XML. Consultez [lier à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Les propriétés suivantes ne peuvent <xref:System.Windows.Data.Binding> pas être définies à l’aide `Binding` du formulaire d'`{Binding}` extension de balisage/expression.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: cette propriété attend une référence à une implémentation de rappel. Les rappels/méthodes autres que les gestionnaires d’événements ne peuvent pas être référencés dans la syntaxe XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: la propriété prend une collection générique d' <xref:System.Windows.Controls.ValidationRule> objets. Cela peut être exprimé comme un élément de propriété dans <xref:System.Windows.Data.Binding> un élément objet, mais n’a pas de technique d’analyse d’attributs facilement disponible pour `Binding` une utilisation dans une expression. Consultez la rubrique de <xref:System.Windows.Data.Binding.ValidationRules%2A>référence pour.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> En termes de priorité des propriétés de dépendance `Binding` , une expression est équivalente à une valeur définie localement. Si vous définissez une valeur locale pour une propriété qui avait précédemment une `Binding` expression, le `Binding` est complètement supprimé. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 La description de la liaison de données à un niveau de base n’est pas traitée dans cette rubrique. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>et <xref:System.Windows.Data.PriorityBinding> ne prennent pas en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] charge une syntaxe d’extension. Au lieu de cela, vous devez utiliser des éléments de propriété. Consultez les rubriques de <xref:System.Windows.Data.MultiBinding> référence <xref:System.Windows.Data.PriorityBinding>pour et.  
  
 Les valeurs booléennes pour XAML ne respectent pas la casse. Par exemple, `{Binding NotifyOnValidationError=true}` vous pouvez spécifier ou `{Binding NotifyOnValidationError=True}`.  
  
 Les liaisons qui impliquent la validation des données sont généralement spécifiées par un élément `Binding` explicite `{Binding ...}` plutôt que comme une <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> expression <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> , et la définition ou dans une expression est rare. Cela est dû au fait que <xref:System.Windows.Data.Binding.ValidationRules%2A> la propriété associée ne peut pas être définie facilement dans le formulaire d’expression. Pour plus d’informations, consultez [implémenter la validation de liaison](../data/how-to-implement-binding-validation.md).  
  
 `Binding` est une extension de balisage. Les extensions de balisage sont généralement implémentées lorsqu’il est nécessaire d’échapper des valeurs d’attribut pour qu’elles soient autres que des valeurs littérales ou des noms de gestionnaire, et que la spécification soit plus globale que les convertisseurs de type attribués sur certains types ou propriétés. Toutes les extensions de balisage en `{` XAML `}` utilisent les caractères et dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter le contenu de la chaîne. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`est une extension de balisage atypique en <xref:System.Windows.Data.Binding> ce que la classe qui implémente les fonctionnalités d’extension pour l’implémentation XAML de WPF implémente également plusieurs autres méthodes et propriétés qui ne sont pas liées à XAML. Les autres membres sont conçus pour créer <xref:System.Windows.Data.Binding> une classe plus polyvalente et autonome qui peut traiter de nombreux scénarios de liaison de données en plus de fonctionner comme une extension de balisage XAML.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
