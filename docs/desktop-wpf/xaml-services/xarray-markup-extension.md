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
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555170"
---
# <a name="xarray-markup-extension"></a>x:Array, extension de balisage

Fournit la prise en charge générale des tableaux d’objets en XAML par le biais d’une extension de balisage. Cela correspond au `x:ArrayExtension` type XAML dans [MS-XAML].

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`typeName`|Nom du type que votre `x:Array` contiendra. `typeName` peut être (et est souvent) préfixé pour un espace de noms XAML qui contient les définitions de type XAML.|
|`arrayContents`|Contenu des éléments qui est assigné à la `ArrayExtension.Items` propriété intrinsèque. En règle générale, ces éléments sont spécifiés sous la forme d’un ou plusieurs éléments objet contenus dans les `x:Array` balises d’ouverture et de fermeture. Les objets spécifiés ici sont censés être assignés au type XAML spécifié dans `typeName` .|

## <a name="remarks"></a>Notes

`Type` est un attribut requis pour tous les `x:Array` éléments objet. Une `Type` valeur de paramètre n’a pas besoin d’utiliser une `x:Type` extension de balisage ; le nom abrégé du type est un type XAML, qui peut être spécifié sous la forme d’une chaîne.

Dans l’implémentation des services XAML .NET, la relation entre le type XAML d’entrée et le CLR <xref:System.Type> de sortie du tableau créé est influencée par le contexte de service pour les extensions de balisage. La sortie <xref:System.Type> est le <xref:System.Xaml.XamlType.UnderlyingType%2A> du type XAML d’entrée, après avoir cherché le nécessaire <xref:System.Xaml.XamlType> en fonction du contexte de schéma XAML et du <xref:System.Windows.Markup.IXamlTypeResolver> service fourni par le contexte.

Lorsqu’il est traité, le contenu du tableau est affecté à la `ArrayExtension.Items` propriété intrinsèque. Dans l' <xref:System.Windows.Markup.ArrayExtension> implémentation, il est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> .

Dans l’implémentation des services XAML .NET, la gestion de cette extension de balisage est définie par la <xref:System.Windows.Markup.ArrayExtension> classe. <xref:System.Windows.Markup.ArrayExtension> n’est pas sealed et peut être utilisé comme base pour une implémentation d’extension de balisage pour un type de tableau personnalisé.

`x:Array` est plus destiné à l’extensibilité de langage générale en XAML. Mais `x:Array` peut également être utile pour spécifier des valeurs XAML de certaines propriétés qui prennent des collections prises en charge en XAML comme contenu de propriété structurée. Par exemple, vous pouvez spécifier le contenu d’une <xref:System.Collections.IEnumerable> propriété avec une `x:Array` utilisation.

`x:Array` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. `x:Array` est partiellement une exception à cette règle, car au lieu de fournir une autre gestion des valeurs d’attribut, `x:Array` fournit une autre gestion de son contenu de texte interne. Ce comportement permet aux types qui ne sont pas pris en charge par un modèle de contenu existant d’être regroupés dans un tableau et référencés ultérieurement dans le code-behind en accédant au tableau nommé ; vous pouvez appeler <xref:System.Array> des méthodes pour récupérer des éléments de tableau individuels.

Toutes les extensions de balisage en XAML utilisent les accolades ( {,} `)` dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter la valeur d’attribut. Pour plus d’informations sur les extensions de balisage en général, consultez [convertisseurs de type et extensions de balisage pour XAML](type-converters-and-markup-extensions.md).

En XAML 2009, `x:Array` est défini comme une primitive de langage au lieu d’une extension de balisage. Pour plus d’informations, consultez [types intégrés pour les primitives de langage XAML courantes](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

En général, les éléments objets qui remplissent un `x:Array` ne sont pas des éléments qui existent dans l' [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] espace de noms XAML et requièrent un mappage de préfixe à un espace de noms XAML non défini par défaut.

Par exemple, le code suivant est un tableau simple de deux chaînes, avec le `sys` préfixe (et également `x` ) défini au niveau du tableau.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Pour les types personnalisés utilisés comme éléments de tableau, la classe doit également prendre en charge les spécifications pour être instanciées en XAML en tant qu’éléments objet. Pour plus d’informations, consultez [XAML et classes personnalisées pour WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).

## <a name="see-also"></a>Voir aussi

- [Extensions de balisage et XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [Types migrés de WPF vers System.Xaml](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
