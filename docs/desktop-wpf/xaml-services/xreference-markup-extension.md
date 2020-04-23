---
title: x:Référence, extension de balisage
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071380"
---
# <a name="xreference-markup-extension"></a>x:Référence, extension de balisage

Références d’un cas qui est déclaré ailleurs dans le balisage XAML. La référence se réfère à `x:Name`un élément .

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`instancexName`|La `x:Name` valeur (ou <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>la valeur de la propriété identifiée) de l’instance référencée.|

## <a name="remarks"></a>Notes

`x:Reference`fournit un soutien au niveau de la langue XAML pour un concept de référence d’élément qui a été autrement mis en œuvre dans des cadres spécifiques tels que WPF.

## <a name="xreference-and-wpf"></a>x:Référence et WPF

Dans WPF et XAML 2006, les références d’éléments sont abordées par la caractéristique de niveau-cadre de la <xref:System.Windows.Data.Binding.ElementName%2A> liaison. Pour la plupart des applications <xref:System.Windows.Data.Binding.ElementName%2A> et scénarios WPF, la liaison doit encore être utilisée. Les exceptions à ces directives générales peuvent inclure les cas où il y a un contexte de données ou d’autres considérations de portée qui rendent la compilation des données impraticable et où la compilation de balisage n’est pas impliquée.

`x:Reference`est une construction définie dans XAML 2009. Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage WPF. Le code XAML compilé par balisage et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés de langage et fonctionnalités XAML 2009.
