---
title: x:TypeArguments, directive
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071352"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments, directive

Passes de type de contrainte arguments d’un générique au constructeur du type générique.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`object`|Une déclaration d’élément d’objet d’un type XAML, qui est soutenue par un type générique CLR. Si `object` se réfère à un type XAML qui n’est `object` pas de l’espace nom XAML par défaut, nécessite un préfixe pour indiquer l’espace de nom XAML où `object` existe.|
|`typeString`|Une chaîne qui déclare un ou plusieurs noms de type XAML comme des chaînes, qui fournit les arguments de type pour le type générique CLR. Voir Remarques pour des notes de syntaxe supplémentaires.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, les types XAML `typeString` qui sont utilisés comme élément d’information dans une chaîne sont préfixés. Les types typiques de contraintes <xref:System.Int32> génériques CLR (par exemple, et <xref:System.String>) proviennent de bibliothèques de classe de base CLR. Ces bibliothèques ne sont pas cartographiées selon des espaces de noms XAML spécifiques au cadre typique et nécessitent donc une cartographie préfixe pour l’utilisation de XAML.

Vous pouvez spécifier plus d’un nom de type XAML en utilisant un délimit de virgule.

Si les contraintes génériques elles-mêmes utilisent des types génériques, les arguments de type contrainte imbriqués peuvent être contenus par parenthèses ().

Notez que `x:TypeArguments` cette définition est spécifique à .NET XAML Services et en utilisant le support CLR. Une définition du niveau de langue se trouve dans [ \[la section 5.3.11 de MS-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="usage-examples"></a>Exemples d’utilisation

Pour ces exemples, supposons que les définitions suivantes de l’espace de nom XAML sont déclarées :

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>Liste\<Des> de chaîne

`<scg:List x:TypeArguments="sys:String" ...>`instantanés un <xref:System.Collections.Generic.List%601> nouveau <xref:System.String> avec un argument de type.

### <a name="dictionarystringstring"></a>Chaîne\<de dictionnaire,> de chaîne

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`instantiates un <xref:System.Collections.Generic.Dictionary%602> nouveau <xref:System.String> avec deux types d’arguments.

### <a name="queuekeyvaluepairstringstring"></a>File d’attente<Chaîne\<KeyValuePair, String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`instantanés un <xref:System.Collections.Generic.Queue%601> nouveau qui a <xref:System.Collections.Generic.KeyValuePair%602> une contrainte de avec <xref:System.String> <xref:System.String>les arguments de type contrainte intérieure et .

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 et WPF Generic XAML Usages

Pour l’utilisation de XAML 2006, et XAML qui est `x:TypeArguments` utilisé pour les applications WPF, les restrictions suivantes existent pour et les utilisations de type générique de XAML en général:

- Seul l’élément racine d’un fichier XAML peut prendre en charge une utilisation générique XAML qui fait référence à un type générique.

- L’élément racine doit cartographier à un type générique avec au moins un argument de type. par exemple <xref:System.Windows.Navigation.PageFunction%601>. Les fonctions de page sont le scénario principal pour le support d’utilisation générique XAML dans WPF.

- L’élément racine XAML élément objet pour le `x:Class`générique doit également déclarer une classe partielle en utilisant . Cela est vrai même si la définition d’une action WPF construire.

- `x:TypeArguments`ne peut pas faire référence aux contraintes génériques imbriquées.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou XAML 2006 sans WPF 3.0 ou WPF 3.5 Dépendance

Dans .NET XAML Services pour XAML 2006 ou XAML 2009, les restrictions liées au WPF sur l’utilisation générique de XAML sont assouplies. Vous pouvez instantané un élément d’objet générique à n’importe quelle position dans le balisage XAML que le système de support et le modèle d’objet peuvent prendre en charge.

Si vous utilisez XAML 2009 au lieu de cartographier les types de base CLR pour obtenir des types XAML pour les primitifs de langage commun, vous pouvez utiliser [les types intégrés pour les primitifs de langue XAML communs](types-for-primitives.md) comme éléments d’information dans un `typeString`. Par exemple, vous pouvez déclarer ce qui suit (les cartes préfixes non affichées, mais x est l’espace de nom XAML en langue XAML pour XAML 2009) :

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

Dans WPF et lors du ciblage .NET Framework 4 ou .NET Core 3.0 (ou plus `x:TypeArguments` tard), vous pouvez utiliser XAML 2009 fonctionnalités avec mais seulement pour le lâche XAML (XAML qui n’est pas compilée de balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009. Si vous avez besoin de compiler le XAML, vous devez opérer en vertu des restrictions indiquées dans la section [XAML 2006 et WPF Generic XAML Usages.](#xaml-2006-and-wpf-generic-xaml-usages) BAML n’est pris en charge que dans le cadre .NET.

## <a name="see-also"></a>Voir aussi

- [x:Class, directive](xclass-directive.md)
- [x:Type, extension de balisage](xtype-markup-extension.md)
- [Types intégrés pour les primitives associées au langage XAML courant](types-for-primitives.md)
- [Génériques en XAML](generics.md)
