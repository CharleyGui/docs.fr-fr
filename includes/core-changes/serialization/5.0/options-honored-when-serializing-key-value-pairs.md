---
ms.openlocfilehash: 07980cf94d5de0173808da2ce44adb409fdd5419
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050461"
---
### <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a><span data-ttu-id="26def-101">Les options PropertyNamingPolicy, PropertyNameCaseInsensitive et encoder sont respectées lors de la sérialisation et de la désérialisation des paires clé-valeur</span><span class="sxs-lookup"><span data-stu-id="26def-101">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>

<span data-ttu-id="26def-102"><xref:System.Text.Json.JsonSerializer> honore désormais les <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> <xref:System.Text.Json.JsonSerializerOptions.Encoder> options et lors de la sérialisation <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> des noms de propriété et d’une <xref:System.Collections.Generic.KeyValuePair%602> instance.</span><span class="sxs-lookup"><span data-stu-id="26def-102"><xref:System.Text.Json.JsonSerializer> now honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options when serializing the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names of a <xref:System.Collections.Generic.KeyValuePair%602> instance.</span></span> <span data-ttu-id="26def-103">En outre, <xref:System.Text.Json.JsonSerializer> honore les <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> options et lors de la <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> désérialisation des <xref:System.Collections.Generic.KeyValuePair%602> instances.</span><span class="sxs-lookup"><span data-stu-id="26def-103">Additionally, <xref:System.Text.Json.JsonSerializer> honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options when deserializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span>

#### <a name="change-description"></a><span data-ttu-id="26def-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="26def-104">Change description</span></span>

##### <a name="serialization"></a><span data-ttu-id="26def-105">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="26def-105">Serialization</span></span>

<span data-ttu-id="26def-106">Dans les versions de .NET Core 3. x et dans les versions 4.6.0-4.7.2 de l' [System.Text.Jssur le package NuGet](https://www.nuget.org/packages/System.Text.Json), les propriétés des <xref:System.Collections.Generic.KeyValuePair%602> instances sont toujours sérialisées en tant que « clé » et « valeur » exactement, quelles que soient les <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options et.</span><span class="sxs-lookup"><span data-stu-id="26def-106">In .NET Core 3.x versions and in the 4.6.0-4.7.2 versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), the properties of <xref:System.Collections.Generic.KeyValuePair%602> instances are always serialized as "Key" and "Value" exactly, regardless of any <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> and <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="26def-107">L’exemple de code suivant montre comment <xref:System.Collections.Generic.KeyValuePair%602.Key> les <xref:System.Collections.Generic.KeyValuePair%602.Value> Propriétés et ne sont *pas* en casse mixte après la sérialisation, même si la stratégie de nommage de propriété spécifiée le détermine.</span><span class="sxs-lookup"><span data-stu-id="26def-107">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are *not* camel-cased after serialization, even though the specified property-naming policy dictates so.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

<span data-ttu-id="26def-108">À compter de .NET 5,0, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> les <xref:System.Text.Json.JsonSerializerOptions.Encoder> options et sont respectées lors de la sérialisation des <xref:System.Collections.Generic.KeyValuePair%602> instances.</span><span class="sxs-lookup"><span data-stu-id="26def-108">Starting in .NET 5.0, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are honored when serializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span> <span data-ttu-id="26def-109">L’exemple de code suivant montre comment <xref:System.Collections.Generic.KeyValuePair%602.Key> les <xref:System.Collections.Generic.KeyValuePair%602.Value> Propriétés et sont en casse mixte après la sérialisation, conformément à la stratégie de nommage de propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26def-109">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are camel-cased after serialization, in accordance with the specified property-naming policy.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

##### <a name="deserialization"></a><span data-ttu-id="26def-110">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="26def-110">Deserialization</span></span>

