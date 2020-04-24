---
title: Binding, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: c6a424e085c7499db08d0a7e6b652f45fb2cdd70
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644083"
---
# <a name="binding-markup-extension"></a>Binding, extension de balisage
Reporte une valeur de propriété à une valeur liée aux données, créant un objet d’expression intermédiaire et interprétant le contexte de données qui s’applique à l’élément et à sa liaison au moment de l’exécution.  
  
## <a name="binding-expression-usage"></a>Utilisation de l’expression contraignante  
  
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
  
## <a name="syntax-notes"></a>Syntax Notes  
 Dans ces syntaxes, les `[]` et `*` ne sont pas littérales. Ils font partie d’une notation pour indiquer que zéro ou `,` plus *bindLes*`=`paires de*valeurprop* peuvent être utilisées, avec un séparateur entre eux et les paires de*valeur* *bindProp*`=`précédentes.  
  
 Toutes les propriétés énumérées dans la section « Propriétés contraignantes qui peuvent être <xref:System.Windows.Data.Binding> définies avec l’extension de liaison » pourraient plutôt être définies à l’aide d’attributs d’un élément d’objet. Cependant, ce n’est pas vraiment <xref:System.Windows.Data.Binding>l’utilisation de l’extension de balisage de , <xref:System.Windows.Data.Binding> c’est juste le traitement général XAML des attributs qui fixent les propriétés de la classe CLR. En `<Binding` d’autres termes, *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valueN* `"]*/>` <xref:System.Windows.Data.Binding> est une syntaxe équivalente pour les attributs de l’utilisation des éléments d’objet au lieu d’une `Binding` utilisation d’expression. Pour en savoir plus sur l’utilisation <xref:System.Windows.Data.Binding>de l’attribut XAML de propriétés <xref:System.Windows.Data.Binding> spécifiques de , voir la section "XAML Attribute Use" de la propriété pertinente de dans la bibliothèque de classe-cadre .NET.  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Le nom <xref:System.Windows.Data.Binding> de <xref:System.Windows.Data.BindingBase> la propriété à définir. Toutes <xref:System.Windows.Data.Binding> les propriétés ne `Binding` peuvent pas être définies `Binding` avec l’extension, et certaines propriétés ne sont définies dans une expression qu’en utilisant d’autres extensions de balisage imbriquées. Voir la section « Propriétés contraignantes qui peuvent être définies avec l’extension de liaison ».|  
