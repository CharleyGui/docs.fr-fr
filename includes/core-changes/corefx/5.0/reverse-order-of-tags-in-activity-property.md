---
ms.openlocfilehash: 24b88b3ba1b6cfe9fb9fb1f6398a6daeb57596a9
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756106"
---
### <a name="order-of-tags-in-activitytags-is-reversed"></a>Ordre des balises dans Activity. les balises sont inversées

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke désormais les éléments dans la liste en fonction de l’ordre dans lequel ils sont ajoutés, c’est-à-dire que le premier élément ajouté est tout d’abord dans la liste. Cette modification a été apportée pour correspondre à la [spécification des attributs OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke les éléments dans l’ordre inverse à partir duquel ils sont ajoutés. Autrement dit, le premier élément ajouté est le dernier de la liste. À compter de .NET 5,0, l’ordre des éléments est inversé et le premier élément ajouté est toujours en premier dans la liste.

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="recommended-action"></a>Action recommandée

Si votre application dépend de l’ordre de la <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste et que vous effectuez une mise à niveau vers .net 5,0 ou une version ultérieure, vous devez modifier cette partie de votre code.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
