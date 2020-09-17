---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738816"
---
### <a name="parameter-names-changed-in-rc1"></a>Noms de paramètres modifiés dans RC1

Certains noms de paramètres d’assembly de référence ont été modifiés pour correspondre aux noms de paramètres dans les assemblys d’implémentation.

#### <a name="change-description"></a>Description de la modification

Dans les versions antérieures de .NET 5,0 Preview et RC, certains noms de paramètres d' [assembly de référence](../../../../docs/standard/assembly/reference-assemblies.md) sont différents de leurs paramètres correspondants dans l’assembly d’implémentation. Cela peut provoquer des problèmes lors de l’utilisation d’arguments nommés et de la réflexion.

Dans .NET 5,0 RC2, ces noms de paramètres incompatibles ont été mis à jour dans les assemblys de référence pour correspondre exactement aux noms de paramètres correspondants dans les assemblys d’implémentation.

Le tableau suivant indique les API et les noms de paramètres qui ont été modifiés.

| API | Ancien nom du paramètre | Nouveau nom du paramètre |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a>Motif de modification

Les noms de paramètres ont été modifiés pour des fins de cohérence et pour éviter des échecs lors de l’utilisation des arguments nommés et de la réflexion.

#### <a name="version-introduced"></a>Version introduite

5,0 RC2

#### <a name="recommended-action"></a>Action recommandée

Si vous rencontrez une erreur de compilation en raison d’un changement de nom de paramètre, mettez à jour le nom du paramètre en conséquence.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
