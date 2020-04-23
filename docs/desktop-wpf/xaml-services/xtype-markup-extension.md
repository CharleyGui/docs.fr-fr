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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071359"
---
# <a name="xtype-markup-extension"></a>x:Type, extension de balisage

Fournit l’objet CLR <xref:System.Type> qui est le type sous-jacent pour un type XAML spécifié.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

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
|`prefix`|facultatif. Un préfixe qui cartographie un espace de nom XAML non par défaut. Spécifier un préfixe n’est souvent pas nécessaire. Consultez la section Notes.|
|`typeNameValue`|Obligatoire. Un nom de type résolvable à l’espace de nom XAML par défaut actuel; ou le préfixe `prefix` cartographié spécifié s’il est fourni.|

## <a name="remarks"></a>Notes

L’extension `x:Type` de balisage `typeof()` a une fonction `GetType` similaire à celle de l’opérateur dans C ou l’opérateur de Microsoft Visual Basic.

L’extension `x:Type` de balisage fournit un comportement de <xref:System.Type>conversion à partir de la corde pour les propriétés qui prennent le type . L’entrée est un type XAML. La relation entre le type XAML <xref:System.Type> d’entrée <xref:System.Type> et <xref:System.Xaml.XamlType.UnderlyingType%2A> le CLR de sortie est que la sortie est l’entrée, <xref:System.Xaml.XamlType>après avoir examiné le nécessaire <xref:System.Xaml.XamlType> basé sur le contexte schéma XAML et le <xref:System.Windows.Markup.IXamlTypeResolver> service que le contexte fournit.

Dans .NET XAML Services, la manipulation de cette <xref:System.Windows.Markup.TypeExtension> extension de balisage est définie par la classe.

Dans des implémentations <xref:System.Type> de cadres spécifiques, certaines propriétés qui prennent comme `Name`valeur peuvent accepter directement le nom du type (la valeur de la chaîne du type). Cependant, la mise en œuvre de ce comportement est un scénario complexe. Pour des exemples, consultez la section « Notes d’utilisation du FMM » qui suit.

La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `x:Type` est assigné en tant que valeur <xref:System.Windows.Markup.TypeExtension.TypeName%2A> de la classe d’extension <xref:System.Windows.Markup.TypeExtension> sous-jacente. Dans le contexte de schéma XAML par défaut pour .NET XAML Services, qui est <xref:System.Reflection.MemberInfo.Name%2A> basé sur les types <xref:System.Reflection.MemberInfo.Name%2A> CLR, la valeur de cet attribut est soit le type souhaité, ou contient celui précédé d’un préfixe pour une cartographie sans défaut XAML namespace.

L’extension `x:Type` de balisage peut être utilisée dans la syntaxe d’élément d’objet. Dans ce cas, il est <xref:System.Windows.Markup.TypeExtension.TypeName%2A> nécessaire de préciser la valeur de la propriété pour initialiser correctement l’extension.

L’extension `x:Type` de balisage peut également être utilisée comme attribut verbeux; toutefois, cette utilisation n’est pas typique :`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

### <a name="default-xaml-namespace-and-type-mapping"></a>Par défaut XAML Namespace et Type Mapping

L’espace de nom XAML par défaut pour la programmation WPF contient la plupart des types XAML dont vous avez besoin pour des scénarios XAML typiques; par conséquent, vous pouvez souvent éviter les préfixes lors du référencement des valeurs de type XAML. Vous devrez peut-être cartographier un préfixe si vous faites référence à un type d’assemblage personnalisé ou pour les types qui existent dans un assemblage WPF, mais qui proviennent d’un espace de nom CLR qui n’a pas été cartographié pour l’espace de nom XAML par défaut. Pour plus d’informations sur les préfixes, les espaces nominaux XAML et la cartographie des espaces nominaux CLR, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

### <a name="type-properties-that-support-typename-as-string"></a>Propriétés de type qui prennent en charge Typename-as-String

WPF prend en charge les techniques qui <xref:System.Type> permettent de `x:Type` spécifier la valeur de certaines propriétés de type sans nécessiter une utilisation d’extension de balisage. Au lieu de cela, vous pouvez spécifier la valeur comme une chaîne qui nomme le type. Exemples de <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>ceci sont et . Le soutien à ce comportement n’est pas fourni par des convertisseurs de type ou des extensions de balisage. Au lieu de cela, il <xref:System.Windows.FrameworkElementFactory>s’agit d’un comportement de report mis en œuvre par .

Silverlight soutient une convention similaire. En fait, Silverlight ne `{x:Type}` prend pas actuellement en charge dans `{x:Type}` son support linguistique XAML, et n’accepte pas les utilisations en dehors de quelques circonstances qui sont destinées à soutenir la migration WPF-Silverlight XAML. Par conséquent, le comportement de typename-as-string est intégré à <xref:System.Type> toute évaluation de propriété indigène de Silverlight où un est la valeur.

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 fournit un support supplémentaire pour les `x:TypeArguments` `x:Type` types génériques et modifie le comportement des fonctionnalités et de fournir ce support.

- `x:TypeArguments`et l’élément objet associé pour une instantanéisation d’objet générique peut être sur des éléments autres que la racine. Pour plus d’informations, voir la section "XAML 2009" de [la directive x:TypeArguments](xtypearguments-directive.md).

- XAML 2009 prend en charge une syntaxe pour spécifier la contrainte d’un type générique dans la balisage. Cela peut être `x:TypeArguments`utilisé `x:Type`par , par , ou par les deux caractéristiques en combinaison.

- WPF XAML implémentation lors du traitement XAML 2009 pour la charge ajoute <xref:System.Type>également cette capacité au comportement implicite de conversion de type pour certaines propriétés-cadres qui utilisent le type .

Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009 mais uniquement pour XAML (XAML en vrac qui n’est pas compilée). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Style>
- [Application d’un style et création de modèles](../fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
