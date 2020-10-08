---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844502"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="7fcca-101">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="7fcca-101">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="7fcca-102">Lorsque le paramètre de type est <xref:System.Char> , l’argument de chaîne de <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> doit contenir un caractère unique pour que la désérialisation aboutisse.</span><span class="sxs-lookup"><span data-stu-id="7fcca-102">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7fcca-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7fcca-103">Change description</span></span>

<span data-ttu-id="7fcca-104">Dans les versions précédentes de .NET, si vous transmettez une chaîne de plusieurs caractères à <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> et que le paramètre de type est <xref:System.Char> , la désérialisation réussit et seul le premier caractère est désérialisé.</span><span class="sxs-lookup"><span data-stu-id="7fcca-104">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="7fcca-105">Dans .NET 5,0 et versions ultérieures, lorsque le paramètre de type est <xref:System.Char> , passer tout autre chose qu’une chaîne de caractères simples entraîne la <xref:System.Text.Json.JsonException> levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="7fcca-105">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a><span data-ttu-id="7fcca-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7fcca-106">Version introduced</span></span>

<span data-ttu-id="7fcca-107">5.0</span><span class="sxs-lookup"><span data-stu-id="7fcca-107">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7fcca-108">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7fcca-108">Reason for change</span></span>

<span data-ttu-id="7fcca-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> analyse le texte qui représente une valeur JSON unique dans une instance du type spécifié par le paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="7fcca-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="7fcca-110">L’analyse doit être effectuée uniquement lorsque la charge utile fournie est valide pour le paramètre de type générique spécifié.</span><span class="sxs-lookup"><span data-stu-id="7fcca-110">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="7fcca-111">Pour un <xref:System.Char> type valeur, une charge utile valide est une chaîne de caractères unique.</span><span class="sxs-lookup"><span data-stu-id="7fcca-111">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7fcca-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7fcca-112">Recommended action</span></span>

<span data-ttu-id="7fcca-113">Lors de l’analyse d’une chaîne dans un <xref:System.Char> type à l’aide de, assurez-vous <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> que la chaîne se compose d’un seul caractère.</span><span class="sxs-lookup"><span data-stu-id="7fcca-113">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

#### <a name="category"></a><span data-ttu-id="7fcca-114">Category</span><span class="sxs-lookup"><span data-stu-id="7fcca-114">Category</span></span>

<span data-ttu-id="7fcca-115">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="7fcca-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7fcca-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="7fcca-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->
