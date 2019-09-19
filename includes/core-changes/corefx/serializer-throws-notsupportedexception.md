---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119281"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Le type d’exception du sérialiseur `JsonException` JSON est passé de à`NotSupportedException`

Dans .net Core 3,0 Preview 6 à 8, le sérialiseur lève une exception <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge. À compter de .net Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> exception à la place.

#### <a name="change-description"></a>Modifier la description

Dans .net Core 3,0 Preview 6 à Preview 8, le sérialiseur lève une exception <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge. Un *type de collection dérivé non pris en charge* est un type de collection qui n’est pas attribuable à l’un des types suivants :

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [Chaîne\<IDictionary, T >](xref:System.Collections.Generic.IDictionary%602)

À compter de .net Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> lorsqu’il rencontre un type de collection non pris en charge. Le nouveau type d’exception reflète mieux la raison pour laquelle l’opération de désérialisation échoue.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Si vous intervenez <xref:System.Text.Json.JsonException> lors de la désérialisation, vous souhaiterez peut-être également prendre <xref:System.NotSupportedException>en compte l’interception.

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
