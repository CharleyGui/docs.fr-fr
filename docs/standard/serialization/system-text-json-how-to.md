---
title: Comment sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Découvrez comment utiliser l' System.Text.Json espace de noms pour sérialiser et désérialiser à partir de JSON dans .net. Comprend un exemple de code.
ms.date: 12/02/2020
ms.custom: contperfq2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: dc1f8dab0d8d1ab5001797140a3bbfe4a02cb52b
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918565"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="545d2-104">Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="545d2-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="545d2-105">Cet article explique comment utiliser l' <xref:System.Text.Json?displayProperty=fullName> espace de noms pour sérialiser et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="545d2-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="545d2-106">Si vous transférez du code existant à partir de `Newtonsoft.Json` , consultez [Comment migrer vers `System.Text.Json` ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="545d2-107">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="545d2-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="545d2-108">La majeure partie de l’exemple de code de sérialisation affecte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` la valeur « joli Printing » au format JSON (avec mise en retrait et espace blanc pour la lisibilité humaine).</span><span class="sxs-lookup"><span data-stu-id="545d2-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="545d2-109">Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="545d2-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="545d2-110">Les exemples de code font référence à la classe et aux variantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="545d2-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a><span data-ttu-id="545d2-111">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="545d2-111">Namespaces</span></span>

<span data-ttu-id="545d2-112">L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="545d2-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="545d2-113">L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="545d2-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="545d2-114">Les exemples de code présentés dans cet article requièrent des `using` directives pour l’un de ces espaces de noms ou les deux :</span><span class="sxs-lookup"><span data-stu-id="545d2-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="545d2-115">Les attributs de l' <xref:System.Runtime.Serialization> espace de noms ne sont pas pris en charge dans `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="545d2-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="545d2-116">Comment écrire des objets .NET au format JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="545d2-116">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="545d2-117">Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="545d2-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="545d2-118">L’exemple suivant crée JSON sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="545d2-118">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="545d2-119">L’exemple suivant utilise du code synchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="545d2-119">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="545d2-120">L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="545d2-120">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="545d2-121">Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="545d2-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="545d2-122">Une surcharge de `Serialize()` prend un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="545d2-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="545d2-123">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="545d2-123">Serialization example</span></span>

