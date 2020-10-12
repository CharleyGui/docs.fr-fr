---
ms.openlocfilehash: 5b49dcae45e44bfd9ec3e150ad25c3f21d62c18e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955333"
---
### <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="1a0f4-101">JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null</span><span class="sxs-lookup"><span data-stu-id="1a0f4-101">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="1a0f4-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> , et <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> les surcharges qui ont un <xref:System.Type> paramètre lèvent désormais une exception <xref:System.ArgumentNullException> chaque fois que `null` est passé pour le <xref:System.Type> paramètre.</span><span class="sxs-lookup"><span data-stu-id="1a0f4-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter now throw an <xref:System.ArgumentNullException> whenever `null` is passed for the <xref:System.Type> parameter.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1a0f4-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1a0f4-103">Change description</span></span>

<span data-ttu-id="1a0f4-104">Dans .NET Core 3,1, les <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> surcharges, et qui ont un <xref:System.Type> paramètre lèvent une exception <xref:System.ArgumentNullException> lorsque `null` est passé pour le `Type inputType` paramètre, mais pas si le `Object value` paramètre est également `null` .</span><span class="sxs-lookup"><span data-stu-id="1a0f4-104">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="1a0f4-105">À compter de .NET 5,0, ces méthodes lèvent *toujours* un <xref:System.ArgumentNullException> lorsque `null` est passé pour le <xref:System.Type> paramètre.</span><span class="sxs-lookup"><span data-stu-id="1a0f4-105">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="1a0f4-106">Comportement dans .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="1a0f4-106">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="1a0f4-107">Comportement dans .NET 5,0 et versions ultérieures :</span><span class="sxs-lookup"><span data-stu-id="1a0f4-107">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

#### <a name="version-introduced"></a><span data-ttu-id="1a0f4-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1a0f4-108">Version introduced</span></span>

<span data-ttu-id="1a0f4-109">5.0</span><span class="sxs-lookup"><span data-stu-id="1a0f4-109">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1a0f4-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="1a0f4-110">Reason for change</span></span>

<span data-ttu-id="1a0f4-111">Le passage `null` du `Type inputType` paramètre est inacceptable et doit toujours lever une exception <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="1a0f4-111">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1a0f4-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1a0f4-112">Recommended action</span></span>

<span data-ttu-id="1a0f4-113">Assurez-vous que vous ne passez pas `null` pour le `Type inputType` paramètre de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="1a0f4-113">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="1a0f4-114">Category</span><span class="sxs-lookup"><span data-stu-id="1a0f4-114">Category</span></span>

<span data-ttu-id="1a0f4-115">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1a0f4-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a0f4-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="1a0f4-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

-->
