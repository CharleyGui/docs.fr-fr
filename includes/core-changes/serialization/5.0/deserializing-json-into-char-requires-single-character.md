---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844502"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a>JsonSerializer. Deserialize requiert une chaîne à un seul caractère

Lorsque le paramètre de type est <xref:System.Char> , l’argument de chaîne de <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> doit contenir un caractère unique pour que la désérialisation aboutisse.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, si vous transmettez une chaîne de plusieurs caractères à <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> et que le paramètre de type est <xref:System.Char> , la désérialisation réussit et seul le premier caractère est désérialisé.

Dans .NET 5,0 et versions ultérieures, lorsque le paramètre de type est <xref:System.Char> , passer tout autre chose qu’une chaîne de caractères simples entraîne la <xref:System.Text.Json.JsonException> levée d’une exception.

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="reason-for-change"></a>Motif de modification

<xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> analyse le texte qui représente une valeur JSON unique dans une instance du type spécifié par le paramètre de type générique. L’analyse doit être effectuée uniquement lorsque la charge utile fournie est valide pour le paramètre de type générique spécifié. Pour un <xref:System.Char> type valeur, une charge utile valide est une chaîne de caractères unique.

#### <a name="recommended-action"></a>Action recommandée

Lors de l’analyse d’une chaîne dans un <xref:System.Char> type à l’aide de, assurez-vous <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> que la chaîne se compose d’un seul caractère.

#### <a name="category"></a>Category

Sérialisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->
