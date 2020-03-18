---
title: La mondialisation config paramètres
description: Découvrez les paramètres de run-time qui configurent les aspects de la mondialisation d’une application .NET Core, par exemple, comment elle analyse les dates japonaises.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733454"
---
# <a name="run-time-configuration-options-for-globalization"></a>Options de configuration en temps de course pour la mondialisation

## <a name="invariant-mode"></a>Mode invariant

- Détermine si une application .NET Core fonctionne en mode invariant mondialisation sans accès à des données et à un comportement spécifiques à la culture ou si elle a accès à des données culturelles.
- Défaut : Exécutez l’application`false`avec accès aux données culturelles ( ).
- Pour plus d’informations, voir [.NET Core globalisation en mode invariant](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Globalization.Invariant` | `false`- accès aux données culturelles<br/>`true`- exécuter en mode invariant |
| **Propriété MSBuild** | `InvariantGlobalization` | `false`- accès aux données culturelles<br/>`true`- exécuter en mode invariant |
| **Variable de l’environnement** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`- accès aux données culturelles<br/>`1`- exécuter en mode invariant |

### <a name="examples"></a>Exemples

*fichier runtimeconfig.json:*

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

## <a name="era-year-ranges"></a>Gammes d’années d’époque

- Détermine si les contrôles de portée pour les calendriers qui prennent en charge plusieurs <xref:System.ArgumentOutOfRangeException>époques sont assouplis ou si les dates qui débordent de la plage de date d’une époque jeter un .
- Défaut : Les contrôles`false`de portée sont détendus ( ).
- Pour plus d’informations, voir [Calendriers, époques et plages de dates: Vérifications de portée détendue](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`- contrôles de portée détendus<br/>`true`- les débordements causent une exception |
| **Variable de l’environnement** | N/A | N/A |

## <a name="japanese-date-parsing"></a>Analyse de date japonaise

- Détermine si une chaîne qui contient soit "1" ou "Gannen" que l’année analyse avec succès ou si seulement "1" est pris en charge.
- Défaut: Parse cordes qui contiennent soit "1" ou "Gannen" comme l’année (`false`).
- Pour plus d’informations, voir [Les dates de représentation dans les calendriers à plusieurs époques](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`- "Gannen" ou "1" est soutenu<br/>`true`- seul "1" est pris en charge |
| **Variable de l’environnement** | N/A | N/A |

## <a name="japanese-year-format"></a>Format de l’année japonaise

- Détermine si la première année d’une ère de calendrier japonaise est formatée comme "Gannen" ou en nombre.
- Défaut: Format de la première année`false`comme "Gannen" ( ).
- Pour plus d’informations, voir [Les dates de représentation dans les calendriers à plusieurs époques](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`- format comme "Gannen"<br/>`true`- format comme numéro |
| **Variable de l’environnement** | N/A | N/A |
