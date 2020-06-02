---
title: Comment sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Cet article explique comment utiliser l’espace de System.Text.Json noms pour sérialiser et désérialiser à partir de JSON dans .net. Il comprend un exemple de code.
ms.date: 05/13/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 7ad2721f12c5d14b61b35ecf7696ff0d6a6f27da
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289510"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="eab0d-104">Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="eab0d-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="eab0d-105">Cet article explique comment utiliser l' <xref:System.Text.Json> espace de noms pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="eab0d-105">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="eab0d-106">Si vous transférez du code existant à partir de `Newtonsoft.Json` , consultez [Comment migrer vers `System.Text.Json` ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="eab0d-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="eab0d-107">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="eab0d-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="eab0d-108">La majeure partie de l’exemple de code de sérialisation affecte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` la valeur « joli Printing » au format JSON (avec mise en retrait et espace blanc pour la lisibilité humaine).</span><span class="sxs-lookup"><span data-stu-id="eab0d-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="eab0d-109">Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eab0d-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="eab0d-110">Les exemples de code font référence à la classe et aux variantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="eab0d-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="eab0d-111">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="eab0d-111">Namespaces</span></span>

<span data-ttu-id="eab0d-112">L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="eab0d-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="eab0d-113">L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="eab0d-114">Les exemples de code présentés dans cet article requièrent des `using` directives pour l’un de ces espaces de noms ou les deux :</span><span class="sxs-lookup"><span data-stu-id="eab0d-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="eab0d-115">Les attributs de l' <xref:System.Runtime.Serialization> espace de noms ne sont actuellement pas pris en charge dans `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="eab0d-116">Comment écrire des objets .NET dans JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="eab0d-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="eab0d-117">Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="eab0d-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="eab0d-118">L’exemple suivant crée JSON sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="eab0d-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-119">L’exemple suivant utilise du code synchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-120">L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-121">Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="eab0d-122">Une surcharge de `Serialize()` prend un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="eab0d-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="eab0d-123">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="eab0d-123">Serialization example</span></span>

<span data-ttu-id="eab0d-124">Voici un exemple de classe qui contient des collections et une classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="eab0d-124">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="eab0d-125">La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eab0d-125">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="eab0d-126">La sortie JSON est minimisés par défaut :</span><span class="sxs-lookup"><span data-stu-id="eab0d-126">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="eab0d-127">L’exemple suivant montre le même JSON, mis en forme (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="eab0d-127">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="eab0d-128">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="eab0d-128">Serialize to UTF-8</span></span>

<span data-ttu-id="eab0d-129">Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :</span><span class="sxs-lookup"><span data-stu-id="eab0d-129">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-130">Une <xref:System.Text.Json.JsonSerializer.Serialize%2A> surcharge qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.</span><span class="sxs-lookup"><span data-stu-id="eab0d-130">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="eab0d-131">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="eab0d-131">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="eab0d-132">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="eab0d-132">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="eab0d-133">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="eab0d-133">Serialization behavior</span></span>

