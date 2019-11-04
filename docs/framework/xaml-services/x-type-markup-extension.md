---
title: x:Type, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459915"
---
# <a name="xtype-markup-extension"></a>x:Type, extension de balisage
Fournit l’objet de <xref:System.Type> CLR qui est le type sous-jacent pour un type XAML spécifié.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`prefix`|Optionnel. Préfixe qui mappe un espace de noms XAML non défini par défaut. La spécification d’un préfixe n’est souvent pas nécessaire. Consultez la section Notes.|  
|`typeNameValue`|Requis. Nom de type pouvant être résolu dans l’espace de noms XAML par défaut actuel ; ou le préfixe mappé spécifié si `prefix` est fourni.|  
  
## <a name="remarks"></a>Notes  
 L’extension de balisage `x:Type` a une fonction similaire à l’opérateur C# `typeof()` dans ou à l’opérateur `GetType` dans Microsoft Visual Basic.  
  
 L’extension de balisage `x:Type` fournit un comportement de conversion à partir d’une chaîne pour les propriétés qui prennent le type <xref:System.Type>. L’entrée est un type XAML. La relation entre le type XAML d’entrée et le CLR de sortie <xref:System.Type> est que la <xref:System.Type> de sortie est la <xref:System.Xaml.XamlType.UnderlyingType%2A> du <xref:System.Xaml.XamlType>d’entrée, après avoir cherché les <xref:System.Xaml.XamlType> nécessaires en fonction du contexte de schéma XAML et du service de <xref:System.Windows.Markup.IXamlTypeResolver> fourni par le contexte.  
  
 Dans .NET Framework services XAML, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.TypeExtension>.  
  
 Dans les implémentations d’infrastructure spécifiques, certaines propriétés qui prennent <xref:System.Type> en tant que valeur peuvent accepter directement le nom du type (la valeur de chaîne du type `Name`). Toutefois, l’implémentation de ce comportement est un scénario complexe. Pour obtenir des exemples, consultez la section « Remarques sur l’utilisation de WPF » qui suit.  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `x:Type` est assigné en tant que valeur <xref:System.Windows.Markup.TypeExtension.TypeName%2A> de la classe d’extension <xref:System.Windows.Markup.TypeExtension> sous-jacente. Dans le contexte de schéma XAML par défaut pour les services XAML .NET Framework, qui est basé sur les types CLR, la valeur de cet attribut est soit le <xref:System.Reflection.MemberInfo.Name%2A> du type souhaité, soit contient ce <xref:System.Reflection.MemberInfo.Name%2A> précédé d’un préfixe pour un mappage d’espace de noms XAML non défini par défaut.  
  
 L’extension de balisage `x:Type` peut être utilisée dans la syntaxe d’élément objet. Dans ce cas, il est nécessaire de spécifier la valeur de la propriété <xref:System.Windows.Markup.TypeExtension.TypeName%2A> pour initialiser correctement l’extension.  
  
 L’extension de balisage `x:Type` peut également être utilisée en tant qu’attribut détaillé ; Toutefois, cette utilisation n’est pas courante : `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Mappage de type et espace de noms XAML par défaut  
 L’espace de noms XAML par défaut pour la programmation WPF contient la plupart des types XAML dont vous avez besoin pour les scénarios XAML standard. par conséquent, vous pouvez souvent éviter des préfixes lors du référencement de valeurs de type XAML. Vous devrez peut-être mapper un préfixe si vous référencez un type à partir d’un assembly personnalisé ou pour des types qui existent dans un assembly WPF, mais qu’ils proviennent d’un espace de noms CLR qui n’a pas été mappé à l’espace de noms XAML par défaut. Pour plus d’informations sur les préfixes, les espaces de noms XAML et le mappage des espaces de noms CLR, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Propriétés de type qui prennent en charge TypeName-As-String  
 WPF prend en charge les techniques qui permettent de spécifier la valeur de certaines propriétés de type <xref:System.Type> sans nécessiter une utilisation d’extension de balisage `x:Type`. Au lieu de cela, vous pouvez spécifier la valeur sous la forme d’une chaîne qui nomme le type. <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> et <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>en sont des exemples. La prise en charge de ce comportement n’est pas assurée par le biais de convertisseurs de type ou d’extensions de balisage. Au lieu de cela, il s’agit d’un comportement de report implémenté via <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight prend en charge une convention similaire. En fait, Silverlight ne prend pas actuellement en charge les `{x:Type}` dans sa prise en charge du langage XAML et n’accepte pas les utilisations `{x:Type}` en dehors de quelques circonstances, destinées à prendre en charge la migration XAML WPF-Silverlight. Par conséquent, le comportement de type TypeName-As-String est intégré à toutes les évaluations de propriétés natives Silverlight où un <xref:System.Type> est la valeur.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 fournit une prise en charge supplémentaire pour les types génériques et modifie le comportement des fonctionnalités de `x:TypeArguments` et `x:Type` pour fournir cette prise en charge.  
  
- `x:TypeArguments` et l’élément objet associé pour une instanciation d’objet générique peuvent se trouver sur des éléments autres que la racine. Pour plus d’informations, consultez la section « XAML 2009 » de [la directive x :TypeArguments](x-typearguments-directive.md).  
  
- XAML 2009 prend en charge une syntaxe pour spécifier la contrainte d’un type générique dans le balisage. Il peut être utilisé par `x:TypeArguments`, par `x:Type`ou par les deux fonctionnalités en combinaison.  
  
- L’implémentation XAML WPF lors du traitement du code XAML 2009 pour le chargement ajoute également cette fonctionnalité au comportement de conversion de type implicite pour certaines propriétés de l’infrastructure qui utilisent le type <xref:System.Type>.  
  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le XAML libre (XAML qui n’est pas compilé par balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Style>
- [Application d’un style et création de modèles](../wpf/controls/styling-and-templating.md)
- [Vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
