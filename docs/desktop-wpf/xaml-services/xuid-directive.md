---
title: x:Uid, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: b5b480016d2183268422dea861510c6a169ac27b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071338"
---
# <a name="xuid-directive"></a>x:Uid, directive

Fournit un identificateur unique à des éléments de balisage. Dans de nombreux scénarios, cet identifiant unique est utilisé par les processus et outils de localisation XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`identifier`|Une chaîne créée ou autogénérée manuellement qui doit être unique `x:Uid` dans un fichier lorsqu’elle est interprétée par un consommateur.|

## <a name="remarks"></a>Notes

Dans [MS-XAML], `x:Uid` est défini comme une directive. Pour plus d’informations, voir [ \[MS-XAML\] Section 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid`est discret `x:Name` à la fois en raison du scénario de localisation XAML énoncé et de sorte que les `x:Name`identificateurs qui sont utilisés pour la localisation n’ont aucune dépendance sur les implications du modèle de programmation de . En `x:Name` outre, est régi par le namescope XAML; cependant, `x:Uid` n’est pas régi par un concept défini par le langage XAML de l’application de la singularité. Les processeurs XAML au sens large (les processeurs qui ne font pas partie `x:Uid` du processus de localisation) ne devraient pas faire respecter l’unicité des valeurs. Cette responsabilité est conceptuellement à l’origine des valeurs. L’attente d’un caractère unique des `x:Uid` valeurs au sein d’une seule source XAML est raisonnable pour les consommateurs des valeurs, telles que les processus ou les outils dédiés à la mondialisation. Le modèle typique d’unicité est que les `x:Uid` valeurs sont uniques dans un fichier codé XML qui représente XAML.

Les outils qui ont une connaissance significative d’un `x:Uid` schéma XAML particulier peuvent choisir de s’appliquer uniquement pour les vraies chaînes localisables, au lieu de tous les cas où une valeur de chaîne de texte est rencontrée dans le balisage.

Les cadres peuvent spécifier une propriété particulière `x:Uid` dans leur <xref:System.Windows.Markup.UidPropertyAttribute> modèle d’objet pour être un alias pour en appliquant l’attribut au type définissant. Si un cadre spécifie une propriété particulière, il n’est pas valide de spécifier à la fois `x:Uid` et le membre alias sur le même objet. Si `x:Uid` les deux et le membre alias sont spécifiés, <xref:System.Xaml.XamlDuplicateMemberException> .NET XAML Services API jette généralement pour ce cas.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Pour plus d’informations `x:Uid` sur le rôle de dans le processus de localisation WPF et sous la forme BAML de XAML, voir [Mondialisation pour WPF](../../framework/wpf/advanced/globalization-for-wpf.md) ou<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalisation pour WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
