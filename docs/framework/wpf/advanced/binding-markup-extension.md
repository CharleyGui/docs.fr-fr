---
title: Binding, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: d0a437e756da16db978d8074c4355fd83d211b67
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453615"
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
 Dans ces syntaxes, les `[]` et `*` ne sont pas des littéraux. Elles font partie d’une notation indiquant qu’il est possible d’utiliser zéro, une ou plusieurs paires de valeurs *de`=`de* *valeur* , avec un séparateur de `,` entre elles et les paires de *valeurs* *bindProp*`=`.  
  
 Les propriétés énumérées dans la section « Propriétés de liaison qui peuvent être définies avec l’extension de liaison » peuvent être définies à la place à l’aide des attributs d’un élément objet <xref:System.Windows.Data.Binding>. Toutefois, il ne s’agit pas véritablement de l’utilisation de l’extension de balisage de <xref:System.Windows.Data.Binding>, il s’agit simplement du traitement XAML général des attributs qui définissent les propriétés de la classe CLR <xref:System.Windows.Data.Binding>. En d’autres termes, `<Binding` *bindProp1*`="`*value1*`"[` *bindPropN*`="`*ValueN*`"]*/>` est une syntaxe équivalente pour les attributs de <xref:System.Windows.Data.Binding> utilisation d’élément objet au lieu d’une utilisation d’expression `Binding`. Pour en savoir plus sur l’utilisation des attributs XAML des propriétés spécifiques de <xref:System.Windows.Data.Binding>, consultez la section « utilisation des attributs XAML » de la propriété appropriée de <xref:System.Windows.Data.Binding> dans la bibliothèque de classes .NET Framework.  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nom de la propriété <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.BindingBase> à définir. Toutes les propriétés de <xref:System.Windows.Data.Binding> ne peuvent pas être définies avec l’extension `Binding`, et certaines propriétés peuvent être définies dans une expression `Binding` uniquement à l’aide d’extensions de balisage imbriquées supplémentaires. Consultez la section « Propriétés de liaison qui peuvent être définies avec l’extension de liaison ».|  
