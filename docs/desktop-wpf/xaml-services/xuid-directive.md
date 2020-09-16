---
title: x:Uid, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 3de02702e6fd2be63bc2d099dad11f896b281ad1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543496"
---
# <a name="xuid-directive"></a>x:Uid, directive

Fournit un identificateur unique à des éléments de balisage. Dans de nombreux scénarios, cet identificateur unique est utilisé par les processus et les outils de localisation XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`identifier`|Chaîne créée manuellement ou générée automatiquement qui doit être unique dans un fichier lorsqu’il est interprété par un `x:Uid` consommateur.|

## <a name="remarks"></a>Notes

Dans [MS-XAML], `x:Uid` est défini en tant que directive. Pour plus d’informations, consultez la [ \[ section MS-XAML \] 5.3.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid` est discrète des `x:Name` deux en raison du scénario de localisation XAML indiqué et de sorte que les identificateurs utilisés pour la localisation n’ont pas de dépendances vis-à-vis des implications du modèle de programmation de `x:Name` . En outre, `x:Name` est régi par la portée de code XAML ; Toutefois, n' `x:Uid` est régi par aucun concept défini par le langage XAML de l’application de l’unicité. Les processeurs XAML à sens large (les processeurs qui ne font pas partie du processus de localisation) ne sont pas censés garantir l’unicité des `x:Uid` valeurs. Cette responsabilité est conceptuellement sur l’expéditeur des valeurs. L’attente de l’unicité des `x:Uid` valeurs dans une même source XAML est raisonnable pour les consommateurs des valeurs, telles que les processus de globalisation dédiés ou les outils. Le modèle d’unicité standard est que les `x:Uid` valeurs sont uniques dans un fichier encodé XML qui représente du code XAML.

Les outils qui ont une connaissance significative d’un schéma XAML particulier peuvent choisir d’appliquer `x:Uid` uniquement pour les véritables chaînes localisables, plutôt que pour tous les cas où une valeur de chaîne de texte est rencontrée dans le balisage.

Les infrastructures peuvent spécifier une propriété particulière dans leur modèle objet pour qu’elles soient un alias de `x:Uid` en appliquant l’attribut <xref:System.Windows.Markup.UidPropertyAttribute> au type de définition. Si une infrastructure spécifie une propriété particulière, il n’est pas possible de spécifier à `x:Uid` la fois et le membre avec alias sur le même objet. Si `x:Uid` et le membre avec alias sont spécifiés, l’API des services XAML .NET lève généralement <xref:System.Xaml.XamlDuplicateMemberException> pour ce cas.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Pour plus d’informations sur le rôle de `x:Uid` dans le processus de localisation WPF et dans le formulaire BAML de XAML, consultez [globalisation pour WPF](/dotnet/desktop/wpf/advanced/globalization-for-wpf) ou <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalisation pour WPF](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
