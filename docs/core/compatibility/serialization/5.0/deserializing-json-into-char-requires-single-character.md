---
title: 'Modification avec rupture : la désérialisation de char requiert une chaîne à un seul caractère'
description: Découvrez la modification avec rupture dans .NET 5,0 où System.Text.Jssur requiert une chaîne à un seul caractère dans le JSON lors de la désérialisation vers une cible char.
ms.date: 12/15/2020
ms.openlocfilehash: 39a2d25b00bf8855cfbf46a4d78b8545052703e5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633869"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a><span data-ttu-id="2f969-103">System.Text.Jssur requiert une chaîne à un seul caractère pour désérialiser un caractère</span><span class="sxs-lookup"><span data-stu-id="2f969-103">System.Text.Json requires single-char string to deserialize a char</span></span>

<span data-ttu-id="2f969-104">Pour désérialiser avec succès un <xref:System.Char> à l’aide de <xref:System.Text.Json> , la chaîne JSON doit contenir un seul caractère.</span><span class="sxs-lookup"><span data-stu-id="2f969-104">To successfully deserialize a <xref:System.Char> using <xref:System.Text.Json>, the JSON string must contain a single character.</span></span>

## <a name="change-description"></a><span data-ttu-id="2f969-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="2f969-105">Change description</span></span>

<span data-ttu-id="2f969-106">Dans les versions précédentes de .NET, une `char` chaîne multiple dans le JSON est correctement désérialisée en une `char` propriété ou un champ.</span><span class="sxs-lookup"><span data-stu-id="2f969-106">In previous .NET versions, a multi-`char` string in the JSON is successfully deserialized to a `char` property or field.</span></span> <span data-ttu-id="2f969-107">Seul le premier `char` de la chaîne est utilisé, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2f969-107">Only the first `char` of the string is used, as in the following example:</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

<span data-ttu-id="2f969-108">Dans .NET 5,0 et versions ultérieures, toute autre chose qu’une `char` chaîne unique entraîne <xref:System.Text.Json.JsonException> la levée d’une exception lorsque la cible de désérialisation est un `char` .</span><span class="sxs-lookup"><span data-stu-id="2f969-108">In .NET 5.0 and later, anything other than a single-`char` string causes a <xref:System.Text.Json.JsonException> to be thrown when the deserialization target is a `char`.</span></span> <span data-ttu-id="2f969-109">L’exemple de chaîne suivant est correctement désérialisé dans toutes les versions de .NET :</span><span class="sxs-lookup"><span data-stu-id="2f969-109">The following example string is successfully deserialized in all .NET versions:</span></span>

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="2f969-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2f969-110">Version introduced</span></span>

<span data-ttu-id="2f969-111">5.0</span><span class="sxs-lookup"><span data-stu-id="2f969-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2f969-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2f969-112">Reason for change</span></span>

<span data-ttu-id="2f969-113">L’analyse de la désérialisation doit être effectuée uniquement lorsque la charge utile fournie est valide pour le type cible.</span><span class="sxs-lookup"><span data-stu-id="2f969-113">Parsing for deserialization should only succeed when the provided payload is valid for the target type.</span></span> <span data-ttu-id="2f969-114">Pour un `char` type, la seule charge utile valide est une `char` chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="2f969-114">For a `char` type, the only valid payload is a single-`char` string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2f969-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2f969-115">Recommended action</span></span>

<span data-ttu-id="2f969-116">Lorsque vous désérialisez JSON dans une cible, assurez-vous `char` que la chaîne est constituée d’un seul `char` .</span><span class="sxs-lookup"><span data-stu-id="2f969-116">When you deserialize JSON into a `char` target, make sure the string consists of a single `char`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2f969-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="2f969-117">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
