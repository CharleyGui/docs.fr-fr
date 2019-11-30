---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568218"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Le type d’exception du sérialiseur JSON est passé de `JsonException` à `NotSupportedException`

Dans .NET Core 3,0 Preview 6 à 8, le sérialiseur lève une <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge. À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> à la place.

#### <a name="change-description"></a>Modifier la description

Dans .NET Core 3,0 Preview 6 jusqu’à Preview 8, le sérialiseur lève une <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge. Un *type de collection dérivé non pris en charge* est un type de collection qui n’est pas attribuable à l’un des types suivants :

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [IDictionary\<chaîne, T >](xref:System.Collections.Generic.IDictionary%602)

À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> lorsqu’il rencontre un type de collection non pris en charge. Le nouveau type d’exception reflète mieux la raison pour laquelle l’opération de désérialisation échoue.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Si vous interceptez des <xref:System.Text.Json.JsonException> lors de la désérialisation, vous souhaiterez peut-être également intercepter les <xref:System.NotSupportedException>.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