|`value1, valueN`|Valeur à attribuer à la propriété. La manipulation de la valeur d’attribut est en <xref:System.Windows.Data.Binding> fin de compte spécifique au type et à la logique de la propriété spécifique en cours d’ensemble.|  
|`path`|La chaîne de chemin <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> qui définit la propriété implicite. Voir aussi [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Non qualifié de «liaison»  
 L’utilisation `{Binding}` indiquée dans "Binding <xref:System.Windows.Data.Binding> Expression Use" crée un <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null`objet avec des valeurs par défaut, qui comprend une initiale de . Ceci est encore utile dans de <xref:System.Windows.Data.Binding> nombreux scénarios, car les créations pourraient s’appuyer sur des propriétés clés de liaison de données telles que <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> et <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> être définies dans le contexte des données en temps d’exécution. Pour plus d’informations sur le concept de contexte de données, voir [Data Binding](../../../desktop-wpf/data/data-binding-overview.md).  
  
## <a name="implicit-path"></a>Chemin implicite  
 L’extension `Binding` de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> balisage sert de `Path=` « propriété par défaut » conceptuelle, où elle n’a pas besoin d’apparaître dans l’expression. Si vous `Binding` spécifiez une expression avec un chemin implicite, le `bindProp` = `value` chemin <xref:System.Windows.Data.Binding> implicite doit apparaître en premier dans l’expression, avant toute autre paire où la propriété est spécifiée par son nom. Par `{Binding PathString}`exemple: `PathString` , où est une chaîne qui <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> est <xref:System.Windows.Data.Binding> évaluée pour être la valeur de dans le créé par l’utilisation de l’extension de balisage. Vous pouvez ajouter un chemin implicite avec d’autres propriétés `{Binding LastName, Mode=TwoWay}`nommées d’après le séparateur de virgule, par exemple, .  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Propriétés contraignantes qui peuvent être définies avec l’extension de liaison  
 La syntaxe montrée dans `bindProp` = `value` ce sujet utilise l’approximation générique, <xref:System.Windows.Data.Binding> parce qu’il `Binding` y a beaucoup de propriétés de lecture/écriture de <xref:System.Windows.Data.BindingBase> ou qui peuvent être définies par l’extension de balisage / syntaxe d’expression. Ils peuvent être fixés dans n’importe <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>quel ordre, à l’exception d’un implicite . (Vous avez la possibilité `Path=`de spécifier explicitement, auquel cas il peut être défini dans n’importe quel ordre). Fondamentalement, vous pouvez définir zéro ou plus des `bindProp` = `value` propriétés dans la liste ci-dessous, en utilisant des paires séparées par des virgules.  
  
 Plusieurs de ces valeurs de propriété exigent des types d’objets qui ne supportent pas une conversion de type indigène à partir d’une syntaxe de texte dans XAML, et exigent donc des extensions de balisage pour être définis comme valeur d’attribut. Consultez la section utilisation des attributs XAML dans la bibliothèque de classe-cadre .NET pour chaque propriété pour plus d’informations; la chaîne que vous utilisez pour la syntaxe d’attribut XAML avec ou `Binding` sans autre utilisation d’extension de balisage `bindProp` = `value` est `Binding` fondamentalement la même que la valeur que vous spécifiez dans une expression, à l’exception que vous ne placez pas de guillemets autour de chacun dans l’expression.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: une chaîne qui identifie un groupe de liaison possible. Il s’agit d’un concept contraignant relativement avancé; voir la <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>page de référence pour .  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: peut être `bindProp` = `value` défini comme une chaîne dans l’expression, mais pour ce faire nécessite une référence d’objet pour la valeur, telle qu’une [extension de Markup StaticResource](staticresource-markup-extension.md). La valeur dans ce cas est un cas d’une classe de convertisseur personnalisé.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: défini dans l’expression comme un identifiant basé sur des normes; voir le sujet <xref:System.Windows.Data.Binding.ConverterCulture%2A>de référence pour .  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: peut être `bindProp` = `value` défini comme une corde dans l’expression, mais cela dépend du type de paramètre passé. Si vous passez un type de référence pour la valeur, cette utilisation nécessite une référence d’objet comme une [extension de balisage statique recoupée](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: mutuellement exclusive <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding.Source%2A>contre et ; chacune de ces propriétés contraignantes représente une méthodologie contraignante particulière. Voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: peut être `bindProp` = `value` défini comme une corde dans l’expression, mais cela dépend du type de valeur passée. Si vous passez un type de référence, nécessite une référence d’objet comme une [extension de markup statique imbriquée](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *la valeur* est <xref:System.Windows.Data.BindingMode> un nom constant de l’énumération. Par exemple : `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: une chaîne qui décrit un chemin dans un objet de données ou un modèle d’objet général. Le format fournit plusieurs conventions différentes pour traverser un modèle d’objet qui ne peut pas être décrit adéquatement dans ce sujet. Voir [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuellement exclusive <xref:System.Windows.Data.Binding.ElementName%2A> contre <xref:System.Windows.Data.Binding.Source%2A>et ; chacune de ces propriétés contraignantes représente une méthodologie contraignante particulière. Voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md). Nécessite une utilisation imbriquée [relative de MarkupExtension](relativesource-markupextension.md) pour spécifier la valeur.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: mutuellement exclusive <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding.ElementName%2A>contre et ; chacune de ces propriétés contraignantes représente une méthodologie contraignante particulière. Voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md). Nécessite une utilisation d’extension imbriquée, généralement une [extension de Markup StaticResource](staticresource-markup-extension.md) qui se réfère à une source de données d’objet à partir d’un dictionnaire de ressources clés.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: une chaîne qui décrit une convention de format de chaîne pour les données liées. Il s’agit d’un concept contraignant relativement avancé; voir la <xref:System.Windows.Data.BindingBase.StringFormat%2A>page de référence pour .  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: peut être `bindProp` = `value` défini comme une corde dans l’expression, mais cela dépend du type de paramètre passé. Si l’adoption d’un type de référence pour la valeur, nécessite une référence d’objet tel qu’une [extension de balisage statique recoupée](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *la valeur* est <xref:System.Windows.Data.UpdateSourceTrigger> un nom constant de l’énumération. Par exemple : `{Binding UpdateSourceTrigger=LostFocus}`. Les contrôles spécifiques ont potentiellement des valeurs de défaut différentes pour cette propriété contraignante. Consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`. Consultez la section Notes.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, peut `true` `false`être soit ou . Par défaut, il s’agit de `false`. Consultez la section Notes.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: une chaîne qui décrit un chemin dans le XMLDOM d’une source de données XML. Voir [Bind to XML Data À l’aide d’un XMLDataProvider et XPath Queries](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Ce qui suit <xref:System.Windows.Data.Binding> sont des propriétés qui ne peuvent pas être définies en utilisant l’extension `Binding` de balisage /`{Binding}` formulaire d’expression.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: cette propriété s’attend à une référence à une mise en œuvre de rappel. Les rappels/méthodes autres que les gestionnaires d’événements ne peuvent pas être référencés dans la syntaxe XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: la propriété prend <xref:System.Windows.Controls.ValidationRule> une collection générique d’objets. Cela pourrait être exprimé comme <xref:System.Windows.Data.Binding> un élément de propriété dans un élément d’objet, `Binding` mais n’a pas facilement disponible attribut-analyse technique pour l’utilisation dans une expression. Voir le <xref:System.Windows.Data.Binding.ValidationRules%2A>sujet de référence pour .  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
> En termes de préséance foncière, une `Binding` expression équivaut à une valeur fixée localement. Si vous définissez une valeur locale `Binding` pour une `Binding` propriété qui avait auparavant une expression, la est complètement supprimée. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).  
  
 La description de la liaison des données à un niveau de base n’est pas abordée dans ce sujet. Voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>et <xref:System.Windows.Data.PriorityBinding> ne supportent pas une syntaxe d’extension. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Vous utiliseriez plutôt des éléments de propriété. Voir les <xref:System.Windows.Data.MultiBinding> sujets <xref:System.Windows.Data.PriorityBinding>de référence pour et .  
  
 Les valeurs boolean pour XAML sont insensibles. Par exemple, vous `{Binding NotifyOnValidationError=true}` `{Binding NotifyOnValidationError=True}`pouvez spécifier l’un ou l’autre ou .  
  
 Les liaisons qui impliquent la `Binding` validation des données `{Binding ...}` sont généralement <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> spécifiées par un élément explicite plutôt que comme une expression, et le réglage ou dans une expression est rare. C’est parce <xref:System.Windows.Data.Binding.ValidationRules%2A> que la propriété compagnon ne peut pas être facilement mis sous la forme d’expression. Pour plus d’informations, voir [Implement Binding Validation](../data/how-to-implement-binding-validation.md).  
  
 `Binding` est une extension de balisage. Les extensions de majoration sont généralement mises en œuvre lorsqu’il est nécessaire d’échapper aux valeurs d’attributs pour être autres que des valeurs littérales ou des noms de gestionnaire, et l’exigence est plus globale que les convertisseurs de type attribués sur certains types ou propriétés. Toutes les extensions de balisage `}` dans XAML utilisent le et les `{` caractères dans leur syntaxe attribut, qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter le contenu de la chaîne. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`est une extension atypique de balisage en ce que la <xref:System.Windows.Data.Binding> classe qui implémente la fonctionnalité d’extension pour la mise en œuvre XAML de WPF implémente également plusieurs autres méthodes et propriétés qui ne sont pas liées à XAML. Les autres membres sont <xref:System.Windows.Data.Binding> destinés à faire une classe plus polyvalente et autonome qui peut répondre à de nombreux scénarios de liaison de données en plus de fonctionner comme une extension de balisage XAML.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
