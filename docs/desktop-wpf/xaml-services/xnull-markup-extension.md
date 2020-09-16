---
title: x:Null, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549442"
---
# <a name="xnull-markup-extension"></a>x:Null, extension de balisage

Spécifie `null` comme valeur pour un membre XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Notes

Le mot clé pour une référence null en C# et C++ a la valeur null. Le mot clé Microsoft Visual Basic pour une référence null est `Nothing` , mais vous utilisez toujours `{x:Null}` comme utilisation XAML quel que soit le langage code-behind que vous associez au XAML.

L' `x:Null` extension de balisage n’a pas de propriétés définissables.

Une utilisation null est souvent associée à l’exposition du membre XAML d’une <xref:System.Nullable%601> valeur CLR.

L' `x:Null` extension de balisage, comme toutes les extensions de balisage XAML, utilise les accolades ( `{,}` ) pour échapper la gestion des valeurs d’attribut à d’autres littéraux ou références de gestionnaires d’événements. La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Une syntaxe d’élément objet `<x:Null />` est techniquement possible, mais est rarement utilisée, car l' `x:Null` extension de balisage n’a pas de paramètres positionnels ou d’arguments de construction.

Pour plus d’informations sur les extensions de balisage, consultez [extensions de balisage et XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).

Dans les services XAML .NET, la gestion de cette extension de balisage est définie par la <xref:System.Windows.Markup.NullExtension> classe.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Notez qu' `null` il ne s’agit pas nécessairement de la valeur initiale non définie pour une propriété de dépendance de type référence. La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété. De nombreuses propriétés de dépendance n’acceptent pas `null` comme valeur, par le biais du balisage ou du code en raison de leurs implémentations de rappel de validation. Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](/dotnet/desktop/wpf/advanced/dependency-properties-overview).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
