---
title: Comment autoriser certains types de JSON non valide avec System.Text.Json
description: Découvrez comment autoriser les commentaires, les virgules de fin et les nombres entre guillemets lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 12/03/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1b6402952c4765290d22b530834ed831a68bd2fe
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851241"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="3a1bb-103">Comment autoriser certains types de JSON non valide avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3a1bb-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="3a1bb-104">Dans cet article, vous allez apprendre comment autoriser des commentaires, des virgules de fin et des nombres entre guillemets dans JSON, et comment écrire des nombres sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="3a1bb-105">Autoriser les commentaires et les virgules de fin</span><span class="sxs-lookup"><span data-stu-id="3a1bb-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="3a1bb-106">Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="3a1bb-107">Pour autoriser les commentaires dans le JSON, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="3a1bb-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="3a1bb-108">Et pour autoriser les virgules de fin, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="3a1bb-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="3a1bb-109">L’exemple suivant montre comment autoriser les deux :</span><span class="sxs-lookup"><span data-stu-id="3a1bb-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="3a1bb-110">Voici un exemple de code JSON avec des commentaires et une virgule de fin :</span><span class="sxs-lookup"><span data-stu-id="3a1bb-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="3a1bb-111">Autoriser ou écrire des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="3a1bb-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="3a1bb-112">Certains sérialiseurs encodent les nombres sous forme de chaînes JSON (entourées de guillemets).</span><span class="sxs-lookup"><span data-stu-id="3a1bb-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="3a1bb-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3a1bb-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="3a1bb-114">À la place de :</span><span class="sxs-lookup"><span data-stu-id="3a1bb-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="3a1bb-115">Pour sérialiser des nombres entre guillemets ou accepter des nombres dans des guillemets dans le graphique d’objet d’entrée entier, définissez <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3a1bb-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="3a1bb-116">Lorsque vous utilisez `System.Text.Json` indirectement par le biais de ASP.net Core, les nombres entre guillemets sont autorisés lors de la désérialisation, car ASP.net Core spécifie les [options par défaut du Web](xref:System.Text.Json.JsonSerializerDefaults.Web).</span><span class="sxs-lookup"><span data-stu-id="3a1bb-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="3a1bb-117">Pour autoriser ou écrire des nombres entre guillemets pour des propriétés, des champs ou des types spécifiques, utilisez l’attribut [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3a1bb-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="3a1bb-118">`System.Text.Json` dans .NET Core 3,1 ne prend pas en charge la sérialisation ou la désérialisation des nombres placés entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="3a1bb-119">Pour plus d’informations, consultez [autoriser ou écrire des nombres dans des guillemets](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="3a1bb-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="3a1bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a1bb-120">See also</span></span>

* [<span data-ttu-id="3a1bb-121">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="3a1bb-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="3a1bb-122">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="3a1bb-122">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="3a1bb-123">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="3a1bb-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="3a1bb-124">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="3a1bb-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="3a1bb-125">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="3a1bb-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="3a1bb-126">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="3a1bb-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="3a1bb-127">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="3a1bb-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="3a1bb-128">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="3a1bb-128">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="3a1bb-129">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="3a1bb-129">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="3a1bb-130">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3a1bb-130">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
