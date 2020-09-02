---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359131"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>Les contrôles de IsSupported intrinsèques matériels peuvent être différents pour les types imbriqués

`<Isa>.X64.IsSupported`La vérification, où `<Isa>` fait référence aux classes de l' <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> espace de noms, peut à présent produire un résultat différent pour les versions précédentes de .net.

> [!TIP]
> *ISA* est l’acronyme de l’architecture standard de l’industrie.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, certains des <xref:System.Runtime.Intrinsics.X86> types intrinsèques du matériel, par exemple, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> , n’exposent pas une classe imbriquée `X64` . Pour ces types, l’appel de `<Isa>.X64.IsSupported` résolu à une `IsSupported` propriété sur une `X64` classe imbriquée d’une classe parente de `<Isa>` . Cela signifiait que la propriété pouvait retourner `true` même lorsque `<Isa>.IsSupported` retourne `false` .

Dans .NET 5,0 et versions ultérieures, tous les <xref:System.Runtime.Intrinsics.X86> types exposent une `X64` classe imbriquée qui signale correctement la prise en charge. Cela garantit que la hiérarchie générale reste correcte, et que si `<Isa>.X64.IsSupported` a la valeur `true` , `<Isa>.IsSupported` peut également être supposé être `true` .

#### <a name="reason-for-change"></a>Motif de modification

Il a été prévu que si `<Isa>.X64.IsSupported` a la valeur `true` , `<Isa>.IsSupported` est également supposé être `true` . Toutefois, en raison du fonctionnement de la résolution des membres en C#, les classes qui n’ont pas de classe imbriquée `X64` exposaient une situation où cela n’était pas toujours le cas et ont conduit à des bogues dans le code utilisateur.

#### <a name="recommended-action"></a>Action recommandée

Si nécessaire, ajustez le code qui vérifie si `IsSupported` le ISA approprié est vérifié.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
