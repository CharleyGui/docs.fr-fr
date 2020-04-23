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
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071429"
---
# <a name="xnull-markup-extension"></a>x:Null, extension de balisage

Spécifie `null` comme valeur pour un membre XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Notes

Le mot clé pour une référence nulle dans C et CM est nul. Le mot clé Microsoft Visual `Nothing`Basic pour une `{x:Null}` référence nulle est, mais vous utilisez toujours comme l’utilisation XAML indépendamment de la langue codé-derrière vous associer avec le XAML.

L’extension `x:Null` de balisage n’a pas de propriétés fixes.

Une utilisation nulle est souvent associée à l’exposition <xref:System.Nullable%601> des membres XAML d’une valeur CLR.

L’extension `x:Null` de balisage, comme toutes les extensions`{,}`de balisage XAML, utilise les accolades ( ) pour échapper à la manipulation des valeurs d’attribut pour être autre que les littérals ou les références event-handler. La syntaxe d’attribut est la syntaxe la plus fréquemment utilisée avec cette extension de balisage. Une syntaxe `<x:Null />` d’élément objet est techniquement `x:Null` possible, mais est rarement utilisée parce que l’extension de balisage n’a pas de paramètres de position ou d’arguments de construction.

Pour plus d’informations sur les extensions de balisage, voir [Extensions Markup et WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Dans .NET XAML Services, la manipulation de cette <xref:System.Windows.Markup.NullExtension> extension de balisage est définie par la classe.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Notez `null` que ce n’est pas nécessairement la valeur initiale non assaillie d’une propriété de dépendance de type de référence. La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété. De nombreuses propriétés `null` de dépendance n’acceptent pas comme valeur, que ce soit par balisage ou par code en raison de leurs implémentations de rappel de validation. Pour plus d’informations sur les propriétés de dépendance, voir [Dependency Properties Aperçu](../../framework/wpf/advanced/dependency-properties-overview.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
