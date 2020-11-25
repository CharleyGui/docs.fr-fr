---
title: 'Modification avec rupture : complexité de LINQ OrderBy. la première {OrDefault} a augmenté'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où l’implémentation de OrderBy. First a changé.
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f8fd0bb2051c3e1ac14eab091be11f10f88b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761046"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a>Complexité de LINQ OrderBy. la première {OrDefault} a augmenté

L’implémentation de <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> et <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> a changé, ce qui a entraîné une plus grande complexité pour l’opération.

## <a name="change-description"></a>Description de la modification

Dans .NET Core 1. x-3. x, l’appel de <xref:System.Linq.Enumerable.OrderBy%2A> ou <xref:System.Linq.Enumerable.OrderByDescending%2A> suivi de <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> fonctionne avec `O(N)` complexité. Étant donné que seul le premier élément (ou par défaut) est requis, une seule énumération est nécessaire pour le trouver. Toutefois, le prédicat fourni à <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> est appelé exactement `N` fois, où `N` est la longueur de la séquence.

Dans .NET 5,0 et versions ultérieures, une [modification a été apportée](https://github.com/dotnet/runtime/pull/36643) de telle sorte que l’appel <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> de ou suivi de <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> fonctionne avec `O(N log N)` la complexité plutôt que `O(N)` la complexité. Toutefois, le prédicat fourni à <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> peut être appelé *moins* de `N` fois, ce qui est plus important pour les performances globales.

> [!NOTE]
> Cette modification correspond à l’implémentation et à la complexité de l’opération dans .NET Framework.

## <a name="reason-for-change"></a>Motif de modification

L’avantage de l’appel du prédicat moins souvent compense une complexité globale plus faible, de sorte que l’implémentation introduite dans .NET Core 1,0 a été annulée. Pour plus d’informations, consultez [ce problème dotnet/Runtime](https://github.com/dotnet/runtime/issues/31554).

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur.

## <a name="affected-apis"></a>API affectées

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
