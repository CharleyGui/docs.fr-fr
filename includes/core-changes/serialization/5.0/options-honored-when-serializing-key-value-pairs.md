---
ms.openlocfilehash: 07980cf94d5de0173808da2ce44adb409fdd5419
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050461"
---
### <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a>Les options PropertyNamingPolicy, PropertyNameCaseInsensitive et encoder sont respectées lors de la sérialisation et de la désérialisation des paires clé-valeur

<xref:System.Text.Json.JsonSerializer> honore désormais les <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> <xref:System.Text.Json.JsonSerializerOptions.Encoder> options et lors de la sérialisation <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> des noms de propriété et d’une <xref:System.Collections.Generic.KeyValuePair%602> instance. En outre, <xref:System.Text.Json.JsonSerializer> honore les <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> options et lors de la <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> désérialisation des <xref:System.Collections.Generic.KeyValuePair%602> instances.

#### <a name="change-description"></a>Description de la modification

##### <a name="serialization"></a>Sérialisation

Dans les versions de .NET Core 3. x et dans les versions 4.6.0-4.7.2 de l' [System.Text.Jssur le package NuGet](https://www.nuget.org/packages/System.Text.Json), les propriétés des <xref:System.Collections.Generic.KeyValuePair%602> instances sont toujours sérialisées en tant que « clé » et « valeur » exactement, quelles que soient les <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options et. L’exemple de code suivant montre comment <xref:System.Collections.Generic.KeyValuePair%602.Key> les <xref:System.Collections.Generic.KeyValuePair%602.Value> Propriétés et ne sont *pas* en casse mixte après la sérialisation, même si la stratégie de nommage de propriété spécifiée le détermine.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

À compter de .NET 5,0, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> les <xref:System.Text.Json.JsonSerializerOptions.Encoder> options et sont respectées lors de la sérialisation des <xref:System.Collections.Generic.KeyValuePair%602> instances. L’exemple de code suivant montre comment <xref:System.Collections.Generic.KeyValuePair%602.Key> les <xref:System.Collections.Generic.KeyValuePair%602.Value> Propriétés et sont en casse mixte après la sérialisation, conformément à la stratégie de nommage de propriété spécifiée.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

##### <a name="deserialization"></a>Désérialisation

Dans les versions de .NET Core 3. x et dans les versions 4.7. x de l' [System.Text.Jssur le package NuGet](https://www.nuget.org/packages/System.Text.Json), une <xref:System.Text.Json.JsonException> exception est levée lorsque les noms de propriété JSON ne sont pas précis `Key` et `Value` , par exemple, s’ils ne commencent pas par une lettre majuscule. L’exception est levée même si une stratégie de nommage de propriété spécifiée le permet expressément.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

À compter de .NET 5,0, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> les <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options et sont respectées lors de la désérialisation à l’aide de <xref:System.Text.Json.JsonSerializer> . Par exemple, l’extrait de code suivant montre la désérialisation réussie des noms de propriété et de minuscules <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> , car la stratégie de nommage de propriété spécifiée le permet.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

Pour prendre en charge les charges utiles qui ont été sérialisées avec les versions précédentes, les valeurs « clé » et « valeur » font l’affaire d’une correspondance spéciale lors de la désérialisation. Même si les <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> noms de propriété et ne sont pas en casse mixte conformément à l' <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in dans l’exemple de code suivant, ils sont désérialisés avec succès.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="reason-for-change"></a>Motif de modification

Des commentaires clients importants ont indiqué que <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> doit être respecté. À des fins d’exhaustivité, les <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> <xref:System.Text.Json.JsonSerializerOptions.Encoder> options et sont également honorées, afin que les <xref:System.Collections.Generic.KeyValuePair%602> instances soient traitées de la même façon que tout autre objet POCO (Plain Old CLR Object).

#### <a name="recommended-action"></a>Action recommandée

Si cette modification s’interrompt, vous pouvez utiliser un [convertisseur personnalisé](../../../../docs/standard/serialization/system-text-json-converters-how-to.md) qui implémente la sémantique souhaitée.

#### <a name="category"></a>Category

Sérialisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