|`value1, valueN`|Valeur à affecter à la propriété. La gestion de la valeur d’attribut est en définitive spécifique au type et à la logique de la propriété <xref:System.Windows.Data.Binding> spécifique qui est définie.|  
|`path`|Chaîne de chemin d’accès qui définit la propriété de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> implicite. Voir aussi [syntaxe XAML PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} non qualifié  
 L’utilisation `{Binding}` présentée dans « Binding expression usage » crée un objet <xref:System.Windows.Data.Binding> avec des valeurs par défaut, qui comprend une <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> initiale de `null`. Cela est toujours utile dans de nombreux scénarios, car le <xref:System.Windows.Data.Binding> créé peut s’appuyer sur des propriétés de liaison de données clés telles que <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> et <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> être défini dans le contexte de données d’exécution. Pour plus d’informations sur le concept de contexte de données, consultez [liaison de données](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Chemin d’accès implicite  
 L’extension de balisage `Binding` utilise <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> en tant que « propriété par défaut » conceptuelle, où `Path=` n’a pas besoin d’apparaître dans l’expression. Si vous spécifiez une expression `Binding` avec un chemin d’accès implicite, le chemin d’accès implicite doit apparaître en premier dans l’expression, avant tout autre `bindProp`=paires `value` où la propriété <xref:System.Windows.Data.Binding> est spécifiée par nom. Par exemple : `{Binding PathString}`, où `PathString` est une chaîne qui est évaluée comme étant la valeur de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> dans le <xref:System.Windows.Data.Binding> créé par l’utilisation d’une extension de balisage. Vous pouvez ajouter un chemin d’accès implicite à d’autres propriétés nommées après le séparateur de virgule, par exemple `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Propriétés de liaison qui peuvent être définies avec l’extension de liaison  
 La syntaxe présentée dans cette rubrique utilise le `bindProp`générique =`value` approximation, car il existe de nombreuses propriétés de lecture/écriture de <xref:System.Windows.Data.BindingBase> ou de <xref:System.Windows.Data.Binding> qui peuvent être définies via la syntaxe d’expression ou d’extension de balisage `Binding`. Elles peuvent être définies dans n’importe quel ordre, à l’exception d’une <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>implicite. (Vous avez la possibilité de spécifier explicitement `Path=`, auquel cas elle peut être définie dans n’importe quel ordre). En fait, vous pouvez définir zéro, une ou plusieurs des propriétés dans la liste ci-dessous, en utilisant des paires de `bindProp`=`value` séparées par des virgules.  
  
 Plusieurs de ces valeurs de propriété requièrent des types d’objet qui ne prennent pas en charge une conversion de type native à partir d’une syntaxe de texte en XAML, et nécessitent donc des extensions de balisage pour être définies en tant que valeur d’attribut. Pour plus d’informations, consultez la section utilisation des attributs XAML dans la bibliothèque de classes .NET Framework pour chaque propriété. la chaîne que vous utilisez pour la syntaxe d’attribut XAML avec ou sans l’utilisation de l’extension de balisage est fondamentalement la même que la valeur que vous spécifiez dans une expression `Binding`, à l’exception du fait que vous ne placez pas de guillemets autour de chaque `bindProp`=`value` dans expression `Binding`.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: chaîne qui identifie un groupe de liaisons possible. Il s’agit d’un concept de liaison relativement avancé. consultez la page de référence pour <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`,  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: peut être défini en tant que `bindProp`=`value` chaîne dans l’expression, mais pour ce faire, requiert une référence d’objet pour la valeur, telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md). La valeur dans ce cas est une instance d’une classe de convertisseur personnalisée.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: définissable dans l’expression comme identificateur basé sur des normes ; pour <xref:System.Windows.Data.Binding.ConverterCulture%2A>, consultez la rubrique de référence.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: peut être défini en tant que `bindProp`=`value` chaîne dans l’expression, mais cela dépend du type du paramètre passé. En cas de passage d’un type référence pour la valeur, cette utilisation requiert une référence d’objet telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md)imbriquée.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: s’exclut mutuellement contre <xref:System.Windows.Data.Binding.RelativeSource%2A> et <xref:System.Windows.Data.Binding.Source%2A>; chacune de ces propriétés de liaison représente une méthodologie de liaison particulière. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: peut être défini en tant que `bindProp`=`value` chaîne dans l’expression, mais cela dépend du type de la valeur passée. En cas de passage d’un type référence, requiert une référence d’objet telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md)imbriquée.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`,  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *value* est un nom de constante de l’énumération <xref:System.Windows.Data.BindingMode>. Par exemple, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`,  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`,  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`,  
  