<span data-ttu-id="545d2-124">Voici un exemple de classe qui contient des propriétés de type collection et un type défini par l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="545d2-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="545d2-125">« POCO » signifie « [Plain Old CLR Object](https://en.wikipedia.org/wiki/Plain_old_CLR_object)».</span><span class="sxs-lookup"><span data-stu-id="545d2-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="545d2-126">Un POCO est un type .NET qui ne dépend d’aucun type spécifique à l’infrastructure, par exemple par le biais de l’héritage ou des attributs.</span><span class="sxs-lookup"><span data-stu-id="545d2-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="545d2-127">La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="545d2-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="545d2-128">La sortie JSON est minimisés (les espaces blancs, les mises en retrait et les caractères de nouvelle ligne sont supprimés) par défaut :</span><span class="sxs-lookup"><span data-stu-id="545d2-128">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="545d2-129">L’exemple suivant montre le même JSON, mais formaté (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="545d2-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

## <a name="serialize-to-utf-8"></a><span data-ttu-id="545d2-130">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="545d2-130">Serialize to UTF-8</span></span>

<span data-ttu-id="545d2-131">Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :</span><span class="sxs-lookup"><span data-stu-id="545d2-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="545d2-132">Une <xref:System.Text.Json.JsonSerializer.Serialize%2A> surcharge qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.</span><span class="sxs-lookup"><span data-stu-id="545d2-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="545d2-133">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="545d2-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="545d2-134">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="545d2-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="545d2-135">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="545d2-135">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="545d2-136">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="545d2-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="545d2-137">Vous pouvez [spécifier des propriétés à ignorer](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-137">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="545d2-138">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="545d2-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="545d2-139">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="545d2-139">By default, JSON is minified.</span></span> <span data-ttu-id="545d2-140">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="545d2-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="545d2-141">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="545d2-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="545d2-142">Vous pouvez [personnaliser la casse du nom JSON](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-142">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="545d2-143">Par défaut, les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="545d2-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="545d2-144">Vous pouvez [conserver les références et gérer les références circulaires](system-text-json-preserve-references.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-144">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="545d2-145">Par défaut, les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="545d2-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="545d2-146">Vous pouvez [inclure des champs](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="545d2-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="545d2-147">Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="545d2-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="545d2-148">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="545d2-148">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="545d2-149">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="545d2-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="545d2-150">Vous pouvez [spécifier des propriétés à ignorer](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-150">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="545d2-151">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="545d2-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="545d2-152">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="545d2-152">By default, JSON is minified.</span></span> <span data-ttu-id="545d2-153">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="545d2-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="545d2-154">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="545d2-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="545d2-155">Vous pouvez [personnaliser la casse du nom JSON](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-155">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="545d2-156">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="545d2-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="545d2-157">Les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="545d2-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="545d2-158">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="545d2-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="545d2-159">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="545d2-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="545d2-160">[Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="545d2-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="545d2-161">Tableaux unidimensionnels et en escalier ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="545d2-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="545d2-162">Collections et dictionnaires à partir des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="545d2-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="545d2-163">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="545d2-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="545d2-164">[Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="545d2-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="545d2-165">Tableaux unidimensionnels et en escalier ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="545d2-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="545d2-166">`Dictionary<string,TValue>` où `TValue` est `object` , `JsonElement` ou un poco.</span><span class="sxs-lookup"><span data-stu-id="545d2-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="545d2-167">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="545d2-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="545d2-168">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="545d2-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="545d2-169">Comment lire JSON en tant qu’objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="545d2-169">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="545d2-170">Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="545d2-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="545d2-171">L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la `WeatherForecastWithPOCOs` classe indiquée précédemment pour l' [exemple de sérialisation](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="545d2-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="545d2-172">Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="545d2-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="545d2-173">Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> méthode :</span><span class="sxs-lookup"><span data-stu-id="545d2-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="545d2-174">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="545d2-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="545d2-175">Pour désérialiser à partir d’UTF-8, appelez une <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> surcharge qui accepte un `ReadOnlySpan<byte>` ou un `Utf8JsonReader` , comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="545d2-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="545d2-176">Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="545d2-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="545d2-177">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="545d2-177">Deserialization behavior</span></span>

<span data-ttu-id="545d2-178">Les comportements suivants s’appliquent lors de la désérialisation de JSON :</span><span class="sxs-lookup"><span data-stu-id="545d2-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="545d2-179">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="545d2-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="545d2-180">Vous pouvez [spécifier le non-respect de la casse](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-180">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="545d2-181">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="545d2-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="545d2-182">Les constructeurs non publics sont ignorés par le sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="545d2-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="545d2-183">La désérialisation des objets immuables ou des propriétés en lecture seule est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="545d2-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="545d2-184">Consultez [les types immuables et les enregistrements](system-text-json-immutability.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-184">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="545d2-185">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="545d2-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="545d2-186">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](system-text-json-customize-properties.md#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="545d2-186">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="545d2-187">Par défaut, les champs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="545d2-187">By default, fields are ignored.</span></span> <span data-ttu-id="545d2-188">Vous pouvez [inclure des champs](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="545d2-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="545d2-189">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="545d2-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="545d2-190">Vous pouvez [autoriser les commentaires et les virgules de fin](system-text-json-invalid-json.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-190">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="545d2-191">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="545d2-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="545d2-192">Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="545d2-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="545d2-193">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="545d2-193">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="545d2-194">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="545d2-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="545d2-195">Vous pouvez [spécifier le non-respect de la casse](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-195">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="545d2-196">Par défaut, les applications ASP.NET Core [spécifient le non-respect](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)de la casse.</span><span class="sxs-lookup"><span data-stu-id="545d2-196">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="545d2-197">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="545d2-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="545d2-198">Un constructeur sans paramètre, qui peut être public, Internal ou Private, est utilisé pour la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="545d2-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="545d2-199">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="545d2-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="545d2-200">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="545d2-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="545d2-201">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](system-text-json-customize-properties.md#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="545d2-201">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="545d2-202">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="545d2-202">Fields aren't supported.</span></span>
* <span data-ttu-id="545d2-203">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="545d2-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="545d2-204">Vous pouvez [autoriser les commentaires et les virgules de fin](system-text-json-invalid-json.md).</span><span class="sxs-lookup"><span data-stu-id="545d2-204">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="545d2-205">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="545d2-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="545d2-206">Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="545d2-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="545d2-207">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="545d2-207">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="545d2-208">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="545d2-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="545d2-209">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="545d2-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="545d2-210">Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true` :</span><span class="sxs-lookup"><span data-stu-id="545d2-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="545d2-211">Voici un exemple de type à sérialiser et à imprimer une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="545d2-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="545d2-212">Si vous utilisez `JsonSerializerOptions` à plusieurs reprises avec les mêmes options, ne créez pas une nouvelle `JsonSerializerOptions` instance à chaque fois que vous l’utilisez.</span><span class="sxs-lookup"><span data-stu-id="545d2-212">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="545d2-213">Réutilisez la même instance pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="545d2-213">Reuse the same instance for every call.</span></span> <span data-ttu-id="545d2-214">Pour plus d’informations, consultez [réutiliser des instances JsonSerializerOptions](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="545d2-214">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="545d2-215">Inclure les champs</span><span class="sxs-lookup"><span data-stu-id="545d2-215">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="545d2-216">Utilisez le <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> paramètre global ou l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) pour inclure les champs lors de la sérialisation ou de la désérialisation, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="545d2-216">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="545d2-217">Pour ignorer les champs en lecture seule, utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.</span><span class="sxs-lookup"><span data-stu-id="545d2-217">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="545d2-218">Les champs ne sont pas pris en charge dans System.Text.Json dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="545d2-218">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="545d2-219">Les [convertisseurs personnalisés](system-text-json-converters-how-to.md) peuvent fournir cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="545d2-219">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="545d2-220">Méthodes d’extension HttpClient et HttpContent</span><span class="sxs-lookup"><span data-stu-id="545d2-220">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="545d2-221">La sérialisation et la désérialisation des charges utiles JSON à partir du réseau sont des opérations courantes.</span><span class="sxs-lookup"><span data-stu-id="545d2-221">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="545d2-222">Les méthodes d’extension sur [httpclient](xref:System.Net.Http.Json.HttpClientJsonExtensions) et [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) vous permettent d’effectuer ces opérations sur une seule ligne de code.</span><span class="sxs-lookup"><span data-stu-id="545d2-222">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="545d2-223">Ces méthodes d’extension utilisent [des valeurs par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="545d2-223">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="545d2-224">L’exemple suivant illustre l’utilisation de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> et <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="545d2-224">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="545d2-225">Il existe également des méthodes d’extension pour System.Text.Json sur [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span><span class="sxs-lookup"><span data-stu-id="545d2-225">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="545d2-226">Les méthodes d’extension sur `HttpClient` et ne `HttpContent` sont pas disponibles dans System.Text.Json dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="545d2-226">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="545d2-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="545d2-227">See also</span></span>

* [<span data-ttu-id="545d2-228">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="545d2-228">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="545d2-229">Guide pratique pour écrire des convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="545d2-229">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="545d2-230">Migration à partir de Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="545d2-230">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="545d2-231">Prise en charge des valeurs DateTime et DateTimeOffset dans System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="545d2-231">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="545d2-232">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="545d2-232">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
