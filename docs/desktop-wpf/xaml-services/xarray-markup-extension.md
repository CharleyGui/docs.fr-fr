---
title: x:Array, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072045"
---
# <a name="xarray-markup-extension"></a>x:Array, extension de balisage

Fournit un support général pour les tableaux d’objets dans XAML grâce à une extension de balisage. Cela correspond au `x:ArrayExtension` type XAML dans [MS-XAML].

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`typeName`|Le nom du type `x:Array` que vous contiendra. `typeName`peut être (et est souvent) préfixé pour un espace de nom XAML qui contient les définitions de type XAML.|
|`arrayContents`|Le contenu des éléments qui `ArrayExtension.Items` est attribué à la propriété intrinsèque. En règle générale, ces éléments sont spécifiés `x:Array` comme un ou plusieurs éléments d’objet contenus dans les balises d’ouverture et de fermeture. Les objets spécifiés ici devraient être attribués au `typeName`type XAML spécifié dans .|

## <a name="remarks"></a>Notes

`Type`est un attribut `x:Array` requis pour tous les éléments d’objets. Une `Type` valeur de paramètre `x:Type` n’a pas besoin d’utiliser une extension de balisage; le nom court du type est un type XAML, qui peut être spécifié comme une chaîne.

Dans la mise en œuvre de .NET XAML Services, <xref:System.Type> la relation entre le type XAML d’entrée et le CLR de sortie du tableau créé est influencée par le contexte de service pour les extensions de balisage. La <xref:System.Type> sortie <xref:System.Xaml.XamlType.UnderlyingType%2A> est le type XAML d’entrée, après avoir examiné le <xref:System.Xaml.XamlType> <xref:System.Windows.Markup.IXamlTypeResolver> nécessaire en fonction du contexte schéma XAML et du service fourni par le contexte.

Lorsqu’il est traité, le `ArrayExtension.Items` contenu du tableau est attribué à la propriété intrinsèque. Dans <xref:System.Windows.Markup.ArrayExtension> la mise en œuvre, cela est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.

Dans la mise en œuvre de .NET XAML <xref:System.Windows.Markup.ArrayExtension> Services, le traitement de cette extension de balisage est défini par la classe. <xref:System.Windows.Markup.ArrayExtension>n’est pas scellé et pourrait servir de base à une mise en œuvre d’extension de balisage pour un type de tableau personnalisé.

`x:Array`est plus destiné à l’extéabilité générale de la langue dans XAML. Mais `x:Array` peut également être utile pour spécifier les valeurs XAML de certaines propriétés qui prennent XAML-soutenu collections comme leur contenu de propriété structurée. Par exemple, vous pouvez spécifier le contenu d’une <xref:System.Collections.IEnumerable> propriété avec une `x:Array` utilisation.

`x:Array` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. `x:Array`est en partie une exception à cette règle `x:Array` parce qu’au lieu de fournir une manipulation alternative de la valeur d’attribut, fournit la manipulation alternative de son contenu de texte intérieur. Ce comportement permet aux types qui pourraient ne pas être pris en charge par un modèle de contenu existant d’être regroupés dans un tableau et référencé plus tard dans le code-derrière en accédant à la grille nommée; vous pouvez <xref:System.Array> appeler des méthodes pour obtenir des éléments de tableau individuels.

Toutes les extensions de balisage dans{,} `)` XAML utilisent les accolades (dans leur syntaxe d’attribut, qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter la valeur d’attribut. Pour plus d’informations sur les extensions de balisage en général, voir [Les convertisseurs de type et extensions de balisage pour XAML](type-converters-and-markup-extensions.md).

Dans XAML 2009, `x:Array` est défini comme une langue primitive au lieu d’une extension de balisage. Pour plus d’informations, voir [Types intégrés pour les Primitifs en langue XAML communs](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Typiquement, les éléments d’objet qui peuplent un ne sont pas des `x:Array` éléments qui existent dans l’espace [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] de nom XAML, et nécessitent une cartographie préfixe à un espace de nom XAML non-défaut.

Par exemple, ce qui suit est un simple `sys` tableau de `x`deux cordes, avec le préfixe (et aussi ) défini au niveau du tableau.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Pour les types personnalisés qui sont utilisés comme éléments de tableau, la classe doit également prendre en charge les exigences pour être instantanée dans XAML comme éléments d’objet. Pour plus d’informations, voir [XAML et Custom Classes pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

## <a name="see-also"></a>Voir aussi

- [Extensions de balisage et XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Types migrés de WPF vers System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
