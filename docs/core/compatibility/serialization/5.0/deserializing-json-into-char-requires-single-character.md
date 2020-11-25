---
title: 'Modification avec rupture : la désérialisation requiert une chaîne à un seul caractère'
description: Découvrez la modification avec rupture dans .NET 5,0 où JsonSerializer. Deserialize requiert une chaîne à un seul caractère.
ms.date: 10/18/2020
ms.openlocfilehash: 780f2928d776ecb6db9a7fc05a720e889eb363e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761207"
---
# <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="e9aca-103">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="e9aca-103">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="e9aca-104">Lorsque le paramètre de type est <xref:System.Char> , l’argument de chaîne de <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> doit contenir un caractère unique pour que la désérialisation aboutisse.</span><span class="sxs-lookup"><span data-stu-id="e9aca-104">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

## <a name="change-description"></a><span data-ttu-id="e9aca-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e9aca-105">Change description</span></span>

<span data-ttu-id="e9aca-106">Dans les versions précédentes de .NET, si vous transmettez une chaîne de plusieurs caractères à <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> et que le paramètre de type est <xref:System.Char> , la désérialisation réussit et seul le premier caractère est désérialisé.</span><span class="sxs-lookup"><span data-stu-id="e9aca-106">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="e9aca-107">Dans .NET 5,0 et versions ultérieures, lorsque le paramètre de type est <xref:System.Char> , passer tout autre chose qu’une chaîne de caractères simples entraîne la <xref:System.Text.Json.JsonException> levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="e9aca-107">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="e9aca-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e9aca-108">Version introduced</span></span>

<span data-ttu-id="e9aca-109">5.0</span><span class="sxs-lookup"><span data-stu-id="e9aca-109">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e9aca-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e9aca-110">Reason for change</span></span>

<span data-ttu-id="e9aca-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> analyse le texte qui représente une valeur JSON unique dans une instance du type spécifié par le paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="e9aca-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="e9aca-112">L’analyse doit être effectuée uniquement lorsque la charge utile fournie est valide pour le paramètre de type générique spécifié.</span><span class="sxs-lookup"><span data-stu-id="e9aca-112">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="e9aca-113">Pour un <xref:System.Char> type valeur, une charge utile valide est une chaîne de caractères unique.</span><span class="sxs-lookup"><span data-stu-id="e9aca-113">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e9aca-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e9aca-114">Recommended action</span></span>

<span data-ttu-id="e9aca-115">Lors de l’analyse d’une chaîne dans un <xref:System.Char> type à l’aide de, assurez-vous <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> que la chaîne se compose d’un seul caractère.</span><span class="sxs-lookup"><span data-stu-id="e9aca-115">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e9aca-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="e9aca-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
