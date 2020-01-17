---
title: Comment sérialiser et désérialiser JSON à l' C# aide de-.net
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: fdca8d957bb2453e90652af1dfe5ef99b33b1b2c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163200"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="1047c-102">Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="1047c-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="1047c-103">Cet article explique comment utiliser l’espace de noms <xref:System.Text.Json> pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="1047c-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="1047c-104">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="1047c-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="1047c-105">La majeure partie de l’exemple de code de sérialisation définit <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> de façon à ce qu’il `true` « plutôt imprimer » le JSON (avec mise en retrait et espace blanc pour la lisibilité humaine).</span><span class="sxs-lookup"><span data-stu-id="1047c-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="1047c-106">Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="1047c-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="1047c-107">Espaces de noms des</span><span class="sxs-lookup"><span data-stu-id="1047c-107">Namespaces</span></span>

<span data-ttu-id="1047c-108">L’espace de noms <xref:System.Text.Json> contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="1047c-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="1047c-109">L’espace de noms <xref:System.Text.Json.Serialization> contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="1047c-110">Les exemples de code présentés dans cet article requièrent des directives `using` pour l’un de ces espaces de noms ou les deux :</span><span class="sxs-lookup"><span data-stu-id="1047c-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="1047c-111">Les attributs de l’espace de noms <xref:System.Runtime.Serialization> ne sont actuellement pas pris en charge dans `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="1047c-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="1047c-112">Comment écrire des objets .NET dans JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="1047c-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="1047c-113">Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1047c-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1047c-114">L’exemple suivant crée JSON sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="1047c-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-115">L’exemple suivant utilise du code synchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-116">L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-117">Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="1047c-118">Une surcharge de `Serialize()` prend un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="1047c-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="1047c-119">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="1047c-119">Serialization example</span></span>

<span data-ttu-id="1047c-120">Voici un exemple de classe qui contient des collections et une classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="1047c-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="1047c-121">La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1047c-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="1047c-122">La sortie JSON est minimisés par défaut :</span><span class="sxs-lookup"><span data-stu-id="1047c-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="1047c-123">L’exemple suivant montre le même JSON, mis en forme (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="1047c-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="1047c-124">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="1047c-124">Serialize to UTF-8</span></span>

<span data-ttu-id="1047c-125">Pour sérialiser vers UTF-8, appelez la méthode <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="1047c-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-126">Une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.</span><span class="sxs-lookup"><span data-stu-id="1047c-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="1047c-127">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1047c-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="1047c-128">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="1047c-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="1047c-129">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="1047c-129">Serialization behavior</span></span>

* <span data-ttu-id="1047c-130">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1047c-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="1047c-131">Vous pouvez [spécifier les propriétés à exclure](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="1047c-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="1047c-132">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="1047c-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="1047c-133">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="1047c-133">By default, JSON is minified.</span></span> <span data-ttu-id="1047c-134">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="1047c-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="1047c-135">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="1047c-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="1047c-136">Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="1047c-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="1047c-137">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="1047c-137">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="1047c-138">Actuellement, les champs sont exclus.</span><span class="sxs-lookup"><span data-stu-id="1047c-138">Currently, fields are excluded.</span></span>

<span data-ttu-id="1047c-139">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1047c-139">Supported types include:</span></span>

* <span data-ttu-id="1047c-140">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="1047c-140">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="1047c-141">[Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="1047c-141">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="1047c-142">Tableaux unidimensionnels et en escalier (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="1047c-142">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="1047c-143">`Dictionary<string,TValue>` où `TValue` est `object`, `JsonElement`ou POCO.</span><span class="sxs-lookup"><span data-stu-id="1047c-143">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="1047c-144">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="1047c-144">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="1047c-145">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="1047c-145">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="1047c-146">Comment lire JSON dans des objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="1047c-146">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="1047c-147">Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1047c-147">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1047c-148">L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la classe `WeatherForecast` présentée précédemment pour l' [exemple de sérialisation](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="1047c-148">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="1047c-149">Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-149">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="1047c-150">Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la méthode <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :</span><span class="sxs-lookup"><span data-stu-id="1047c-150">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="1047c-151">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="1047c-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="1047c-152">Pour désérialiser à partir d’UTF-8, appelez une surcharge <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> qui prend un `Utf8JsonReader` ou un `ReadOnlySpan<byte>`, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="1047c-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="1047c-153">Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="1047c-153">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="1047c-154">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="1047c-154">Deserialization behavior</span></span>

* <span data-ttu-id="1047c-155">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="1047c-155">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="1047c-156">Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="1047c-156">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="1047c-157">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="1047c-157">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="1047c-158">La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1047c-158">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="1047c-159">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1047c-159">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="1047c-160">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="1047c-160">By default, enums are supported as numbers.</span></span> <span data-ttu-id="1047c-161">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="1047c-161">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="1047c-162">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1047c-162">Fields aren't supported.</span></span>
* <span data-ttu-id="1047c-163">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="1047c-163">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="1047c-164">Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="1047c-164">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="1047c-165">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="1047c-165">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="1047c-166">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="1047c-166">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="1047c-167">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="1047c-167">Serialize to formatted JSON</span></span>

<span data-ttu-id="1047c-168">Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true`:</span><span class="sxs-lookup"><span data-stu-id="1047c-168">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="1047c-169">Voici un exemple de type à sérialiser et à imprimer une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-169">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="1047c-170">Personnaliser les noms et les valeurs JSON</span><span class="sxs-lookup"><span data-stu-id="1047c-170">Customize JSON names and values</span></span>

