---
title: 'Modification avec rupture : la sérialisation lève une exception lorsque le paramètre de type est null'
description: Découvrez la modification avec rupture dans .NET 5,0 où les méthodes de sérialisation JsonSerialize qui ont un paramètre de type lèvent désormais une exception chaque fois que la valeur null est passée pour ce paramètre.
ms.date: 10/18/2020
ms.openlocfilehash: af2885394418072ad7efec5855490b5b80152fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761183"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a>JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null

<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> , et les <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> surcharges qui ont un paramètre de type <xref:System.Type> lèvent désormais une exception <xref:System.ArgumentNullException> chaque fois que `null` est passé pour ce paramètre.

## <a name="change-description"></a>Description de la modification

Dans .NET Core 3,1, les <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> surcharges, et qui ont un <xref:System.Type> paramètre lèvent une exception <xref:System.ArgumentNullException> lorsque `null` est passé pour le `Type inputType` paramètre, mais pas si le `Object value` paramètre est également `null` . À compter de .NET 5,0, ces méthodes lèvent *toujours* un <xref:System.ArgumentNullException> lorsque `null` est passé pour le <xref:System.Type> paramètre.

Comportement dans .NET Core 3,1 :

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

Comportement dans .NET 5,0 et versions ultérieures :

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="reason-for-change"></a>Motif de modification

Le passage `null` du `Type inputType` paramètre est inacceptable et doit toujours lever une exception <xref:System.ArgumentNullException> .

## <a name="recommended-action"></a>Action recommandée

Assurez-vous que vous ne passez pas `null` pour le `Type inputType` paramètre de ces méthodes.

## <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