<span data-ttu-id="26def-111">Dans les versions de .NET Core 3. x et dans les versions 4.7. x de l' [System.Text.Jssur le package NuGet](https://www.nuget.org/packages/System.Text.Json), une <xref:System.Text.Json.JsonException> exception est levée lorsque les noms de propriété JSON ne sont pas précis `Key` et `Value` , par exemple, s’ils ne commencent pas par une lettre majuscule.</span><span class="sxs-lookup"><span data-stu-id="26def-111">In .NET Core 3.x versions and in the 4.7.x versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), a <xref:System.Text.Json.JsonException> is thrown when the JSON property names are not precisely `Key` and `Value`, for example, if they don't start with an uppercase letter.</span></span> <span data-ttu-id="26def-112">L’exception est levée même si une stratégie de nommage de propriété spécifiée le permet expressément.</span><span class="sxs-lookup"><span data-stu-id="26def-112">The exception is thrown even if a specified property-naming policy expressly permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

<span data-ttu-id="26def-113">À compter de .NET 5,0, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> les <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options et sont respectées lors de la désérialisation à l’aide de <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="26def-113">Starting in .NET 5.0, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options are honored when deserializing using <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="26def-114">Par exemple, l’extrait de code suivant montre la désérialisation réussie des noms de propriété et de minuscules <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> , car la stratégie de nommage de propriété spécifiée le permet.</span><span class="sxs-lookup"><span data-stu-id="26def-114">For example, the following code snippet shows successful deserialization of lowercased <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names because the specified property-naming policy permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

<span data-ttu-id="26def-115">Pour prendre en charge les charges utiles qui ont été sérialisées avec les versions précédentes, les valeurs « clé » et « valeur » font l’affaire d’une correspondance spéciale lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="26def-115">To accommodate payloads that were serialized with previous versions, "Key" and "Value" are special-cased to match when deserializing.</span></span> <span data-ttu-id="26def-116">Même si les <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> noms de propriété et ne sont pas en casse mixte conformément à l' <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in dans l’exemple de code suivant, ils sont désérialisés avec succès.</span><span class="sxs-lookup"><span data-stu-id="26def-116">Even though the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names aren't camel-cased according to the in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in the following code example, they deserialize successfully.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

#### <a name="version-introduced"></a><span data-ttu-id="26def-117">Version introduite</span><span class="sxs-lookup"><span data-stu-id="26def-117">Version introduced</span></span>

<span data-ttu-id="26def-118">5.0</span><span class="sxs-lookup"><span data-stu-id="26def-118">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="26def-119">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="26def-119">Reason for change</span></span>

<span data-ttu-id="26def-120">Des commentaires clients importants ont indiqué que <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> doit être respecté.</span><span class="sxs-lookup"><span data-stu-id="26def-120">Substantial customer feedback indicated that the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> should be honored.</span></span> <span data-ttu-id="26def-121">À des fins d’exhaustivité, les <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> <xref:System.Text.Json.JsonSerializerOptions.Encoder> options et sont également honorées, afin que les <xref:System.Collections.Generic.KeyValuePair%602> instances soient traitées de la même façon que tout autre objet POCO (Plain Old CLR Object).</span><span class="sxs-lookup"><span data-stu-id="26def-121">For completeness, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are also honored, so that <xref:System.Collections.Generic.KeyValuePair%602> instances are treated the same as any other plain old CLR object (POCO).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="26def-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="26def-122">Recommended action</span></span>

<span data-ttu-id="26def-123">Si cette modification s’interrompt, vous pouvez utiliser un [convertisseur personnalisé](../../../../docs/standard/serialization/system-text-json-converters-how-to.md) qui implémente la sémantique souhaitée.</span><span class="sxs-lookup"><span data-stu-id="26def-123">If this change is disruptive to you, you can use a [custom converter](../../../../docs/standard/serialization/system-text-json-converters-how-to.md) that implements the desired semantics.</span></span>

#### <a name="category"></a><span data-ttu-id="26def-124">Category</span><span class="sxs-lookup"><span data-stu-id="26def-124">Category</span></span>

<span data-ttu-id="26def-125">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="26def-125">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26def-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="26def-126">Affected APIs</span></span>

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
