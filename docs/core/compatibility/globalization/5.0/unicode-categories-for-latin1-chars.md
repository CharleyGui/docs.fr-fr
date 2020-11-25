---
title: 'Modification avec rupture : catégorie Unicode modifiée pour certains caractères latin-1'
description: Découvrez les modifications avec rupture de globalisation dans .NET 5,0 où les méthodes Char renvoient désormais la catégorie Unicode correcte pour les caractères de la plage latin-1.
ms.date: 04/07/2020
ms.openlocfilehash: 8bd093a89857c83921fc0bf987348b529f74ce68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761286"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a>Catégorie Unicode modifiée pour certains caractères latin-1

<xref:System.Char> les méthodes retournent désormais la catégorie Unicode correcte pour les caractères de la plage latin-1. La catégorie correspond à celle de la norme Unicode.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Char> les méthodes utilisaient une liste fixe de catégories Unicode pour les caractères de la plage latin-1. Toutefois, la norme Unicode a modifié les catégories de certains de ces caractères, car ces API ont été implémentées, créant ainsi une différence. En outre, il y avait également une différence entre <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> les API et, qui suivent la norme Unicode. Dans .NET 5,0 et versions ultérieures, <xref:System.Char> les méthodes utilisent et retournent la catégorie Unicode qui correspond à la norme Unicode pour tous les caractères.

Le tableau suivant indique les caractères dont les catégories Unicode ont changé dans .NET 5,0 :

| Caractère    | Catégorie Unicode<br>dans les versions précédentes de .NET | Catégorie Unicode<br>dans .NET 5,0 et versions ultérieures |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| § (\u00a7)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| ª (\u00aa)   | `LowercaseLetter`                             | `OtherLetter`                                      |
| DISCRET (\u00ad) | `DashPunctuation`                             | `Format`                                           |
| ¶ (\u00b6)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| º (\u00ba)   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

Si vous avez du code qui obtient la catégorie de caractères Unicode à l’aide de la <xref:System.Char> classe et suppose que la catégorie ne changera jamais, vous devrez peut-être la mettre à jour.

## <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée afin que les catégories retournées par le <xref:System.Char> type soient cohérentes avec la norme Unicode et le <xref:System.Globalization.CharUnicodeInfo> type.

## <a name="affected-apis"></a>API affectées

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

En outre, toute classe qui dépend de <xref:System.Char> pour obtenir la catégorie de caractères Unicode, par exemple, <xref:System.Text.RegularExpressions.Regex> , est affectée par cette modification.

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
