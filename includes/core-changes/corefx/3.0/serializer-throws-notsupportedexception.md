---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021664"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Le type d’exception du sérialiseur `JsonException` JSON est passé de à`NotSupportedException`

Dans .NET Core 3,0 Preview 6 à 8, le sérialiseur lève une exception <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge. À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> exception à la place.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 3,0 Preview 6 à Preview 8, le sérialiseur lève une exception <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge. Un *type de collection dérivé non pris en charge* est un type de collection qui n’est pas attribuable à l’un des types suivants :

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [Chaîne\<IDictionary, T>](xref:System.Collections.Generic.IDictionary%602)

À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> lorsqu’il rencontre un type de collection non pris en charge. Le nouveau type d’exception reflète mieux la raison pour laquelle l’opération de désérialisation échoue.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Si vous intervenez <xref:System.Text.Json.JsonException> lors de la désérialisation, vous souhaiterez peut-être également prendre <xref:System.NotSupportedException>en compte l’interception.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
