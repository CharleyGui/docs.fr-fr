---
title: 'Modification avec rupture : LastIndexOf a amélioré la gestion des chaînes de recherche vides'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où LastIndexOf et les API associées retournent désormais des valeurs correctes lors de la recherche d’une sous-chaîne de longueur nulle.
ms.date: 11/01/2020
ms.openlocfilehash: 6d1a676eb2b9ed3de6a745db27d53bd43560a32f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760867"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a>LastIndexOf a amélioré la gestion des chaînes de recherche vides

<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> et les API associées retournent désormais des valeurs correctes lors de la recherche d’une sous-chaîne de longueur nulle (ou équivalente de longueur nulle) dans une chaîne plus grande.

## <a name="change-description"></a>Description de la modification

Dans .NET Framework et .NET Core 1,0-3,1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> et les API associées peuvent retourner une valeur incorrecte lorsque l’appelant recherche une sous-chaîne de longueur nulle.

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

À compter de .NET 5,0, ces API retournent la valeur correcte pour `LastIndexOf` .

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

Dans ces exemples, `5` est la réponse correcte, car `"Hello".Substring(5)` et `"Hello".AsSpan().Slice(5)` les deux produisent une chaîne vide, qui est, de manière triviale, égale à la sous-chaîne vide recherchée.

## <a name="reason-for-change"></a>Motif de modification

Cette modification faisait partie d’un effort de correction global des bogues autour de la gestion des chaînes pour .NET 5. Il permet également d’unifier notre comportement entre les plates-formes Windows et non-Windows. Pour plus d’informations, consultez [dotnet/Runtime # 13383](https://github.com/dotnet/runtime/issues/13383) et [dotnet/Runtime # #13382](https://github.com/dotnet/runtime/issues/13382).

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Aucune action de votre part n’est nécessaire. Le Runtime .NET 5,0 fournit automatiquement les nouveaux comportements.

Il n’existe aucun commutateur de compatibilité pour restaurer l’ancien comportement.

## <a name="affected-apis"></a>API affectées

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
