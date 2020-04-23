---
title: Génériques en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071737"
---
# <a name="generics-in-xaml"></a>Génériques en XAML

.NET XAML Services <xref:System.Xaml?displayProperty=fullName> tel qu’il est mis en œuvre dans fournit un soutien à l’utilisation de types de CLR génériques. Ce support comprend la spécence des contraintes des génériques comme `Add` argument type et l’application de la contrainte en appelant la méthode appropriée pour les cas de collecte générique. Ce sujet décrit des aspects de l’utilisation et du référencement des types génériques dans XAML.

## <a name="xtypearguments"></a>x:TypeArguments

`x:TypeArguments`est une directive définie par la langue XAML. Lorsqu’il est utilisé comme membre d’un type XAML `x:TypeArguments` qui est soutenu par un type générique, passe des arguments de type contraignant du générique au constructeur de soutien. Pour la syntaxe de référence qui se `x:TypeArguments`rapporte à .NET XAML Services utilisation de , qui comprend des exemples de syntaxe, voir [x:TypeArguments Directive](xtypearguments-directive.md).

Parce `x:TypeArguments` que prend une chaîne, et a le support de convertisseur de type, il est généralement déclaré dans l’utilisation XAML comme un attribut.

Dans le flux de nœuds `x:TypeArguments` XAML, <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> les `StartObject` informations déclarées par peuvent être obtenues à partir d’une position dans le flux de nœuds. La valeur <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> de rendement <xref:System.Xaml.XamlType> est une liste de valeurs. Déterminer si un type XAML représente un type <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>générique peut être fait en appelant .

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Conventions de règles et de syntaxe pour les génériques dans XAML

Dans XAML, un type générique doit toujours être représenté comme un générique contraint. Un générique sans contrainte n’est jamais présent dans le système de type XAML ou un flux de nœuds XAML et ne peut pas être représenté dans la balisage XAML. Un générique peut être référencé dans la syntaxe d’attribut XAML pour les `x:TypeArguments`cas où `x:Type` il s’agit d’une contrainte de type imbriqué d’un générique référencé par , ou pour les cas où fournit une référence de type CLR pour un type générique. Le référencement des génériques est pris en charge par la <xref:System.Xaml.Schema.XamlTypeTypeConverter> classe définie par .NET XAML Services.

La forme de syntaxe <xref:System.Xaml.Schema.XamlTypeTypeConverter> d’attribut XAML activée par modifie la convention typique de syntaxe MSIL /CLR qui utilise des supports d’angle pour les types et les contraintes des génériques, et remplace plutôt les parenthèses pour le contenant de contrainte. Par exemple, voir [x:TypeArguments Directive](xtypearguments-directive.md).

## <a name="generics-and-xaml-2009-features"></a>Caractéristiques génériques et XAML 2009

Si vous utilisez XAML 2009 au lieu de cartographier les types de base CLR pour obtenir des types XAML pour `x:TypeArguments`les primitifs de langage commun, vous pouvez utiliser [XAML 2009 types intégrés](types-for-primitives.md) comme éléments d’information dans . Par exemple, vous pouvez déclarer ce qui suit `x` (les cartes préfixes non affichées, mais c’est l’espace de nom XAML en langue XAML pour XAML 2009) :

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a>Soutien générique dans WPF

Pour l’utilisation de XAML 2006 lors du ciblage spécifique de `x:TypeArguments`WPF, [x:Classe](xclass-directive.md) doit également être fourni sur le même élément que, et cet élément doit être l’élément racine dans un document XAML. L’élément racine doit cartographier à un type générique avec au moins un argument de type. par exemple <xref:System.Windows.Navigation.PageFunction%601>.

Les solutions de contournement possibles pour soutenir les utilisations génériques comprennent la définition d’une extension de balisage personnalisée qui peut retourner les types génériques, ou de fournir une définition de classe d’emballage qui dérive d’un type générique, mais aplatit la contrainte générique dans sa propre définition de classe.

Dans WPF, vous pouvez utiliser XAML 2009 fonctionnalités avec `x:TypeArguments`, mais seulement pour XAML lâche (XAML qui n’est pas compilée de balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.

Les flux de travail personnalisés de windows Workflow Foundation pour .NET Framework 3.5 ne prennent pas en charge l’utilisation générique de XAML.

## <a name="see-also"></a>Voir aussi

- [x:TypeArguments, directive](xtypearguments-directive.md)
- [x:Class, directive](xclass-directive.md)
- [Types intégrés pour les primitives associées au langage XAML courant](types-for-primitives.md)