* <span data-ttu-id="eab0d-134">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="eab0d-134">By default, all public properties are serialized.</span></span> <span data-ttu-id="eab0d-135">Vous pouvez [spécifier les propriétés à exclure](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="eab0d-135">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="eab0d-136">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="eab0d-136">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="eab0d-137">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-137">By default, JSON is minified.</span></span> <span data-ttu-id="eab0d-138">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="eab0d-138">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="eab0d-139">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="eab0d-139">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="eab0d-140">Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="eab0d-140">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="eab0d-141">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="eab0d-141">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="eab0d-142">Actuellement, les champs sont exclus.</span><span class="sxs-lookup"><span data-stu-id="eab0d-142">Currently, fields are excluded.</span></span>

<span data-ttu-id="eab0d-143">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="eab0d-143">Supported types include:</span></span>

* <span data-ttu-id="eab0d-144">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="eab0d-144">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="eab0d-145">[Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="eab0d-145">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="eab0d-146">Tableaux unidimensionnels et en escalier ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="eab0d-146">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="eab0d-147">`Dictionary<string,TValue>`où `TValue` est `object` , `JsonElement` ou un poco.</span><span class="sxs-lookup"><span data-stu-id="eab0d-147">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="eab0d-148">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="eab0d-148">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="eab0d-149">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-149">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="eab0d-150">Comment lire JSON dans des objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="eab0d-150">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="eab0d-151">Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="eab0d-151">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="eab0d-152">L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la `WeatherForecast` classe indiquée précédemment pour l' [exemple de sérialisation](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="eab0d-152">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="eab0d-153">Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-153">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="eab0d-154">Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> méthode :</span><span class="sxs-lookup"><span data-stu-id="eab0d-154">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="eab0d-155">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="eab0d-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="eab0d-156">Pour désérialiser à partir d’UTF-8, appelez une <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> surcharge qui accepte un `Utf8JsonReader` ou un `ReadOnlySpan<byte>` , comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="eab0d-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="eab0d-157">Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="eab0d-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="eab0d-158">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="eab0d-158">Deserialization behavior</span></span>

* <span data-ttu-id="eab0d-159">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="eab0d-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="eab0d-160">Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="eab0d-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="eab0d-161">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="eab0d-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="eab0d-162">La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="eab0d-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="eab0d-163">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="eab0d-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="eab0d-164">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="eab0d-164">By default, enums are supported as numbers.</span></span> <span data-ttu-id="eab0d-165">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="eab0d-165">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="eab0d-166">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="eab0d-166">Fields aren't supported.</span></span>
* <span data-ttu-id="eab0d-167">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="eab0d-167">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="eab0d-168">Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="eab0d-168">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="eab0d-169">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="eab0d-169">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="eab0d-170">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-170">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="eab0d-171">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="eab0d-171">Serialize to formatted JSON</span></span>

<span data-ttu-id="eab0d-172">Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-172">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="eab0d-173">Voici un exemple de type à sérialiser et à imprimer une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-173">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="eab0d-174">Personnaliser les noms et les valeurs JSON</span><span class="sxs-lookup"><span data-stu-id="eab0d-174">Customize JSON names and values</span></span>

<span data-ttu-id="eab0d-175">Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse.</span><span class="sxs-lookup"><span data-stu-id="eab0d-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="eab0d-176">Les valeurs enum sont représentées sous forme de nombres.</span><span class="sxs-lookup"><span data-stu-id="eab0d-176">Enum values are represented as numbers.</span></span> <span data-ttu-id="eab0d-177">Cette section explique comment :</span><span class="sxs-lookup"><span data-stu-id="eab0d-177">This section explains how to:</span></span>

* [<span data-ttu-id="eab0d-178">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="eab0d-178">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="eab0d-179">Convertir tous les noms de propriété en casse mixte</span><span class="sxs-lookup"><span data-stu-id="eab0d-179">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="eab0d-180">Implémenter une stratégie d’attribution de noms de propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="eab0d-180">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="eab0d-181">Convertir les clés du dictionnaire en casse mixte</span><span class="sxs-lookup"><span data-stu-id="eab0d-181">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="eab0d-182">Convertir des enums en chaînes et casse mixte</span><span class="sxs-lookup"><span data-stu-id="eab0d-182">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="eab0d-183">Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="eab0d-183">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="eab0d-184">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="eab0d-184">Customize individual property names</span></span>

<span data-ttu-id="eab0d-185">Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="eab0d-185">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="eab0d-186">Voici un exemple de type pour sérialiser et JSON obtenu :</span><span class="sxs-lookup"><span data-stu-id="eab0d-186">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="eab0d-187">Nom de propriété défini par cet attribut :</span><span class="sxs-lookup"><span data-stu-id="eab0d-187">The property name set by this attribute:</span></span>

* <span data-ttu-id="eab0d-188">S’applique dans les deux directions, pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-188">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="eab0d-189">Est prioritaire sur les stratégies d’attribution de noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="eab0d-189">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="eab0d-190">Utiliser la casse mixte pour tous les noms de propriété JSON</span><span class="sxs-lookup"><span data-stu-id="eab0d-190">Use camel case for all JSON property names</span></span>

<span data-ttu-id="eab0d-191">Pour utiliser la casse mixte pour tous les noms de propriétés JSON, affectez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> la valeur à `JsonNamingPolicy.CamelCase` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-191">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="eab0d-192">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-192">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="eab0d-193">La stratégie de nommage de propriété casse mixte :</span><span class="sxs-lookup"><span data-stu-id="eab0d-193">The camel case property naming policy:</span></span>

* <span data-ttu-id="eab0d-194">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-194">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="eab0d-195">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="eab0d-195">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="eab0d-196">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.</span><span class="sxs-lookup"><span data-stu-id="eab0d-196">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="eab0d-197">Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée</span><span class="sxs-lookup"><span data-stu-id="eab0d-197">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="eab0d-198">Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> méthode, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-198">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="eab0d-199">Définissez ensuite la <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :</span><span class="sxs-lookup"><span data-stu-id="eab0d-199">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-200">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-200">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="eab0d-201">La stratégie d’attribution de noms de propriété JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-201">The JSON property naming policy:</span></span>

* <span data-ttu-id="eab0d-202">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-202">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="eab0d-203">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="eab0d-203">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="eab0d-204">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.</span><span class="sxs-lookup"><span data-stu-id="eab0d-204">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="eab0d-205">Clés de dictionnaire de casse mixte</span><span class="sxs-lookup"><span data-stu-id="eab0d-205">Camel case dictionary keys</span></span>

<span data-ttu-id="eab0d-206">Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>` , les `string` clés peuvent être converties en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="eab0d-206">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="eab0d-207">Pour ce faire, affectez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> à `JsonNamingPolicy.CamelCase` la valeur, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-207">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-208">La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` provoquerait une sortie JSON similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-208">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="eab0d-209">La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-209">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="eab0d-210">Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-210">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="eab0d-211">Enums en tant que chaînes</span><span class="sxs-lookup"><span data-stu-id="eab0d-211">Enums as strings</span></span>

<span data-ttu-id="eab0d-212">Par défaut, les enums sont sérialisés en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="eab0d-212">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="eab0d-213">Pour sérialiser les noms d’enum sous forme de chaînes, utilisez <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="eab0d-213">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="eab0d-214">Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :</span><span class="sxs-lookup"><span data-stu-id="eab0d-214">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="eab0d-215">Si le résumé est `Hot` , par défaut, le JSON sérialisé a la valeur numérique 3 :</span><span class="sxs-lookup"><span data-stu-id="eab0d-215">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="eab0d-216">L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :</span><span class="sxs-lookup"><span data-stu-id="eab0d-216">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-217">Le JSON obtenu ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-217">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="eab0d-218">Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-218">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="eab0d-219">Exclure des propriétés de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="eab0d-219">Exclude properties from serialization</span></span>

<span data-ttu-id="eab0d-220">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="eab0d-220">By default, all public properties are serialized.</span></span> <span data-ttu-id="eab0d-221">Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="eab0d-221">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="eab0d-222">Cette section explique comment exclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="eab0d-222">This section explains how to exclude:</span></span>

* [<span data-ttu-id="eab0d-223">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="eab0d-223">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="eab0d-224">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="eab0d-224">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="eab0d-225">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="eab0d-225">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="eab0d-226">Exclure des propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="eab0d-226">Exclude individual properties</span></span>

<span data-ttu-id="eab0d-227">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="eab0d-227">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="eab0d-228">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="eab0d-229">Exclure toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="eab0d-229">Exclude all read-only properties</span></span>

<span data-ttu-id="eab0d-230">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="eab0d-230">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="eab0d-231">Pour exclure toutes les propriétés en lecture seule, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> à `true` , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-231">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-232">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-232">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="eab0d-233">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-233">This option applies only to serialization.</span></span> <span data-ttu-id="eab0d-234">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="eab0d-234">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="eab0d-235">Exclure toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="eab0d-235">Exclude all null value properties</span></span>

<span data-ttu-id="eab0d-236">Pour exclure toutes les propriétés de valeur null, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> `true` , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-236">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-237">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-237">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="eab0d-238">Propriété</span><span class="sxs-lookup"><span data-stu-id="eab0d-238">Property</span></span> |<span data-ttu-id="eab0d-239">Valeur</span><span class="sxs-lookup"><span data-stu-id="eab0d-239">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="eab0d-240">Date</span><span class="sxs-lookup"><span data-stu-id="eab0d-240">Date</span></span>    | <span data-ttu-id="eab0d-241">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="eab0d-241">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="eab0d-242">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="eab0d-242">TemperatureCelsius</span></span>| <span data-ttu-id="eab0d-243">25</span><span class="sxs-lookup"><span data-stu-id="eab0d-243">25</span></span> |
| <span data-ttu-id="eab0d-244">Résumé</span><span class="sxs-lookup"><span data-stu-id="eab0d-244">Summary</span></span>| <span data-ttu-id="eab0d-245">null</span><span class="sxs-lookup"><span data-stu-id="eab0d-245">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="eab0d-246">Ce paramètre s’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-246">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="eab0d-247">Pour plus d’informations sur son effet sur la désérialisation, consultez [ignorer la valeur null lors de la désérialisation](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="eab0d-247">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="eab0d-248">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="eab0d-248">Customize character encoding</span></span>

<span data-ttu-id="eab0d-249">Par défaut, le sérialiseur échappe tous les caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="eab0d-249">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="eab0d-250">Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.</span><span class="sxs-lookup"><span data-stu-id="eab0d-250">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="eab0d-251">Par exemple, si la `Summary` propriété a la valeur cyrillique Жарко, l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="eab0d-251">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="eab0d-252">Sérialiser les jeux de caractères de la langue</span><span class="sxs-lookup"><span data-stu-id="eab0d-252">Serialize language character sets</span></span>

<span data-ttu-id="eab0d-253">Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-253">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="eab0d-254">Ce code n’échappe pas aux caractères cyrilliques ou grecs.</span><span class="sxs-lookup"><span data-stu-id="eab0d-254">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="eab0d-255">Si la `Summary` propriété a la valeur cyrillique Жарко, l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="eab0d-255">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="eab0d-256">Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="eab0d-256">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="eab0d-257">Sérialiser des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="eab0d-257">Serialize specific characters</span></span>

<span data-ttu-id="eab0d-258">Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-258">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="eab0d-259">L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :</span><span class="sxs-lookup"><span data-stu-id="eab0d-259">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="eab0d-260">Voici un exemple de JSON généré par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="eab0d-260">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="eab0d-261">Sérialiser tous les caractères</span><span class="sxs-lookup"><span data-stu-id="eab0d-261">Serialize all characters</span></span>

<span data-ttu-id="eab0d-262">Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-262">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="eab0d-263">Par rapport à l’encodeur par défaut, l' `UnsafeRelaxedJsonEscaping` encodeur est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :</span><span class="sxs-lookup"><span data-stu-id="eab0d-263">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="eab0d-264">Elle n’échappe pas les caractères HTML, tels que `<` ,, `>` `&` et `'` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-264">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="eab0d-265">Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu*de caractères.</span><span class="sxs-lookup"><span data-stu-id="eab0d-265">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="eab0d-266">Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="eab0d-266">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="eab0d-267">Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-267">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="eab0d-268">N’autorisez jamais l' `UnsafeRelaxedJsonEscaping` émission de la sortie brute dans une page HTML ou un `<script>` élément.</span><span class="sxs-lookup"><span data-stu-id="eab0d-268">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="eab0d-269">Sérialiser les propriétés des classes dérivées</span><span class="sxs-lookup"><span data-stu-id="eab0d-269">Serialize properties of derived classes</span></span>

<span data-ttu-id="eab0d-270">La sérialisation d’une hiérarchie de type polymorphe n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="eab0d-270">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="eab0d-271">Par exemple, si une propriété est définie comme une interface ou une classe abstraite, seules les propriétés définies sur l’interface ou la classe abstraite sont sérialisées, même si le type de runtime a des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="eab0d-271">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="eab0d-272">Les exceptions à ce comportement sont expliquées dans cette section.</span><span class="sxs-lookup"><span data-stu-id="eab0d-272">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="eab0d-273">Par exemple, supposons que vous avez une `WeatherForecast` classe et une classe dérivée `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="eab0d-274">Et supposons que l’argument de type de la `Serialize` méthode au moment de la compilation est `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="eab0d-275">Dans ce scénario, la `WindSpeed` propriété n’est pas sérialisée, même si l' `weatherForecast` objet est en fait un `WeatherForecastDerived` objet.</span><span class="sxs-lookup"><span data-stu-id="eab0d-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="eab0d-276">Seules les propriétés de la classe de base sont sérialisées :</span><span class="sxs-lookup"><span data-stu-id="eab0d-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="eab0d-277">Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.</span><span class="sxs-lookup"><span data-stu-id="eab0d-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="eab0d-278">Pour sérialiser les propriétés du type dérivé dans l’exemple précédent, utilisez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="eab0d-278">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="eab0d-279">Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="eab0d-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="eab0d-280">Déclarez l’objet à sérialiser en tant que `object` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-280">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="eab0d-281">Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la `WindSpeed` propriété dans la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="eab0d-282">Ces approches fournissent la sérialisation polymorphe uniquement pour l’objet racine à sérialiser, et non pour les propriétés de cet objet racine.</span><span class="sxs-lookup"><span data-stu-id="eab0d-282">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="eab0d-283">Vous pouvez obtenir la sérialisation polymorphe pour les objets de niveau inférieur si vous les définissez en tant que type `object` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-283">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="eab0d-284">Par exemple, supposons que votre `WeatherForecast` classe ait une propriété nommée `PreviousForecast` qui peut être définie en tant que type `WeatherForecast` ou `object` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-284">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="eab0d-285">Si la `PreviousForecast` propriété contient une instance de `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-285">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="eab0d-286">La sortie JSON de la sérialisation `WeatherForecastWithPrevious` **n’inclut pas** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-286">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="eab0d-287">La sortie JSON de la sérialisation `WeatherForecastWithPreviousAsObject` **comprend** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-287">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="eab0d-288">Pour sérialiser `WeatherForecastWithPreviousAsObject` , il n’est pas nécessaire d’appeler `Serialize<object>` ou `GetType` parce que l’objet racine n’est pas celui d’un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="eab0d-288">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="eab0d-289">L’exemple de code suivant n’appelle pas `Serialize<object>` ou `GetType` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-289">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="eab0d-290">Le code précédent sérialise correctement `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-290">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="eab0d-291">La même approche de la définition des propriétés `object` fonctionne avec les interfaces.</span><span class="sxs-lookup"><span data-stu-id="eab0d-291">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="eab0d-292">Supposons que vous disposez de l’interface et de l’implémentation suivantes, et que vous souhaitez sérialiser une classe avec des propriétés qui contiennent des instances d’implémentation :</span><span class="sxs-lookup"><span data-stu-id="eab0d-292">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="eab0d-293">Lorsque vous sérialisez une instance de `Forecasts` , `Tuesday` affiche uniquement la `WindSpeed` propriété, car `Tuesday` est défini comme `object` suit :</span><span class="sxs-lookup"><span data-stu-id="eab0d-293">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="eab0d-294">L’exemple suivant montre le code JSON qui résulte du code précédent :</span><span class="sxs-lookup"><span data-stu-id="eab0d-294">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="eab0d-295">Pour plus d’informations sur **la sérialisation**polymorphe et sur la **désérialisation**, consultez [Comment migrer de Newtonsoft.Json vers System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="eab0d-295">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="eab0d-296">Autoriser les commentaires et les virgules de fin</span><span class="sxs-lookup"><span data-stu-id="eab0d-296">Allow comments and trailing commas</span></span>

<span data-ttu-id="eab0d-297">Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-297">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="eab0d-298">Pour autoriser les commentaires dans le JSON, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-298">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="eab0d-299">Et pour autoriser les virgules de fin, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-299">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="eab0d-300">L’exemple suivant montre comment autoriser les deux :</span><span class="sxs-lookup"><span data-stu-id="eab0d-300">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="eab0d-301">Voici un exemple de code JSON avec des commentaires et une virgule de fin :</span><span class="sxs-lookup"><span data-stu-id="eab0d-301">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="eab0d-302">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="eab0d-302">Case-insensitive property matching</span></span>

<span data-ttu-id="eab0d-303">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="eab0d-303">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="eab0d-304">Pour modifier ce comportement, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-304">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="eab0d-305">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="eab0d-305">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="eab0d-306">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="eab0d-306">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="eab0d-307">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="eab0d-307">Handle overflow JSON</span></span>

<span data-ttu-id="eab0d-308">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="eab0d-308">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="eab0d-309">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-309">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="eab0d-310">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-310">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="eab0d-311">Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` `SummaryWords` Propriétés et ne sont pas visibles et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="eab0d-311">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="eab0d-312">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de type `Dictionary<string,object>` ou `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="eab0d-312">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="eab0d-313">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la `ExtensionData` propriété :</span><span class="sxs-lookup"><span data-stu-id="eab0d-313">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="eab0d-314">Propriété</span><span class="sxs-lookup"><span data-stu-id="eab0d-314">Property</span></span> |<span data-ttu-id="eab0d-315">Valeur</span><span class="sxs-lookup"><span data-stu-id="eab0d-315">Value</span></span>  |<span data-ttu-id="eab0d-316">Notes</span><span class="sxs-lookup"><span data-stu-id="eab0d-316">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="eab0d-317">Date</span><span class="sxs-lookup"><span data-stu-id="eab0d-317">Date</span></span>    | <span data-ttu-id="eab0d-318">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="eab0d-318">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="eab0d-319">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="eab0d-319">TemperatureCelsius</span></span>| <span data-ttu-id="eab0d-320">0</span><span class="sxs-lookup"><span data-stu-id="eab0d-320">0</span></span> | <span data-ttu-id="eab0d-321">Incompatibilité sensible à la casse ( `temperatureCelsius` dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="eab0d-321">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="eab0d-322">Résumé</span><span class="sxs-lookup"><span data-stu-id="eab0d-322">Summary</span></span> | <span data-ttu-id="eab0d-323">À chaud</span><span class="sxs-lookup"><span data-stu-id="eab0d-323">Hot</span></span> ||
| <span data-ttu-id="eab0d-324">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="eab0d-324">ExtensionData</span></span> | <span data-ttu-id="eab0d-325">temperatureCelsius : 25</span><span class="sxs-lookup"><span data-stu-id="eab0d-325">temperatureCelsius: 25</span></span> |<span data-ttu-id="eab0d-326">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="eab0d-326">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="eab0d-327">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="eab0d-327">DatesAvailable:</span></span><br>  <span data-ttu-id="eab0d-328">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="eab0d-328">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="eab0d-329">DE 8/2/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="eab0d-329">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="eab0d-330">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="eab0d-330">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="eab0d-331">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="eab0d-331">SummaryWords:</span></span><br><span data-ttu-id="eab0d-332">À froid</span><span class="sxs-lookup"><span data-stu-id="eab0d-332">Cool</span></span><br><span data-ttu-id="eab0d-333">Venteux</span><span class="sxs-lookup"><span data-stu-id="eab0d-333">Windy</span></span><br><span data-ttu-id="eab0d-334">Humide</span><span class="sxs-lookup"><span data-stu-id="eab0d-334">Humid</span></span> |<span data-ttu-id="eab0d-335">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="eab0d-335">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="eab0d-336">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-336">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="eab0d-337">Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-337">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="eab0d-338">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="eab0d-338">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="eab0d-339">Ignorer la valeur null lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="eab0d-339">Ignore null when deserializing</span></span>

<span data-ttu-id="eab0d-340">Par défaut, si une propriété dans JSON a la valeur null, la propriété correspondante dans l’objet cible a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="eab0d-340">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="eab0d-341">Dans certains scénarios, la propriété cible peut avoir une valeur par défaut et vous ne souhaitez pas qu’une valeur null remplace la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="eab0d-341">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="eab0d-342">Par exemple, supposons que le code suivant représente votre objet cible :</span><span class="sxs-lookup"><span data-stu-id="eab0d-342">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="eab0d-343">Et supposons que le code JSON suivant est désérialisé :</span><span class="sxs-lookup"><span data-stu-id="eab0d-343">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="eab0d-344">Après la désérialisation, la `Summary` propriété de l' `WeatherForecastWithDefault` objet a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="eab0d-344">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="eab0d-345">Pour modifier ce comportement, affectez <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> à `true` la valeur, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-345">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="eab0d-346">Avec cette option, la `Summary` propriété de l' `WeatherForecastWithDefault` objet est la valeur par défaut « no Summary » après la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eab0d-346">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="eab0d-347">Les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides.</span><span class="sxs-lookup"><span data-stu-id="eab0d-347">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="eab0d-348">Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="eab0d-348">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="eab0d-349">Utf8JsonReader, Utf8JsonWriter et JsonDocument</span><span class="sxs-lookup"><span data-stu-id="eab0d-349">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="eab0d-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un ou d’un `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="eab0d-351">Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-351">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="eab0d-352">La <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonReader` couvertures.</span><span class="sxs-lookup"><span data-stu-id="eab0d-352">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="eab0d-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants tels que `String` , `Int32` et `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="eab0d-354">Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-354">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="eab0d-355">La <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonWriter` couvertures.</span><span class="sxs-lookup"><span data-stu-id="eab0d-355">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="eab0d-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>offre la possibilité de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="eab0d-357">Le DOM fournit un accès aléatoire aux données dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-357">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="eab0d-358">Les éléments JSON qui composent la charge utile sont accessibles via le <xref:System.Text.Json.JsonElement> type.</span><span class="sxs-lookup"><span data-stu-id="eab0d-358">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="eab0d-359">Le `JsonElement` type fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .net courants.</span><span class="sxs-lookup"><span data-stu-id="eab0d-359">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="eab0d-360">`JsonDocument`expose une <xref:System.Text.Json.JsonDocument.RootElement> propriété.</span><span class="sxs-lookup"><span data-stu-id="eab0d-360">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="eab0d-361">Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-361">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="eab0d-362">Utiliser JsonDocument pour l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="eab0d-362">Use JsonDocument for access to data</span></span>

<span data-ttu-id="eab0d-363">L’exemple suivant montre comment utiliser la <xref:System.Text.Json.JsonDocument> classe pour l’accès aléatoire aux données d’une chaîne JSON :</span><span class="sxs-lookup"><span data-stu-id="eab0d-363">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="eab0d-364">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="eab0d-364">The preceding code:</span></span>

* <span data-ttu-id="eab0d-365">Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-365">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="eab0d-366">Calcule une qualité moyenne pour les objets d’un `Students` tableau qui ont une `Grade` propriété.</span><span class="sxs-lookup"><span data-stu-id="eab0d-366">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="eab0d-367">Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.</span><span class="sxs-lookup"><span data-stu-id="eab0d-367">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="eab0d-368">Compte les élèves en incrémentant une `count` variable à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="eab0d-368">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="eab0d-369">Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-369">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="eab0d-370">Voici un exemple du JSON traité par ce code :</span><span class="sxs-lookup"><span data-stu-id="eab0d-370">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="eab0d-371">Utiliser JsonDocument pour écrire du code JSON</span><span class="sxs-lookup"><span data-stu-id="eab0d-371">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="eab0d-372">L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="eab0d-372">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="eab0d-373">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="eab0d-373">The preceding code:</span></span>

* <span data-ttu-id="eab0d-374">Lit un fichier JSON, charge les données dans un `JsonDocument` et écrit le format JSON (Pretty-imprimed) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="eab0d-374">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="eab0d-375">Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.</span><span class="sxs-lookup"><span data-stu-id="eab0d-375">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="eab0d-376">Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer.</span><span class="sxs-lookup"><span data-stu-id="eab0d-376">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="eab0d-377">Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="eab0d-377">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="eab0d-378">Voici un exemple d’entrée JSON à traiter par l’exemple de code :</span><span class="sxs-lookup"><span data-stu-id="eab0d-378">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="eab0d-379">Le résultat est la sortie JSON imprimée suivante :</span><span class="sxs-lookup"><span data-stu-id="eab0d-379">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="eab0d-380">Utiliser Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="eab0d-380">Use Utf8JsonWriter</span></span>

<span data-ttu-id="eab0d-381">L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonWriter> classe :</span><span class="sxs-lookup"><span data-stu-id="eab0d-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="eab0d-382">Utiliser Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="eab0d-382">Use Utf8JsonReader</span></span>

<span data-ttu-id="eab0d-383">L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonReader> classe :</span><span class="sxs-lookup"><span data-stu-id="eab0d-383">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="eab0d-384">Le code précédent suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="eab0d-384">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="eab0d-385">Filtrer les données à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="eab0d-385">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="eab0d-386">L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur :</span><span class="sxs-lookup"><span data-stu-id="eab0d-386">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="eab0d-387">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="eab0d-387">The preceding code:</span></span>

* <span data-ttu-id="eab0d-388">Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="eab0d-388">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="eab0d-389">Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».</span><span class="sxs-lookup"><span data-stu-id="eab0d-389">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="eab0d-390">Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="eab0d-390">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="eab0d-391">Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>` , à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="eab0d-391">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="eab0d-392">Si le fichier contient une marque d’ordre d’octet (BOM) UTF-8, supprimez-le avant de passer les octets au `Utf8JsonReader` , puisque le lecteur attend du texte.</span><span class="sxs-lookup"><span data-stu-id="eab0d-392">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="eab0d-393">Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="eab0d-393">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="eab0d-394">Voici un exemple JSON que le code précédent peut lire.</span><span class="sxs-lookup"><span data-stu-id="eab0d-394">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="eab0d-395">Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :</span><span class="sxs-lookup"><span data-stu-id="eab0d-395">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="eab0d-396">Lire à partir d’un flux à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="eab0d-396">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="eab0d-397">Lors de la lecture d’un fichier volumineux (un gigaoctet ou plus en taille, par exemple), vous pouvez éviter d’avoir à charger la totalité du fichier en mémoire en même temps.</span><span class="sxs-lookup"><span data-stu-id="eab0d-397">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="eab0d-398">Pour ce scénario, vous pouvez utiliser un <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="eab0d-398">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="eab0d-399">Lorsque vous utilisez le `Utf8JsonReader` pour lire un flux, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="eab0d-399">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="eab0d-400">La mémoire tampon contenant la charge utile JSON partielle doit être au moins aussi grande que le plus grand jeton JSON au sein de celle-ci afin que le lecteur puisse avancer la progression.</span><span class="sxs-lookup"><span data-stu-id="eab0d-400">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="eab0d-401">La mémoire tampon doit être au moins aussi grande que la plus grande séquence d’espaces blancs dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-401">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="eab0d-402">Le lecteur n’effectue pas le suivi des données qu’il a lues jusqu’à ce qu’il Lise complètement le suivant <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> dans la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-402">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="eab0d-403">Ainsi, lorsqu’il y a des octets restants dans la mémoire tampon, vous devez les transmettre à nouveau au lecteur.</span><span class="sxs-lookup"><span data-stu-id="eab0d-403">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="eab0d-404">Vous pouvez utiliser <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> pour déterminer le nombre d’octets restants.</span><span class="sxs-lookup"><span data-stu-id="eab0d-404">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="eab0d-405">Le code suivant illustre comment lire à partir d’un flux.</span><span class="sxs-lookup"><span data-stu-id="eab0d-405">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="eab0d-406">L’exemple montre un <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="eab0d-406">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="eab0d-407">Un code similaire fonctionne avec un <xref:System.IO.FileStream> , sauf lorsque `FileStream` contient une nomenclature UTF-8 au début.</span><span class="sxs-lookup"><span data-stu-id="eab0d-407">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="eab0d-408">Dans ce cas, vous devez supprimer ces trois octets de la mémoire tampon avant de passer les octets restants à `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="eab0d-408">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="eab0d-409">Dans le cas contraire, le lecteur lèvera une exception, puisque la nomenclature n’est pas considérée comme une partie valide du JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-409">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="eab0d-410">L’exemple de code commence par une mémoire tampon de 4 Ko et double la taille de la mémoire tampon chaque fois qu’il détecte que la taille n’est pas assez grande pour tenir un jeton JSON complet, ce qui est nécessaire pour que le lecteur fasse progresser la progression sur la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="eab0d-410">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="eab0d-411">L’exemple JSON fourni dans l’extrait de code déclenche une augmentation de la taille de la mémoire tampon uniquement si vous définissez une très petite taille de mémoire tampon initiale, par exemple 10 octets.</span><span class="sxs-lookup"><span data-stu-id="eab0d-411">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="eab0d-412">Si vous définissez la taille de la mémoire tampon initiale sur 10, les `Console.WriteLine` instructions illustrent la cause et l’effet de la taille de la mémoire tampon augmente.</span><span class="sxs-lookup"><span data-stu-id="eab0d-412">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="eab0d-413">Au niveau de la taille de la mémoire tampon initiale de 4 Ko, la totalité de l’exemple JSON est affichée par chaque `Console.WriteLine` , et la taille de la mémoire tampon ne doit jamais être augmentée.</span><span class="sxs-lookup"><span data-stu-id="eab0d-413">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="eab0d-414">L’exemple précédent n’affecte aucune limite à la taille maximale de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="eab0d-414">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="eab0d-415">Si la taille du jeton est trop grande, le code peut échouer avec une <xref:System.OutOfMemoryException> exception.</span><span class="sxs-lookup"><span data-stu-id="eab0d-415">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="eab0d-416">Cela peut se produire si le JSON contient un jeton d’une taille d’environ 1 Go, car le doublement de la taille de 1 Go donne une taille trop importante pour tenir dans une `int32` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="eab0d-416">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eab0d-417">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="eab0d-417">Additional resources</span></span>

* <span data-ttu-id="eab0d-418">[System.Text.Jsonvue](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="eab0d-418">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="eab0d-419">Guide pratique pour écrire des convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="eab0d-419">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="eab0d-420">[Migration à partir deNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="eab0d-420">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="eab0d-421">[Prise en charge des valeurs DateTime et DateTimeOffset dansSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="eab0d-421">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="eab0d-422">[System.Text.JsonRéférence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="eab0d-422">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
