---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 76cd4a0a0f93f4df3ff243c6024b952576e8e6cb
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740539"
---
# <a name="run-time-configuration-options-for-globalization"></a>Options de configuration au moment de l’exécution pour la globalisation

## <a name="invariant-mode"></a>Mode indifférent

- Détermine si une application .NET Core s’exécute en mode de globalisation indifférente sans accéder aux données et au comportement spécifiques à la culture, ou si elle a accès aux données culturelles.
- Par défaut : exécutez l’application avec accès aux données culturelles (`false`).
- Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false`-accès aux données culturelles<br/>`true`-s’exécuter en mode invariant |
| **Variable d'environnement** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`-accès aux données culturelles<br/>`1`-s’exécuter en mode invariant |

## <a name="era-year-ranges"></a>Plages d’années d’ère

- Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui dépassent la plage de dates d’une ère lèvent une <xref:System.ArgumentOutOfRangeException>.
- Valeur par défaut : les contrôles de plage sont assouplis (`false`).
- Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`-contrôles de plage souples<br/>les dépassements de `true` provoquent une exception |
| **Variable d'environnement** | Non applicable | Non applicable |

## <a name="japanese-date-parsing"></a>Analyse de date japonaise

- Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.
- Valeur par défaut : analyser les chaînes qui contiennent soit « 1 » soit « gannen » comme année (`false`).
- Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-« gannen » ou « 1 » est pris en charge<br/>`true` seule « 1 » est pris en charge |
| **Variable d'environnement** | Non applicable | Non applicable |

## <a name="japanese-year-format"></a>Format d’année japonaise

- Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.
- Valeur par défaut : mettez en forme la première année sous la forme « gannen » (`false`).
- Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | format d' `false` en tant que « gannen »<br/>`true` sous forme de nombre |
| **Variable d'environnement** | Non applicable | Non applicable |
