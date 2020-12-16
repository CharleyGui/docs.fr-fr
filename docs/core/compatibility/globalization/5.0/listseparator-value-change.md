---
title: 'Modification avec rupture : changement de valeur TextInfo. ListSeparator'
description: Découvrez la modification avec rupture .NET 5,0 où la valeur par défaut de TextInfo. ListSeparator a été modifiée entre les versions 5,0 et 5.0.1.
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596544"
---
# <a name="textinfolistseparator-values-changed"></a>Valeurs de TextInfo. ListSeparator modifiées

Les valeurs par défaut <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> pour les différentes cultures ont changé sur tous les systèmes d’exploitation.

## <a name="change-description"></a>Description de la modification

Dans .NET 5.0.0, dans le cadre du [passage de nls aux bibliothèques ICU](icu-globalization-api.md), les valeurs par défaut <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> pour les différentes cultures ont changé sur Windows. Les valeurs de séparateur décimal, obtenues à partir des composants internationaux pour Unicode (ICU), ont été utilisées comme <xref:System.Globalization.TextInfo.ListSeparator> valeurs. Sur Linux et macOS, aucune modification n’a été apportée aux <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs, c’est-à-dire qu’elles continuent à utiliser des valeurs de séparateur décimal.

Pour tous les systèmes d’exploitation dans .NET 5.0.1 et versions ultérieures, les valeurs de <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> sont équivalentes aux valeurs qui seraient obtenues à partir de nls. Pour Windows, cela signifie que les valeurs sont équivalentes à ce qu’elles étaient dans .NET Framework et .NET Core 1,0-3,1. Pour Linux et macOS, les <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs correspondent maintenant aux <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs pour Windows.

Le tableau suivant récapitule les modifications apportées aux <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs.

| | .NET Framework<br/>.NET Core 1,0-3,1 | .NET 5.0 | .NET 5.0.1 |
-|-|-|-
| **Windows** | Obtenir à partir de NLS | Séparateur décimal d’ICU.<br/>Peut revenir à NLS. | Équivalent à NLS |
| **Linux et macOS** | Séparateur décimal d’ICU | Séparateur décimal d’ICU | Équivalent à NLS |

## <a name="version-introduced"></a>Version introduite

5.0.1

## <a name="reason-for-change"></a>Motif de modification

Les développeurs ont signalé qu’ils utilisent la <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> propriété lors de l’analyse des fichiers de valeurs séparées par des virgules (CSV), et les nouvelles <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs ont enfreint cette analyse.

## <a name="recommended-action"></a>Action recommandée

Si votre code s’appuie sur les valeurs de séparateur décimal précédentes, vous pouvez coder en dur les valeurs souhaitées <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> .

## <a name="affected-apis"></a>API affectées

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
