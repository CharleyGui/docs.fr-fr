---
ms.openlocfilehash: c9547cdc2f127cf13a3610118a26736930fcd8bd
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021608"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="fc96a-101">Modification de la sémantique de `(string)null` dans Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="fc96a-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="fc96a-102">Dans .NET Core 3,0 Preview 7, la chaîne NULL est traitée comme une chaîne vide dans <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="fc96a-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="fc96a-103">À compter de .NET Core 3,0 Preview 8, la chaîne NULL lève une exception lorsqu’elle est utilisée comme nom de propriété et elle émet le jeton null JSON lorsqu’elle est utilisée comme valeur.</span><span class="sxs-lookup"><span data-stu-id="fc96a-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fc96a-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fc96a-104">Change description</span></span>

<span data-ttu-id="fc96a-105">Dans .NET Core 3,0 Preview 7, la `null` chaîne a été traitée `""` comme étant à la fois lors de l’écriture des noms de propriété et lors de l’écriture de valeurs.</span><span class="sxs-lookup"><span data-stu-id="fc96a-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="fc96a-106">À compter de .NET Core 3,0 Preview 8, `null` un nom de propriété lève `ArgumentNullException`une et une `null` valeur est traitée comme un appel à <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> ou <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc96a-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fc96a-107">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fc96a-107">Consider the following code:</span></span>

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

<span data-ttu-id="fc96a-108">Si vous exécutez avec .NET Core 3,0 Preview 7, l’enregistreur produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fc96a-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="fc96a-109">À compter de .NET Core 3,0 Preview 8, l’appel `writer.WriteString(propertyName1, propertyValue1)` à lève une <xref:System.ArgumentNullException>exception.</span><span class="sxs-lookup"><span data-stu-id="fc96a-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="fc96a-110">Si `propertyName1 = null` est remplacé par `propertyName1 = string.Empty`, la sortie est désormais :</span><span class="sxs-lookup"><span data-stu-id="fc96a-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="fc96a-111">Cette modification a été apportée pour améliorer l’alignement `null` avec les attentes de l’appelant pour les valeurs.</span><span class="sxs-lookup"><span data-stu-id="fc96a-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fc96a-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fc96a-112">Version introduced</span></span>

<span data-ttu-id="fc96a-113">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="fc96a-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc96a-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fc96a-114">Recommended action</span></span>

<span data-ttu-id="fc96a-115">Lors de l’écriture des noms de propriété <xref:System.Text.Json.Utf8JsonWriter> et des valeurs avec la classe :</span><span class="sxs-lookup"><span data-stu-id="fc96a-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="fc96a-116">Assurez-`null` vous que les chaînes non-sont utilisées comme noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="fc96a-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="fc96a-117">Si le comportement précédent est souhaité, utilisez un appel de fusion Null ; par exemple, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="fc96a-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="fc96a-118">Si l’écriture `null` d’un littéral `null` pour une valeur de chaîne n’est pas souhaitable, utilisez un appel de fusion Null ; par exemple, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span><span class="sxs-lookup"><span data-stu-id="fc96a-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="fc96a-119">Category</span><span class="sxs-lookup"><span data-stu-id="fc96a-119">Category</span></span>

<span data-ttu-id="fc96a-120">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc96a-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc96a-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="fc96a-121">Affected APIs</span></span>

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->
