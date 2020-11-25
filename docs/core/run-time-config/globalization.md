---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: fc98e965093c28b75b9b66e4f1c9f147abd4680e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721910"
---
# <a name="run-time-configuration-options-for-globalization"></a>Options de configuration au moment de l’exécution pour la globalisation

## <a name="invariant-mode"></a>Mode indifférent

- Détermine si une application .NET Core s’exécute en mode globalisation-invariant sans accéder aux données et au comportement spécifiques à la culture.
- Si vous omettez ce paramètre, l’application s’exécute avec un accès aux données culturelles. Cela équivaut à définir la valeur sur `false` .
- Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Globalization.Invariant` | `false` -accès aux données culturelles<br/>`true` -exécuter en mode invariant |
| **MSBuild, propriété** | `InvariantGlobalization` | `false` -accès aux données culturelles<br/>`true` -exécuter en mode invariant |
| **Variable d'environnement** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0` -accès aux données culturelles<br/>`1` -exécuter en mode invariant |

### <a name="examples"></a>Exemples

*runtimeconfig.jssur le* fichier :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>Plages d’années d’ère

- Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui dépassent la plage de dates d’une ère lèvent un <xref:System.ArgumentOutOfRangeException> .
- Si vous omettez ce paramètre, les contrôles de plage sont assouplis. Cela équivaut à définir la valeur sur `false` .
- Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false` -vérifications de plage souples<br/>`true` -les dépassements de capacité provoquent une exception |
| **Variable d'environnement** | N/A | N/A |

## <a name="japanese-date-parsing"></a>Analyse de date japonaise

- Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.
- Si vous omettez ce paramètre, les chaînes qui contiennent « 1 » ou « gannen » sont analysées avec succès. Cela équivaut à définir la valeur sur `false` .
- Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false` -« Gannen » ou « 1 » est pris en charge<br/>`true` seule « 1 » est pris en charge |
| **Variable d'environnement** | N/A | N/A |

## <a name="japanese-year-format"></a>Format d’année japonaise

- Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.
- Si vous omettez ce paramètre, la première année est mise en forme en tant que « gannen ». Cela équivaut à définir la valeur sur `false` .
- Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false` -format comme « gannen »<br/>`true` -format comme nombre |
| **Variable d'environnement** | N/A | N/A |

## <a name="nls"></a>NLS

- Détermine si .NET utilise les API de globalisation NLS (National Language Support) ou International Components for Unicode (ICU) pour les applications Windows. .NET 5,0 et les versions ultérieures utilisent les API de globalisation ICU par défaut sur Windows 10 mai 2019 Update et les versions ultérieures.
- Si vous omettez ce paramètre, .NET utilise les API de globalisation ICU par défaut. Cela équivaut à définir la valeur sur `false` .
- Pour plus d’informations, consultez [API de globalisation utiliser des bibliothèques ICU sur Windows](../compatibility/globalization/5.0/icu-globalization-api.md).

| | Nom du paramètre | Valeurs | Introduit |
| - | - | - | - |
| **runtimeconfig.js** | `System.Globalization.UseNls` | `false` -Utiliser les API de globalisation ICU<br/>`true` -Utiliser les API de globalisation NLS | .NET 5,0 |
| **Variable d'environnement** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false` -Utiliser les API de globalisation ICU<br/>`true` -Utiliser les API de globalisation NLS | .NET 5,0 |