<span data-ttu-id="1047c-171">Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse.</span><span class="sxs-lookup"><span data-stu-id="1047c-171">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="1047c-172">Les valeurs enum sont représentées sous forme de nombres.</span><span class="sxs-lookup"><span data-stu-id="1047c-172">Enum values are represented as numbers.</span></span> <span data-ttu-id="1047c-173">Cette section explique comment :</span><span class="sxs-lookup"><span data-stu-id="1047c-173">This section explains how to:</span></span>

* [<span data-ttu-id="1047c-174">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="1047c-174">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="1047c-175">Convertir tous les noms de propriété en casse mixte</span><span class="sxs-lookup"><span data-stu-id="1047c-175">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="1047c-176">Implémenter une stratégie d’attribution de noms de propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="1047c-176">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="1047c-177">Convertir les clés du dictionnaire en casse mixte</span><span class="sxs-lookup"><span data-stu-id="1047c-177">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="1047c-178">Convertir des enums en chaînes et casse mixte</span><span class="sxs-lookup"><span data-stu-id="1047c-178">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="1047c-179">Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="1047c-179">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="1047c-180">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="1047c-180">Customize individual property names</span></span>

<span data-ttu-id="1047c-181">Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="1047c-181">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="1047c-182">Voici un exemple de type pour sérialiser et JSON obtenu :</span><span class="sxs-lookup"><span data-stu-id="1047c-182">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="1047c-183">Nom de propriété défini par cet attribut :</span><span class="sxs-lookup"><span data-stu-id="1047c-183">The property name set by this attribute:</span></span>

* <span data-ttu-id="1047c-184">S’applique dans les deux directions, pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-184">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="1047c-185">Est prioritaire sur les stratégies d’attribution de noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="1047c-185">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="1047c-186">Utiliser la casse mixte pour tous les noms de propriété JSON</span><span class="sxs-lookup"><span data-stu-id="1047c-186">Use camel case for all JSON property names</span></span>

<span data-ttu-id="1047c-187">Pour utiliser la casse mixte pour tous les noms de propriété JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-187">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="1047c-188">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-188">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="1047c-189">La stratégie de nommage de propriété casse mixte :</span><span class="sxs-lookup"><span data-stu-id="1047c-189">The camel case property naming policy:</span></span>

* <span data-ttu-id="1047c-190">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="1047c-191">Est substitué par `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="1047c-191">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="1047c-192">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.</span><span class="sxs-lookup"><span data-stu-id="1047c-192">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="1047c-193">Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée</span><span class="sxs-lookup"><span data-stu-id="1047c-193">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="1047c-194">Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la méthode <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-194">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="1047c-195">Définissez ensuite la propriété <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur une instance de votre classe de stratégie d’attribution de noms :</span><span class="sxs-lookup"><span data-stu-id="1047c-195">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-196">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-196">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="1047c-197">La stratégie d’attribution de noms de propriété JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-197">The JSON property naming policy:</span></span>

* <span data-ttu-id="1047c-198">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-198">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="1047c-199">Est substitué par `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="1047c-199">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="1047c-200">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.</span><span class="sxs-lookup"><span data-stu-id="1047c-200">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="1047c-201">Clés de dictionnaire de casse mixte</span><span class="sxs-lookup"><span data-stu-id="1047c-201">Camel case dictionary keys</span></span>

<span data-ttu-id="1047c-202">Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>`, les clés `string` peuvent être converties en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="1047c-202">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="1047c-203">Pour ce faire, définissez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-203">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-204">La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` entraînerait une sortie JSON comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-204">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="1047c-205">La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-205">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="1047c-206">Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="1047c-206">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="1047c-207">Enums en tant que chaînes</span><span class="sxs-lookup"><span data-stu-id="1047c-207">Enums as strings</span></span>

<span data-ttu-id="1047c-208">Par défaut, les enums sont sérialisés en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="1047c-208">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="1047c-209">Pour sérialiser les noms d’enum sous forme de chaînes, utilisez l' <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="1047c-209">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="1047c-210">Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :</span><span class="sxs-lookup"><span data-stu-id="1047c-210">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="1047c-211">Si le résumé est `Hot`, par défaut, le JSON sérialisé a la valeur numérique 3 :</span><span class="sxs-lookup"><span data-stu-id="1047c-211">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="1047c-212">L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :</span><span class="sxs-lookup"><span data-stu-id="1047c-212">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-213">Le JSON obtenu ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-213">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="1047c-214">Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-214">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="1047c-215">Exclure des propriétés de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="1047c-215">Exclude properties from serialization</span></span>

<span data-ttu-id="1047c-216">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1047c-216">By default, all public properties are serialized.</span></span> <span data-ttu-id="1047c-217">Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="1047c-217">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="1047c-218">Cette section explique comment exclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1047c-218">This section explains how to exclude:</span></span>

* [<span data-ttu-id="1047c-219">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="1047c-219">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="1047c-220">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="1047c-220">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="1047c-221">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="1047c-221">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="1047c-222">Exclure des propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="1047c-222">Exclude individual properties</span></span>

<span data-ttu-id="1047c-223">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="1047c-223">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="1047c-224">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-224">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="1047c-225">Exclure toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="1047c-225">Exclude all read-only properties</span></span>

<span data-ttu-id="1047c-226">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="1047c-226">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="1047c-227">Pour exclure toutes les propriétés en lecture seule, affectez la valeur `true`à la <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-227">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-228">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="1047c-229">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-229">This option applies only to serialization.</span></span> <span data-ttu-id="1047c-230">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="1047c-230">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="1047c-231">Exclure toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="1047c-231">Exclude all null value properties</span></span>

<span data-ttu-id="1047c-232">Pour exclure toutes les propriétés de valeur null, affectez la valeur `true`à la propriété <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-232">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-233">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-233">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="1047c-234">Les</span><span class="sxs-lookup"><span data-stu-id="1047c-234">Property</span></span> |<span data-ttu-id="1047c-235">Value</span><span class="sxs-lookup"><span data-stu-id="1047c-235">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="1047c-236">Date</span><span class="sxs-lookup"><span data-stu-id="1047c-236">Date</span></span>    | <span data-ttu-id="1047c-237">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="1047c-237">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="1047c-238">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="1047c-238">TemperatureCelsius</span></span>| <span data-ttu-id="1047c-239">25</span><span class="sxs-lookup"><span data-stu-id="1047c-239">25</span></span> |
| <span data-ttu-id="1047c-240">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="1047c-240">Summary</span></span>| <span data-ttu-id="1047c-241">null</span><span class="sxs-lookup"><span data-stu-id="1047c-241">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="1047c-242">Ce paramètre s’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-242">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="1047c-243">Pour plus d’informations sur son effet sur la désérialisation, consultez [ignorer la valeur null lors de la désérialisation](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="1047c-243">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="1047c-244">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="1047c-244">Customize character encoding</span></span>

<span data-ttu-id="1047c-245">Par défaut, le sérialiseur échappe tous les caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="1047c-245">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="1047c-246">Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.</span><span class="sxs-lookup"><span data-stu-id="1047c-246">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="1047c-247">Par exemple, si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="1047c-247">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="1047c-248">Sérialiser les jeux de caractères de la langue</span><span class="sxs-lookup"><span data-stu-id="1047c-248">Serialize language character sets</span></span>

<span data-ttu-id="1047c-249">Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-249">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="1047c-250">Ce code n’échappe pas aux caractères cyrilliques ou grecs.</span><span class="sxs-lookup"><span data-stu-id="1047c-250">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="1047c-251">Si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="1047c-251">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="1047c-252">Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1047c-252">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="1047c-253">Sérialiser des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="1047c-253">Serialize specific characters</span></span>

<span data-ttu-id="1047c-254">Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés.</span><span class="sxs-lookup"><span data-stu-id="1047c-254">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="1047c-255">L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :</span><span class="sxs-lookup"><span data-stu-id="1047c-255">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="1047c-256">Voici un exemple de JSON généré par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="1047c-256">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="1047c-257">Sérialiser tous les caractères</span><span class="sxs-lookup"><span data-stu-id="1047c-257">Serialize all characters</span></span>

<span data-ttu-id="1047c-258">Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-258">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="1047c-259">Par rapport à l’encodeur par défaut, l’encodeur `UnsafeRelaxedJsonEscaping` est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :</span><span class="sxs-lookup"><span data-stu-id="1047c-259">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="1047c-260">Elle n’échappe pas les caractères HTML tels que `<`, `>`, `&`et `'`.</span><span class="sxs-lookup"><span data-stu-id="1047c-260">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="1047c-261">Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu*de caractères.</span><span class="sxs-lookup"><span data-stu-id="1047c-261">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="1047c-262">Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1047c-262">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="1047c-263">Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="1047c-263">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="1047c-264">N’autorisez jamais l’émission de la sortie `UnsafeRelaxedJsonEscaping` brute dans une page HTML ou un élément `<script>`.</span><span class="sxs-lookup"><span data-stu-id="1047c-264">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="1047c-265">Sérialiser les propriétés des classes dérivées</span><span class="sxs-lookup"><span data-stu-id="1047c-265">Serialize properties of derived classes</span></span>

<span data-ttu-id="1047c-266">La sérialisation d’une hiérarchie de type polymorphe n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1047c-266">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="1047c-267">Par exemple, si une propriété est définie comme une interface ou une classe abstraite, seules les propriétés définies sur l’interface ou la classe abstraite sont sérialisées, même si le type de runtime a des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1047c-267">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="1047c-268">Les exceptions à ce comportement sont expliquées dans cette section.</span><span class="sxs-lookup"><span data-stu-id="1047c-268">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="1047c-269">Par exemple, supposons que vous ayez une classe `WeatherForecast` et une classe dérivée `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="1047c-269">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="1047c-270">Et supposons que l’argument de type de la méthode `Serialize` au moment de la compilation est `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="1047c-270">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="1047c-271">Dans ce scénario, la propriété `WindSpeed` n’est pas sérialisée, même si l’objet `weatherForecast` est en fait un objet `WeatherForecastDerived`.</span><span class="sxs-lookup"><span data-stu-id="1047c-271">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="1047c-272">Seules les propriétés de la classe de base sont sérialisées :</span><span class="sxs-lookup"><span data-stu-id="1047c-272">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="1047c-273">Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.</span><span class="sxs-lookup"><span data-stu-id="1047c-273">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="1047c-274">Pour sérialiser les propriétés du type dérivé dans l’exemple précédent, utilisez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="1047c-274">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="1047c-275">Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="1047c-275">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="1047c-276">Déclarez l’objet à sérialiser en tant que `object`.</span><span class="sxs-lookup"><span data-stu-id="1047c-276">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="1047c-277">Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la propriété `WindSpeed` dans la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-277">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="1047c-278">Ces approches fournissent la sérialisation polymorphe uniquement pour l’objet racine à sérialiser, et non pour les propriétés de cet objet racine.</span><span class="sxs-lookup"><span data-stu-id="1047c-278">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span> 

<span data-ttu-id="1047c-279">Vous pouvez obtenir la sérialisation polymorphe pour les objets de niveau inférieur si vous les définissez en tant que type `object`.</span><span class="sxs-lookup"><span data-stu-id="1047c-279">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="1047c-280">Par exemple, supposons que votre classe `WeatherForecast` possède une propriété nommée `PreviousForecast` qui peut être définie en tant que type `WeatherForecast` ou `object`:</span><span class="sxs-lookup"><span data-stu-id="1047c-280">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="1047c-281">Si la propriété `PreviousForecast` contient une instance de `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="1047c-281">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="1047c-282">La sortie JSON de la sérialisation `WeatherForecastWithPrevious` **n’inclut pas** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="1047c-282">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="1047c-283">La sortie JSON de la sérialisation `WeatherForecastWithPreviousAsObject` **comprend** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="1047c-283">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="1047c-284">Pour sérialiser `WeatherForecastWithPreviousAsObject`, il n’est pas nécessaire d’appeler `Serialize<object>` ou `GetType`, car l’objet racine n’est pas celui d’un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="1047c-284">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="1047c-285">L’exemple de code suivant n’appelle pas `Serialize<object>` ou `GetType`:</span><span class="sxs-lookup"><span data-stu-id="1047c-285">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="1047c-286">Le code précédent sérialise correctement `WeatherForecastWithPreviousAsObject`:</span><span class="sxs-lookup"><span data-stu-id="1047c-286">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="1047c-287">La même approche de la définition des propriétés en tant que `object` fonctionne avec les interfaces.</span><span class="sxs-lookup"><span data-stu-id="1047c-287">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="1047c-288">Supposons que vous disposez de l’interface et de l’implémentation suivantes, et que vous souhaitez sérialiser une classe avec des propriétés qui contiennent des instances d’implémentation :</span><span class="sxs-lookup"><span data-stu-id="1047c-288">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="1047c-289">Lorsque vous sérialisez une instance de `Forecasts`, seul `Tuesday` affiche la propriété `WindSpeed`, car `Tuesday` est défini en tant que `object`:</span><span class="sxs-lookup"><span data-stu-id="1047c-289">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="1047c-290">L’exemple suivant montre le code JSON qui résulte du code précédent :</span><span class="sxs-lookup"><span data-stu-id="1047c-290">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="1047c-291">Pour plus d’informations sur **la sérialisation**polymorphe et sur la **désérialisation**, consultez [How to Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="1047c-291">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="1047c-292">Autoriser les commentaires et les virgules de fin</span><span class="sxs-lookup"><span data-stu-id="1047c-292">Allow comments and trailing commas</span></span>

<span data-ttu-id="1047c-293">Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON.</span><span class="sxs-lookup"><span data-stu-id="1047c-293">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="1047c-294">Pour autoriser les commentaires dans le JSON, affectez à la propriété <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> la valeur `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="1047c-294">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="1047c-295">Et pour autoriser les virgules de fin, définissez la propriété <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> sur `true`.</span><span class="sxs-lookup"><span data-stu-id="1047c-295">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="1047c-296">L’exemple suivant montre comment autoriser les deux :</span><span class="sxs-lookup"><span data-stu-id="1047c-296">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="1047c-297">Voici un exemple de code JSON avec des commentaires et une virgule de fin :</span><span class="sxs-lookup"><span data-stu-id="1047c-297">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="1047c-298">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="1047c-298">Case-insensitive property matching</span></span>

<span data-ttu-id="1047c-299">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="1047c-299">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="1047c-300">Pour modifier ce comportement, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> sur `true`:</span><span class="sxs-lookup"><span data-stu-id="1047c-300">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="1047c-301">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="1047c-301">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="1047c-302">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="1047c-302">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="1047c-303">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="1047c-303">Handle overflow JSON</span></span>

<span data-ttu-id="1047c-304">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="1047c-304">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="1047c-305">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-305">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="1047c-306">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-306">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="1047c-307">Si vous désérialisez le JSON indiqué dans le type indiqué, les propriétés `DatesAvailable` et `SummaryWords` ne peuvent pas être placées et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="1047c-307">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="1047c-308">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de type `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="1047c-308">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="1047c-309">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la propriété `ExtensionData` :</span><span class="sxs-lookup"><span data-stu-id="1047c-309">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="1047c-310">Les</span><span class="sxs-lookup"><span data-stu-id="1047c-310">Property</span></span> |<span data-ttu-id="1047c-311">Value</span><span class="sxs-lookup"><span data-stu-id="1047c-311">Value</span></span>  |<span data-ttu-id="1047c-312">Remarques</span><span class="sxs-lookup"><span data-stu-id="1047c-312">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="1047c-313">Date</span><span class="sxs-lookup"><span data-stu-id="1047c-313">Date</span></span>    | <span data-ttu-id="1047c-314">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="1047c-314">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="1047c-315">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="1047c-315">TemperatureCelsius</span></span>| <span data-ttu-id="1047c-316">0</span><span class="sxs-lookup"><span data-stu-id="1047c-316">0</span></span> | <span data-ttu-id="1047c-317">Incompatibilité sensible à la casse (`temperatureCelsius` dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="1047c-317">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="1047c-318">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="1047c-318">Summary</span></span> | <span data-ttu-id="1047c-319">Très chargé</span><span class="sxs-lookup"><span data-stu-id="1047c-319">Hot</span></span> ||
| <span data-ttu-id="1047c-320">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="1047c-320">ExtensionData</span></span> | <span data-ttu-id="1047c-321">temperatureCelsius : 25</span><span class="sxs-lookup"><span data-stu-id="1047c-321">temperatureCelsius: 25</span></span> |<span data-ttu-id="1047c-322">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="1047c-322">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="1047c-323">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="1047c-323">DatesAvailable:</span></span><br>  <span data-ttu-id="1047c-324">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="1047c-324">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="1047c-325">DE 8/2/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="1047c-325">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="1047c-326">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="1047c-326">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="1047c-327">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="1047c-327">SummaryWords:</span></span><br><span data-ttu-id="1047c-328">Cool</span><span class="sxs-lookup"><span data-stu-id="1047c-328">Cool</span></span><br><span data-ttu-id="1047c-329">Venteux</span><span class="sxs-lookup"><span data-stu-id="1047c-329">Windy</span></span><br><span data-ttu-id="1047c-330">Humide</span><span class="sxs-lookup"><span data-stu-id="1047c-330">Humid</span></span> |<span data-ttu-id="1047c-331">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="1047c-331">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="1047c-332">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="1047c-332">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="1047c-333">Notez que le nom de la propriété `ExtensionData` n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="1047c-333">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="1047c-334">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="1047c-334">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="1047c-335">Ignorer la valeur null lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="1047c-335">Ignore null when deserializing</span></span>

<span data-ttu-id="1047c-336">Par défaut, si une propriété dans JSON a la valeur null, la propriété correspondante dans l’objet cible a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="1047c-336">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="1047c-337">Dans certains scénarios, la propriété cible peut avoir une valeur par défaut et vous ne souhaitez pas qu’une valeur null remplace la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1047c-337">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="1047c-338">Par exemple, supposons que le code suivant représente votre objet cible :</span><span class="sxs-lookup"><span data-stu-id="1047c-338">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="1047c-339">Et supposons que le code JSON suivant est désérialisé :</span><span class="sxs-lookup"><span data-stu-id="1047c-339">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="1047c-340">Après la désérialisation, la propriété `Summary` de l’objet `WeatherForecastWithDefault` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="1047c-340">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="1047c-341">Pour modifier ce comportement, affectez la valeur `true`à <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-341">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="1047c-342">Avec cette option, la propriété `Summary` de l’objet `WeatherForecastWithDefault` est la valeur par défaut « no Summary » après la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1047c-342">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="1047c-343">Les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides.</span><span class="sxs-lookup"><span data-stu-id="1047c-343">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="1047c-344">Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="1047c-344">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="1047c-345">Utf8JsonReader, Utf8JsonWriter et JsonDocument</span><span class="sxs-lookup"><span data-stu-id="1047c-345">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="1047c-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un `ReadOnlySpan<byte>` ou d’un `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="1047c-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="1047c-347">Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1047c-347">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="1047c-348">La méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> utilise `Utf8JsonReader` en coulisses.</span><span class="sxs-lookup"><span data-stu-id="1047c-348">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="1047c-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants comme `String`, `Int32`et `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="1047c-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="1047c-350">Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1047c-350">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="1047c-351">La méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> utilise `Utf8JsonWriter` en coulisses.</span><span class="sxs-lookup"><span data-stu-id="1047c-351">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="1047c-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> permet de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="1047c-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="1047c-353">Le DOM fournit un accès aléatoire aux données dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="1047c-353">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="1047c-354">Les éléments JSON qui composent la charge utile sont accessibles via le type de <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="1047c-354">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="1047c-355">Le type de `JsonElement` fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .NET courants.</span><span class="sxs-lookup"><span data-stu-id="1047c-355">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="1047c-356">`JsonDocument` expose une propriété <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="1047c-356">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="1047c-357">Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.</span><span class="sxs-lookup"><span data-stu-id="1047c-357">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="1047c-358">Utiliser JsonDocument pour l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="1047c-358">Use JsonDocument for access to data</span></span>

<span data-ttu-id="1047c-359">L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.JsonDocument> pour l’accès aléatoire aux données dans une chaîne JSON :</span><span class="sxs-lookup"><span data-stu-id="1047c-359">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="1047c-360">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="1047c-360">The preceding code:</span></span>

* <span data-ttu-id="1047c-361">Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="1047c-361">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="1047c-362">Calcule une qualité moyenne pour les objets d’un tableau de `Students` qui ont une propriété `Grade`.</span><span class="sxs-lookup"><span data-stu-id="1047c-362">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="1047c-363">Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.</span><span class="sxs-lookup"><span data-stu-id="1047c-363">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="1047c-364">Compte les étudiants en incrémentant une variable de `count` à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="1047c-364">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="1047c-365">Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-365">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="1047c-366">Voici un exemple du JSON traité par ce code :</span><span class="sxs-lookup"><span data-stu-id="1047c-366">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="1047c-367">Utiliser JsonDocument pour écrire du code JSON</span><span class="sxs-lookup"><span data-stu-id="1047c-367">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="1047c-368">L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="1047c-368">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="1047c-369">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="1047c-369">The preceding code:</span></span>

* <span data-ttu-id="1047c-370">Lit un fichier JSON, charge les données dans un `JsonDocument`et écrit le format JSON (Pretty-imprimed) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="1047c-370">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="1047c-371">Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.</span><span class="sxs-lookup"><span data-stu-id="1047c-371">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="1047c-372">Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer.</span><span class="sxs-lookup"><span data-stu-id="1047c-372">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="1047c-373">Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="1047c-373">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="1047c-374">Voici un exemple d’entrée JSON à traiter par l’exemple de code :</span><span class="sxs-lookup"><span data-stu-id="1047c-374">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="1047c-375">Le résultat est la sortie JSON imprimée suivante :</span><span class="sxs-lookup"><span data-stu-id="1047c-375">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="1047c-376">Utiliser Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="1047c-376">Use Utf8JsonWriter</span></span>

<span data-ttu-id="1047c-377">L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonWriter> :</span><span class="sxs-lookup"><span data-stu-id="1047c-377">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="1047c-378">Utiliser Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="1047c-378">Use Utf8JsonReader</span></span>

<span data-ttu-id="1047c-379">L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonReader> :</span><span class="sxs-lookup"><span data-stu-id="1047c-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="1047c-380">Le code précédent suppose que la variable `jsonUtf8` est un tableau d’octets contenant un JSON valide, encodé au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1047c-380">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="1047c-381">Filtrer les données à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="1047c-381">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="1047c-382">L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur :</span><span class="sxs-lookup"><span data-stu-id="1047c-382">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="1047c-383">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="1047c-383">The preceding code:</span></span>

* <span data-ttu-id="1047c-384">Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="1047c-384">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="1047c-385">Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».</span><span class="sxs-lookup"><span data-stu-id="1047c-385">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="1047c-386">Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1047c-386">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="1047c-387">Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>`, à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="1047c-387">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

  <span data-ttu-id="1047c-388">Si le fichier contient une marque d’ordre d’octet UTF-8 (BOM), supprimez-le avant de passer les octets au `Utf8JsonReader`, puisque le lecteur attend du texte.</span><span class="sxs-lookup"><span data-stu-id="1047c-388">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="1047c-389">Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="1047c-389">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="1047c-390">Voici un exemple JSON que le code précédent peut lire.</span><span class="sxs-lookup"><span data-stu-id="1047c-390">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="1047c-391">Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :</span><span class="sxs-lookup"><span data-stu-id="1047c-391">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="1047c-392">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1047c-392">Additional resources</span></span>

* <span data-ttu-id="1047c-393">[présentation de System.Text.Json](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="1047c-393">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="1047c-394">Comment écrire des convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="1047c-394">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="1047c-395">[Migration à partir de Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="1047c-395">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="1047c-396">[Prise en charge des valeurs DateTime et DateTimeOffset dans System.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="1047c-396">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="1047c-397">[informations de référence sur l’API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="1047c-397">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
