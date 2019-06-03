---
title: Tableau des formats des résultats numériques - Référence C#
ms.custom: seodec18
description: En savoir plus sur les chaînes de format numériques standard C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 0f2b5bc54a0e9055d64a95dc229eaadf66687b43
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421967"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tableau des formats des résultats numériques (référence C#)

Le tableau suivant montre les spécificateurs de format pris en charge pour la mise en forme des résultats numériques. Le résultat mis en forme dans la dernière colonne correspond à « en-US » <xref:System.Globalization.CultureInfo>.

|Spécificateur de format|Description|Exemples|Résultat|  
|----------------------|-----------------|--------------|------------|  
|C ou c|Devise|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2.50<br /><br /> ($2.50)|  
|D ou d|Decimal|`string s = $"{25:D5}";`|00025|  
|E ou e|Exponentiel|`string s = $"{250000:E2}";`|2.50E+005|  
|F ou f|Virgule fixe|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G ou g|Général|`string s = $"{2.5:G}";`|2.5|  
|N ou n|Numérique|`string s = $"{2500000:N}";`|2,500,000.00|  
|P ou p|Pourcentage|`string s = $"{0.25:P}";`|25.00%|  
|R ou r|Aller-retour|`string s = $"{2.5:R}";`|2.5|  
|X ou x|Hexadécimal|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Remarques

Vous utilisez un spécificateur de format pour créer une chaîne de format. La chaîne de format est au format suivant : `Axx`, où

- `A` est le spécificateur de format, qui contrôle le type de mise en forme appliquée à la valeur numérique.
- `xx` est le spécificateur de précision, qui affecte le nombre de chiffres dans la sortie mise en forme. La valeur du spécificateur de précision est comprise entre 0 et 99.

Les spécificateurs de format décimal (« D » ou « d ») et de format hexadécimal (« X » ou « x ») sont pris en charge uniquement pour les types intégraux. Le spécificateur de format aller-retour (« R » ou « r ») est pris en charge uniquement pour les types <xref:System.Single>, <xref:System.Double> et <xref:System.Numerics.BigInteger>.

Les chaînes de format numériques standard sont prises en charge par :

- Certaines surcharges de la méthode `ToString` de tous les types numériques. Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> et <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

- La [fonctionnalité de mise en forme composite](../../../standard/base-types/composite-formatting.md) de .NET, qui est prise en charge par la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>, par exemple.

- [Chaînes interpolées](../tokens/interpolated.md).

Pour plus d’informations, consultez [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mise en forme des types](../../../standard/base-types/formatting-types.md)
- [Mise en forme composite](../../../standard/base-types/composite-formatting.md)
- [Interpolation de chaîne](../tokens/interpolated.md)
- [string](string.md)
