---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568218"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json serializer type `JsonException` d’exception changé de à`NotSupportedException`

Dans .NET Core 3.0 Aperçu 6 à 8, le sérialisateur jetterait un <xref:System.Text.Json.JsonException> quand il a rencontré un type de collection dérivé non soutenu. À partir de .NET Core 3.0 Aperçu 9, le sérialisateur jette à <xref:System.NotSupportedException> la place.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 3.0 Aperçu 6 à travers Aperçu <xref:System.Text.Json.JsonException> 8, le sérialisateur jetterait un quand il a rencontré un type de collection dérivé non soutenu. Un *type de collection dérivé non soutenu* est tout type de collection qui n’est pas attribué à l’un des types suivants :

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [Chaîne iDictionnaire,T\<>](xref:System.Collections.Generic.IDictionary%602)

En commençant par .NET Core 3.0 Aperçu 9, le sérialisateur lance un <xref:System.NotSupportedException> Lors de la rencontre d’un type de collection non soutenu. Le nouveau type d’exception reflète mieux les raisons pour lesquelles l’opération de désétérialisation est défaillante.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 9

#### <a name="recommended-action"></a>Action recommandée

Si vous attrapez <xref:System.Text.Json.JsonException> lors de deserialisation, vous <xref:System.NotSupportedException>voudrez peut-être envisager également attraper .

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
