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
ms.openlocfilehash: 8acb732841aa7aaaad3e8fdd2cf2962ff44dd60b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506062"
---
# <a name="xarray-markup-extension"></a>x:Array, extension de balisage
Fournit la prise en charge générale pour les tableaux d’objets dans XAML via une extension de balisage. Cela correspond à la `x:ArrayExtension` type XAML dans [MS-XAML].  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xaml
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`typeName`|Le nom du type qui votre `x:Array` contiendra. `typeName` peut être (et est souvent) préfixé pour un XAML définitions de type espace de noms qui contient le XAML.|  
|`arrayContents`|Le contenu d’éléments est affecté à la fonction intrinsèque `ArrayExtension.Items` propriété. En règle générale, ces éléments sont spécifiés en tant qu’un ou plusieurs éléments objet contenus dans le `x:Array` balises. Les objets spécifiés ici sont censées être attribuable au type XAML spécifié dans `typeName`.|  
  
## <a name="remarks"></a>Notes  
 `Type` est un attribut requis pour tous les `x:Array` éléments objet. Un `Type` valeur du paramètre n’a pas besoin d’utiliser un `x:Type` extension de balisage ; court nom du type est un type XAML, qui peut être spécifié sous forme de chaîne.  
  
 Dans l’implémentation de Services XAML du .NET Framework, la relation entre le type XAML d’entrée et la sortie CLR <xref:System.Type> du tableau créé est influencée par le contexte de service pour les extensions de balisage. La sortie <xref:System.Type> est la <xref:System.Xaml.XamlType.UnderlyingType%2A> du type XAML d’entrée, après avoir recherché le nécessaire <xref:System.Xaml.XamlType> selon le contexte de schéma XAML et le <xref:System.Windows.Markup.IXamlTypeResolver> fournit le contexte de service.  
  
 Lors du traitement, le contenu du tableau est affecté à la `ArrayExtension.Items` propriété intrinsèque. Dans le <xref:System.Windows.Markup.ArrayExtension> implémentation, ceci est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 Dans l’implémentation de Services XAML du .NET Framework, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Markup.ArrayExtension> classe. <xref:System.Windows.Markup.ArrayExtension> n’est pas scellé et peut être utilisé comme base pour une implémentation d’extension de balisage pour un type de tableau personnalisé.  
  
 `x:Array` est que plus destiné au grand extensibilité de langage dans XAML. Mais `x:Array` peut également être utile pour spécifier des valeurs XAML de certaines propriétés qui prennent des collections pris en charge de XAML en tant que contenu de propriété structuré. Par exemple, vous pouvez spécifier le contenu d’un <xref:System.Collections.IEnumerable> propriété avec une `x:Array` l’utilisation.  
  
 `x:Array` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. `x:Array` est partiellement une exception à cette règle, car au lieu de fournir un traitement de valeur d’attribut de remplacement, `x:Array` fournit un autre traitement de son contenu de texte interne. Ce comportement permet aux types qui ne peuvent pas être pris en charge par un modèle de contenu existant d’être regroupés en un tableau et référencés plus loin dans le code-behind en accédant au tableau nommé ; Vous pouvez appeler <xref:System.Array> méthodes pour obtenir les éléments de tableau individuels.  
  
 Toutes les extensions de balisage dans XAML utilisent les accolades ({,} `)` dans leur syntaxe d’attribut, qui est la convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter la valeur d’attribut. Pour plus d’informations sur les extensions de balisage en général, consultez [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Dans XAML 2009, `x:Array` est défini en tant que langage primitif au lieu d’une extension de balisage. Pour plus d’informations, consultez [Types intégrés pour les Primitives de langage XAML commun](built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation WPF  
 En règle générale, les éléments objet qui remplissent un `x:Array` ne sont pas des éléments qui existent dans le [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] espace de noms XAML et requièrent un mappage de préfixe à un espace de noms XAML par défaut.  
  
 Par exemple, Voici un tableau simple de deux chaînes, avec le `sys` préfixe (et également `x`) définis au niveau du tableau.  
  
```xaml
<x:Array Type="sys:String"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:sys="clr-namespace:System;assembly=mscorlib">
    <sys:String>Hello</sys:String>
    <sys:String>World</sys:String>
</x:Array>
```
  
 Pour les types personnalisés qui sont utilisés comme éléments de tableau, la classe doit également en charge la configuration requise pour instanciée en XAML en tant qu’éléments de l’objet. Pour plus d’informations, consultez [XAML et Classes personnalisées pour WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- [Extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
