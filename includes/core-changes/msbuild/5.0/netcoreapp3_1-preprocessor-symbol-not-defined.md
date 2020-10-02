---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654734"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a>NETCOREAPP3_1 symbole de préprocesseur n’est pas défini lors du ciblage de .NET 5

Dans .NET 5,0 RC2 et versions ultérieures, les projets ne définissent plus les symboles de préprocesseur pour les versions antérieures, mais uniquement pour la version qu’ils ciblent. Il s’agit du même comportement que .NET Core 1,0-3,1.

#### <a name="version-introduced"></a>Version introduite

5,0 RC2

#### <a name="change-description"></a>Description de la modification

Dans .NET 5,0 Preview 7 à RC1, les projets qui ciblent `net5.0` définissent à la fois les `NETCOREAPP3_1` `NET5_0` symboles de préprocesseur et. L’objectif de ce changement de comportement était que depuis .NET 5,0, les symboles de compilation conditionnelle [seraient cumulatifs](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).

Dans .NET 5,0 RC2 et versions ultérieures, les projets ne définissent que des symboles pour les monikers du Framework cible (TFM) qu’il cible et non pour les versions antérieures.

#### <a name="reason-for-change"></a>Motif de modification

La modification de Preview 7 a été annulée en raison de commentaires des clients. En définissant des symboles pour les versions antérieures, les clients sont surpris et confus, et certains supposés qu’il s’agissait d’un bogue dans le compilateur C#.

#### <a name="recommended-action"></a>Action recommandée

Assurez-vous que votre `#if` logique ne suppose pas que `NETCOREAPP3_1` est défini lorsque le projet cible `net5.0` ou une version ultérieure. Au lieu de cela, supposons que `NETCOREAPP3_1` est défini uniquement lorsque le projet est explicitement ciblé `netcoreapp3.1` .

Par exemple, si votre projet est multiciblé pour .NET Core 2,1 et .NET Core 3,1 et que vous appelez des API qui ont été introduites dans .NET Core 3,1, votre `#if` logique doit ressembler à ce qui suit :

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a>Category

MSBuild

#### <a name="affected-apis"></a>API affectées

N/A

<!--

#### Affected APIs

Not detectable via API analysis.

-->