- <xref:System.Windows.Data.Binding.Path%2A>: chaîne qui décrit un chemin d’accès dans un objet de données ou un modèle objet général. Le format fournit plusieurs conventions différentes pour parcourir un modèle objet qui ne peuvent pas être décrites de manière appropriée dans cette rubrique. Consultez [syntaxe XAML PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: s’exclut mutuellement par rapport à <xref:System.Windows.Data.Binding.ElementName%2A> et <xref:System.Windows.Data.Binding.Source%2A>; chacune de ces propriétés de liaison représente une méthodologie de liaison particulière. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données. Requiert une utilisation de [RelativeSource MarkupExtension](relativesource-markupextension.md) imbriquée pour spécifier la valeur.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: s’exclut mutuellement contre <xref:System.Windows.Data.Binding.RelativeSource%2A> et <xref:System.Windows.Data.Binding.ElementName%2A>; chacune de ces propriétés de liaison représente une méthodologie de liaison particulière. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données. Requiert une utilisation d’extension imbriquée, en général une [extension de balisage StaticResource](staticresource-markup-extension.md) qui fait référence à une source de données d’objet à partir d’un dictionnaire de ressources de clé.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: chaîne qui décrit une convention de format de chaîne pour les données liées. Il s’agit d’un concept de liaison relativement avancé. consultez la page de référence pour <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: peut être défini en tant que `bindProp`=`value` chaîne dans l’expression, mais cela dépend du type du paramètre passé. En cas de passage d’un type référence pour la valeur, requiert une référence d’objet telle qu’une [extension de balisage StaticResource](staticresource-markup-extension.md)imbriquée.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *value* est un nom de constante de l’énumération <xref:System.Windows.Data.UpdateSourceTrigger>. Par exemple, `{Binding UpdateSourceTrigger=LostFocus}`. Des contrôles spécifiques peuvent avoir des valeurs par défaut différentes pour cette propriété de liaison. Consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`, Consultez la section Notes.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, peut être `true` ou `false`. La valeur par défaut est `false`, Consultez la section Notes.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: chaîne qui décrit un chemin d’accès dans le XMLDOM d’une source de données XML. Consultez [lier à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Voici les propriétés de <xref:System.Windows.Data.Binding> qui ne peuvent pas être définies à l’aide de l’extension de balisage `Binding`/`{Binding}` formulaire d’expression.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: cette propriété attend une référence à une implémentation de rappel. Les rappels/méthodes autres que les gestionnaires d’événements ne peuvent pas être référencés dans la syntaxe XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: la propriété prend une collection générique d’objets <xref:System.Windows.Controls.ValidationRule>. Cela peut être exprimé comme un élément de propriété dans un élément objet <xref:System.Windows.Data.Binding>, mais n’a pas de technique d’analyse d’attributs facilement disponible pour l’utilisation dans une expression `Binding`. Consultez la rubrique de référence pour <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> En termes de priorité des propriétés de dépendance, une expression `Binding` est équivalente à une valeur définie localement. Si vous définissez une valeur locale pour une propriété qui avait précédemment une expression `Binding`, la `Binding` est complètement supprimée. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 La description de la liaison de données à un niveau de base n’est pas traitée dans cette rubrique. Consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding> et <xref:System.Windows.Data.PriorityBinding> ne prennent pas en charge une syntaxe d’extension de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Au lieu de cela, vous devez utiliser des éléments de propriété. Consultez les rubriques de référence pour <xref:System.Windows.Data.MultiBinding> et <xref:System.Windows.Data.PriorityBinding>.  
  
 Les valeurs booléennes pour XAML ne respectent pas la casse. Par exemple, vous pouvez spécifier `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 Les liaisons qui impliquent la validation des données sont généralement spécifiées par un élément `Binding` explicite plutôt que comme une expression `{Binding ...}`, et la définition de <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ou <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> dans une expression est rare. Cela est dû au fait que la propriété associée <xref:System.Windows.Data.Binding.ValidationRules%2A> ne peut pas être définie facilement dans le formulaire d’expression. Pour plus d’informations, consultez [implémenter la validation de liaison](../data/how-to-implement-binding-validation.md).  
  
 `Binding` est une extension de balisage. Les extensions de balisage sont généralement implémentées lorsqu’il est nécessaire d’échapper des valeurs d’attribut pour qu’elles soient autres que des valeurs littérales ou des noms de gestionnaire, et que la spécification soit plus globale que les convertisseurs de type attribués sur certains types ou propriétés. Toutes les extensions de balisage en XAML utilisent les caractères `{` et `}` dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter le contenu de la chaîne. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding` est une extension de balisage atypique en ce que la classe <xref:System.Windows.Data.Binding> qui implémente la fonctionnalité d’extension pour l’implémentation XAML de WPF implémente également plusieurs autres méthodes et propriétés qui ne sont pas liées à XAML. Les autres membres sont destinés à faire <xref:System.Windows.Data.Binding> une classe plus polyvalente et autonome qui peut traiter de nombreux scénarios de liaison de données en plus de fonctionner comme une extension de balisage XAML.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
