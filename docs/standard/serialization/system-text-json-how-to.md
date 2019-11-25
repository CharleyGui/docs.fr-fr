---
title: Comment sérialiser et désérialiser JSON à l' C# aide de-.net
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3d3dc0011562e25854938aff857f2832a5978b49
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283337"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="021f6-102">Comment sérialiser et désérialiser JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="021f6-102">How to serialize and deserialize JSON in .NET</span></span>

<span data-ttu-id="021f6-103">Cet article explique comment utiliser l’espace de noms <xref:System.Text.Json> pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="021f6-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="021f6-104">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="021f6-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="021f6-105">La majeure partie de l’exemple de code de sérialisation définit <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> de façon à ce qu’il `true` « plutôt imprimer » le JSON (avec mise en retrait et espace blanc pour la lisibilité humaine).</span><span class="sxs-lookup"><span data-stu-id="021f6-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="021f6-106">Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="021f6-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="021f6-107">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="021f6-107">Namespaces</span></span>

<span data-ttu-id="021f6-108">L’espace de noms <xref:System.Text.Json> contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="021f6-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="021f6-109">L’espace de noms <xref:System.Text.Json.Serialization> contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="021f6-110">Les exemples de code présentés dans cet article requièrent des directives `using` pour l’un de ces espaces de noms ou les deux :</span><span class="sxs-lookup"><span data-stu-id="021f6-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="021f6-111">Les attributs de l’espace de noms <xref:System.Runtime.Serialization> ne sont actuellement pas pris en charge dans `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="021f6-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="021f6-112">Comment écrire des objets .NET dans JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="021f6-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="021f6-113">Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="021f6-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="021f6-114">L’exemple suivant crée JSON sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="021f6-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-115">L’exemple suivant utilise du code synchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-116">L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-117">Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="021f6-118">Une surcharge de `Serialize()` prend un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="021f6-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="021f6-119">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="021f6-119">Serialization example</span></span>

<span data-ttu-id="021f6-120">Voici un exemple de classe qui contient des collections et une classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="021f6-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="021f6-121">La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="021f6-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="021f6-122">La sortie JSON est minimisés par défaut :</span><span class="sxs-lookup"><span data-stu-id="021f6-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="021f6-123">L’exemple suivant montre le même JSON, mis en forme (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="021f6-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="021f6-124">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="021f6-124">Serialize to UTF-8</span></span>

<span data-ttu-id="021f6-125">Pour sérialiser vers UTF-8, appelez la méthode <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="021f6-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-126">Une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.</span><span class="sxs-lookup"><span data-stu-id="021f6-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="021f6-127">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="021f6-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="021f6-128">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="021f6-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="021f6-129">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="021f6-129">Serialization behavior</span></span>

* <span data-ttu-id="021f6-130">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="021f6-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="021f6-131">Vous pouvez [spécifier les propriétés à exclure](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="021f6-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="021f6-132">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="021f6-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="021f6-133">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="021f6-133">By default, JSON is minified.</span></span> <span data-ttu-id="021f6-134">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="021f6-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="021f6-135">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="021f6-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="021f6-136">Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="021f6-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="021f6-137">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="021f6-137">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="021f6-138">Pour plus d’informations, consultez le [problème 38579 sur les références circulaires](https://github.com/dotnet/corefx/issues/38579) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="021f6-138">For more information, see [issue 38579 on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="021f6-139">Actuellement, les champs sont exclus.</span><span class="sxs-lookup"><span data-stu-id="021f6-139">Currently, fields are excluded.</span></span>

<span data-ttu-id="021f6-140">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="021f6-140">Supported types include:</span></span>

* <span data-ttu-id="021f6-141">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="021f6-141">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="021f6-142">[Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="021f6-142">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="021f6-143">Tableaux unidimensionnels et en escalier (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="021f6-143">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="021f6-144">`Dictionary<string,TValue>` où `TValue` est `object`, `JsonElement`ou POCO.</span><span class="sxs-lookup"><span data-stu-id="021f6-144">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="021f6-145">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="021f6-145">Collections from the following namespaces.</span></span> <span data-ttu-id="021f6-146">Pour plus d’informations, consultez le [problème sur la prise en charge de collection](https://github.com/dotnet/corefx/issues/36643) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="021f6-146">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="021f6-147">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="021f6-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="021f6-148">Comment lire JSON dans des objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="021f6-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="021f6-149">Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="021f6-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="021f6-150">L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la classe `WeatherForecast` présentée précédemment pour l' [exemple de sérialisation](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="021f6-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="021f6-151">Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="021f6-152">Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la méthode <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :</span><span class="sxs-lookup"><span data-stu-id="021f6-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="021f6-153">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="021f6-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="021f6-154">Pour désérialiser à partir d’UTF-8, appelez une surcharge <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> qui prend un `Utf8JsonReader` ou un `ReadOnlySpan<byte>`, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="021f6-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="021f6-155">Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="021f6-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="021f6-156">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="021f6-156">Deserialization behavior</span></span>

* <span data-ttu-id="021f6-157">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="021f6-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="021f6-158">Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="021f6-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="021f6-159">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="021f6-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="021f6-160">La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="021f6-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="021f6-161">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="021f6-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="021f6-162">Pour plus d’informations, consultez le [problème GitHub 38569 sur la prise en charge des objets immuables](https://github.com/dotnet/corefx/issues/38569) et le [problème 38163 sur la prise en charge des propriétés en lecture seule](https://github.com/dotnet/corefx/issues/38163) dans le référentiel dotnet/corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="021f6-162">For more information, see GitHub [issue 38569 on immutable object support](https://github.com/dotnet/corefx/issues/38569) and [issue 38163 on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="021f6-163">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="021f6-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="021f6-164">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="021f6-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="021f6-165">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="021f6-165">Fields aren't supported.</span></span>
* <span data-ttu-id="021f6-166">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="021f6-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="021f6-167">Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="021f6-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="021f6-168">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="021f6-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="021f6-169">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="021f6-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="021f6-170">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="021f6-171">Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true`:</span><span class="sxs-lookup"><span data-stu-id="021f6-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="021f6-172">Voici un exemple de type à sérialiser et à imprimer une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="021f6-173">Personnaliser les noms et les valeurs JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-173">Customize JSON names and values</span></span>

<span data-ttu-id="021f6-174">Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse.</span><span class="sxs-lookup"><span data-stu-id="021f6-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="021f6-175">Les valeurs enum sont représentées sous forme de nombres.</span><span class="sxs-lookup"><span data-stu-id="021f6-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="021f6-176">Cette section explique comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="021f6-176">This section explains how to:</span></span>

* [<span data-ttu-id="021f6-177">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="021f6-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="021f6-178">Convertir tous les noms de propriété en casse mixte</span><span class="sxs-lookup"><span data-stu-id="021f6-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="021f6-179">Implémenter une stratégie d’attribution de noms de propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="021f6-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="021f6-180">Convertir les clés du dictionnaire en casse mixte</span><span class="sxs-lookup"><span data-stu-id="021f6-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="021f6-181">Convertir des enums en chaînes et casse mixte</span><span class="sxs-lookup"><span data-stu-id="021f6-181">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="021f6-182">Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="021f6-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="021f6-183">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="021f6-183">Customize individual property names</span></span>

<span data-ttu-id="021f6-184">Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="021f6-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="021f6-185">Voici un exemple de type pour sérialiser et JSON obtenu :</span><span class="sxs-lookup"><span data-stu-id="021f6-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="021f6-186">Nom de propriété défini par cet attribut :</span><span class="sxs-lookup"><span data-stu-id="021f6-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="021f6-187">S’applique dans les deux directions, pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="021f6-188">Est prioritaire sur les stratégies d’attribution de noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="021f6-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="021f6-189">Utiliser la casse mixte pour tous les noms de propriété JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="021f6-190">Pour utiliser la casse mixte pour tous les noms de propriété JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="021f6-191">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="021f6-192">La stratégie de nommage de propriété casse mixte :</span><span class="sxs-lookup"><span data-stu-id="021f6-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="021f6-193">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="021f6-194">Est substitué par `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="021f6-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="021f6-195">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.</span><span class="sxs-lookup"><span data-stu-id="021f6-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="021f6-196">Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée</span><span class="sxs-lookup"><span data-stu-id="021f6-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="021f6-197">Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la méthode <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="021f6-198">Définissez ensuite la propriété <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur une instance de votre classe de stratégie d’attribution de noms :</span><span class="sxs-lookup"><span data-stu-id="021f6-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-199">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="021f6-200">La stratégie d’attribution de noms de propriété JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="021f6-201">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="021f6-202">Est substitué par `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="021f6-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="021f6-203">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.</span><span class="sxs-lookup"><span data-stu-id="021f6-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="021f6-204">Clés de dictionnaire de casse mixte</span><span class="sxs-lookup"><span data-stu-id="021f6-204">Camel case dictionary keys</span></span>

<span data-ttu-id="021f6-205">Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>`, les clés `string` peuvent être converties en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="021f6-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="021f6-206">Pour ce faire, définissez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-207">La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` entraînerait une sortie JSON comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="021f6-208">La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="021f6-209">Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="021f6-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="021f6-210">Enums en tant que chaînes</span><span class="sxs-lookup"><span data-stu-id="021f6-210">Enums as strings</span></span>

<span data-ttu-id="021f6-211">Par défaut, les enums sont sérialisés en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="021f6-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="021f6-212">Pour sérialiser les noms d’enum sous forme de chaînes, utilisez l' <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="021f6-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="021f6-213">Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :</span><span class="sxs-lookup"><span data-stu-id="021f6-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="021f6-214">Si le résumé est `Hot`, par défaut, le JSON sérialisé a la valeur numérique 3 :</span><span class="sxs-lookup"><span data-stu-id="021f6-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="021f6-215">L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :</span><span class="sxs-lookup"><span data-stu-id="021f6-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-216">Le JSON obtenu ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="021f6-217">Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="021f6-218">Exclure des propriétés de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="021f6-218">Exclude properties from serialization</span></span>

<span data-ttu-id="021f6-219">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="021f6-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="021f6-220">Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="021f6-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="021f6-221">Cette section explique comment exclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="021f6-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="021f6-222">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="021f6-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="021f6-223">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="021f6-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="021f6-224">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="021f6-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="021f6-225">Exclure des propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="021f6-225">Exclude individual properties</span></span>

<span data-ttu-id="021f6-226">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="021f6-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="021f6-227">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="021f6-228">Exclure toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="021f6-228">Exclude all read-only properties</span></span>

<span data-ttu-id="021f6-229">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="021f6-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="021f6-230">Pour exclure toutes les propriétés en lecture seule, affectez la valeur `true`à la <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-231">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="021f6-232">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-232">This option applies only to serialization.</span></span> <span data-ttu-id="021f6-233">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="021f6-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="021f6-234">Exclure toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="021f6-234">Exclude all null value properties</span></span>

<span data-ttu-id="021f6-235">Pour exclure toutes les propriétés de valeur null, affectez la valeur `true`à la propriété <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-236">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="021f6-237">Les</span><span class="sxs-lookup"><span data-stu-id="021f6-237">Property</span></span> |<span data-ttu-id="021f6-238">Valeur</span><span class="sxs-lookup"><span data-stu-id="021f6-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="021f6-239">Date</span><span class="sxs-lookup"><span data-stu-id="021f6-239">Date</span></span>    | <span data-ttu-id="021f6-240">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="021f6-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="021f6-241">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="021f6-241">TemperatureCelsius</span></span>| <span data-ttu-id="021f6-242">25</span><span class="sxs-lookup"><span data-stu-id="021f6-242">25</span></span> |
| <span data-ttu-id="021f6-243">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="021f6-243">Summary</span></span>| <span data-ttu-id="021f6-244">null</span><span class="sxs-lookup"><span data-stu-id="021f6-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="021f6-245">Ce paramètre s’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="021f6-246">Pour plus d’informations sur son effet sur la désérialisation, consultez [ignorer la valeur null lors de la désérialisation](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="021f6-246">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="021f6-247">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="021f6-247">Customize character encoding</span></span>

<span data-ttu-id="021f6-248">Par défaut, le sérialiseur échappe tous les caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="021f6-248">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="021f6-249">Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.</span><span class="sxs-lookup"><span data-stu-id="021f6-249">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="021f6-250">Par exemple, si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="021f6-250">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="021f6-251">Sérialiser les jeux de caractères de la langue</span><span class="sxs-lookup"><span data-stu-id="021f6-251">Serialize language character sets</span></span>

<span data-ttu-id="021f6-252">Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-252">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="021f6-253">Ce code n’échappe pas aux caractères cyrilliques ou grecs.</span><span class="sxs-lookup"><span data-stu-id="021f6-253">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="021f6-254">Si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="021f6-254">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="021f6-255">Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="021f6-255">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="021f6-256">Sérialiser des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="021f6-256">Serialize specific characters</span></span>

<span data-ttu-id="021f6-257">Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés.</span><span class="sxs-lookup"><span data-stu-id="021f6-257">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="021f6-258">L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :</span><span class="sxs-lookup"><span data-stu-id="021f6-258">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="021f6-259">Voici un exemple de JSON généré par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="021f6-259">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="021f6-260">Sérialiser tous les caractères</span><span class="sxs-lookup"><span data-stu-id="021f6-260">Serialize all characters</span></span>

<span data-ttu-id="021f6-261">Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-261">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="021f6-262">Par rapport à l’encodeur par défaut, l’encodeur `UnsafeRelaxedJsonEscaping` est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :</span><span class="sxs-lookup"><span data-stu-id="021f6-262">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="021f6-263">Elle n’échappe pas les caractères HTML tels que `<`, `>`, `&`et `'`.</span><span class="sxs-lookup"><span data-stu-id="021f6-263">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="021f6-264">Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu*de caractères.</span><span class="sxs-lookup"><span data-stu-id="021f6-264">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="021f6-265">Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="021f6-265">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="021f6-266">Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="021f6-266">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="021f6-267">N’autorisez jamais l’émission de la sortie `UnsafeRelaxedJsonEscaping` brute dans une page HTML ou un élément `<script>`.</span><span class="sxs-lookup"><span data-stu-id="021f6-267">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="021f6-268">Sérialiser les propriétés des classes dérivées</span><span class="sxs-lookup"><span data-stu-id="021f6-268">Serialize properties of derived classes</span></span>

<span data-ttu-id="021f6-269">La sérialisation polymorphe n’est pas prise en charge lorsque vous spécifiez au moment de la compilation le type à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="021f6-269">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="021f6-270">Par exemple, supposons que vous ayez une classe `WeatherForecast` et une classe dérivée `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="021f6-270">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="021f6-271">Et supposons que l’argument de type de la méthode `Serialize` au moment de la compilation est `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="021f6-271">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="021f6-272">Dans ce scénario, la propriété `WindSpeed` n’est pas sérialisée, même si l’objet `weatherForecast` est en fait un objet `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="021f6-272">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="021f6-273">Seules les propriétés de la classe de base sont sérialisées :</span><span class="sxs-lookup"><span data-stu-id="021f6-273">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="021f6-274">Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.</span><span class="sxs-lookup"><span data-stu-id="021f6-274">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="021f6-275">Pour sérialiser les propriétés du type dérivé, utilisez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="021f6-275">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="021f6-276">Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="021f6-276">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="021f6-277">Déclarez l’objet à sérialiser en tant que `object`.</span><span class="sxs-lookup"><span data-stu-id="021f6-277">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="021f6-278">Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la propriété `WindSpeed` dans la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-278">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="021f6-279">Pour plus d’informations sur la désérialisation polymorphe, consultez [prise en charge de la désérialisation polymorphe](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="021f6-279">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="021f6-280">Autoriser les commentaires et les virgules de fin</span><span class="sxs-lookup"><span data-stu-id="021f6-280">Allow comments and trailing commas</span></span>

<span data-ttu-id="021f6-281">Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON.</span><span class="sxs-lookup"><span data-stu-id="021f6-281">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="021f6-282">Pour autoriser les commentaires dans le JSON, affectez à la propriété <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> la valeur `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="021f6-282">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="021f6-283">Et pour autoriser les virgules de fin, définissez la propriété <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> sur `true`.</span><span class="sxs-lookup"><span data-stu-id="021f6-283">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="021f6-284">L’exemple suivant montre comment autoriser les deux :</span><span class="sxs-lookup"><span data-stu-id="021f6-284">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="021f6-285">Voici un exemple de code JSON avec des commentaires et une virgule de fin :</span><span class="sxs-lookup"><span data-stu-id="021f6-285">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="021f6-286">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="021f6-286">Case-insensitive property matching</span></span>

<span data-ttu-id="021f6-287">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="021f6-287">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="021f6-288">Pour modifier ce comportement, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> sur `true`:</span><span class="sxs-lookup"><span data-stu-id="021f6-288">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="021f6-289">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="021f6-289">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="021f6-290">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="021f6-290">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="021f6-291">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-291">Handle overflow JSON</span></span>

<span data-ttu-id="021f6-292">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="021f6-292">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="021f6-293">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-293">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="021f6-294">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-294">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="021f6-295">Si vous désérialisez le JSON indiqué dans le type indiqué, les propriétés `DatesAvailable` et `SummaryWords` ne peuvent pas être placées et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="021f6-295">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="021f6-296">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de type `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="021f6-296">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="021f6-297">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la propriété `ExtensionData` :</span><span class="sxs-lookup"><span data-stu-id="021f6-297">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="021f6-298">Les</span><span class="sxs-lookup"><span data-stu-id="021f6-298">Property</span></span> |<span data-ttu-id="021f6-299">Valeur</span><span class="sxs-lookup"><span data-stu-id="021f6-299">Value</span></span>  |<span data-ttu-id="021f6-300">Notes</span><span class="sxs-lookup"><span data-stu-id="021f6-300">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="021f6-301">Date</span><span class="sxs-lookup"><span data-stu-id="021f6-301">Date</span></span>    | <span data-ttu-id="021f6-302">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="021f6-302">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="021f6-303">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="021f6-303">TemperatureCelsius</span></span>| <span data-ttu-id="021f6-304">0</span><span class="sxs-lookup"><span data-stu-id="021f6-304">0</span></span> | <span data-ttu-id="021f6-305">Incompatibilité sensible à la casse (`temperatureCelsius` dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="021f6-305">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="021f6-306">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="021f6-306">Summary</span></span> | <span data-ttu-id="021f6-307">Images</span><span class="sxs-lookup"><span data-stu-id="021f6-307">Hot</span></span> ||
| <span data-ttu-id="021f6-308">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="021f6-308">ExtensionData</span></span> | <span data-ttu-id="021f6-309">temperatureCelsius : 25</span><span class="sxs-lookup"><span data-stu-id="021f6-309">temperatureCelsius: 25</span></span> |<span data-ttu-id="021f6-310">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="021f6-310">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="021f6-311">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="021f6-311">DatesAvailable:</span></span><br>  <span data-ttu-id="021f6-312">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="021f6-312">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="021f6-313">DE 8/2/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="021f6-313">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="021f6-314">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="021f6-314">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="021f6-315">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="021f6-315">SummaryWords:</span></span><br><span data-ttu-id="021f6-316">Cool</span><span class="sxs-lookup"><span data-stu-id="021f6-316">Cool</span></span><br><span data-ttu-id="021f6-317">Venteux</span><span class="sxs-lookup"><span data-stu-id="021f6-317">Windy</span></span><br><span data-ttu-id="021f6-318">Humide</span><span class="sxs-lookup"><span data-stu-id="021f6-318">Humid</span></span> |<span data-ttu-id="021f6-319">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="021f6-319">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="021f6-320">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="021f6-320">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="021f6-321">Notez que le nom de la propriété `ExtensionData` n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="021f6-321">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="021f6-322">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="021f6-322">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="021f6-323">Ignorer la valeur null lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="021f6-323">Ignore null when deserializing</span></span>

<span data-ttu-id="021f6-324">Par défaut, si une propriété dans JSON a la valeur null, la propriété correspondante dans l’objet cible a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="021f6-324">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="021f6-325">Dans certains scénarios, la propriété cible peut avoir une valeur par défaut et vous ne souhaitez pas qu’une valeur null remplace la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="021f6-325">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="021f6-326">Par exemple, supposons que le code suivant représente votre objet cible :</span><span class="sxs-lookup"><span data-stu-id="021f6-326">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="021f6-327">Et supposons que le code JSON suivant est désérialisé :</span><span class="sxs-lookup"><span data-stu-id="021f6-327">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="021f6-328">Après la désérialisation, la propriété `Summary` de l’objet `WeatherForecastWithDefault` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="021f6-328">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="021f6-329">Pour modifier ce comportement, affectez la valeur `true`à <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-329">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="021f6-330">Avec cette option, la propriété `Summary` de l’objet `WeatherForecastWithDefault` est la valeur par défaut « no Summary » après la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="021f6-330">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="021f6-331">Les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides.</span><span class="sxs-lookup"><span data-stu-id="021f6-331">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="021f6-332">Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="021f6-332">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="021f6-333">Pour plus d’informations, consultez le [problème 40922 sur les types valeur non Nullable](https://github.com/dotnet/corefx/issues/40922) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="021f6-333">For more information, see [issue 40922 on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="021f6-334">Utf8JsonReader, Utf8JsonWriter et JsonDocument</span><span class="sxs-lookup"><span data-stu-id="021f6-334">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="021f6-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur hautes performances et à faible allocation de type forward-only pour le texte JSON codé au format UTF-8 et lu à partir de `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="021f6-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="021f6-336">Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="021f6-336">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="021f6-337">La méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> utilise `Utf8JsonReader` en coulisses.</span><span class="sxs-lookup"><span data-stu-id="021f6-337">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="021f6-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants comme `String`, `Int32`et `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="021f6-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="021f6-339">Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="021f6-339">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="021f6-340">La méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> utilise `Utf8JsonWriter` en coulisses.</span><span class="sxs-lookup"><span data-stu-id="021f6-340">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="021f6-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> permet de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="021f6-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="021f6-342">Le DOM fournit un accès aléatoire aux données dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="021f6-342">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="021f6-343">Les éléments JSON qui composent la charge utile sont accessibles via le type de <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="021f6-343">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="021f6-344">Le type de `JsonElement` fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .NET courants.</span><span class="sxs-lookup"><span data-stu-id="021f6-344">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="021f6-345">`JsonDocument` expose une propriété <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="021f6-345">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="021f6-346">Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.</span><span class="sxs-lookup"><span data-stu-id="021f6-346">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="021f6-347">Utiliser JsonDocument pour l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="021f6-347">Use JsonDocument for access to data</span></span>

<span data-ttu-id="021f6-348">L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.JsonDocument> pour l’accès aléatoire aux données dans une chaîne JSON :</span><span class="sxs-lookup"><span data-stu-id="021f6-348">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="021f6-349">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="021f6-349">The preceding code:</span></span>

* <span data-ttu-id="021f6-350">Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="021f6-350">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="021f6-351">Calcule une qualité moyenne pour les objets d’un tableau de `Students` qui ont une propriété `Grade`.</span><span class="sxs-lookup"><span data-stu-id="021f6-351">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="021f6-352">Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.</span><span class="sxs-lookup"><span data-stu-id="021f6-352">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="021f6-353">Compte les étudiants en incrémentant une variable de `count` à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="021f6-353">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="021f6-354">Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-354">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="021f6-355">Voici un exemple du JSON traité par ce code :</span><span class="sxs-lookup"><span data-stu-id="021f6-355">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="021f6-356">Utiliser JsonDocument pour écrire du code JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-356">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="021f6-357">L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="021f6-357">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="021f6-358">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="021f6-358">The preceding code:</span></span>

* <span data-ttu-id="021f6-359">Lit un fichier JSON, charge les données dans un `JsonDocument`et écrit le format JSON (Pretty-imprimed) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="021f6-359">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="021f6-360">Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.</span><span class="sxs-lookup"><span data-stu-id="021f6-360">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="021f6-361">Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer.</span><span class="sxs-lookup"><span data-stu-id="021f6-361">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="021f6-362">Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="021f6-362">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="021f6-363">Voici un exemple d’entrée JSON à traiter par l’exemple de code :</span><span class="sxs-lookup"><span data-stu-id="021f6-363">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="021f6-364">Le résultat est la sortie JSON imprimée suivante :</span><span class="sxs-lookup"><span data-stu-id="021f6-364">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="021f6-365">Utiliser Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="021f6-365">Use Utf8JsonWriter</span></span>

<span data-ttu-id="021f6-366">L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonWriter> :</span><span class="sxs-lookup"><span data-stu-id="021f6-366">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="021f6-367">Utiliser Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="021f6-367">Use Utf8JsonReader</span></span>

<span data-ttu-id="021f6-368">L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonReader> :</span><span class="sxs-lookup"><span data-stu-id="021f6-368">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="021f6-369">Le code précédent suppose que la variable `jsonUtf8` est un tableau d’octets contenant un JSON valide, encodé au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="021f6-369">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="021f6-370">Filtrer les données à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="021f6-370">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="021f6-371">L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur :</span><span class="sxs-lookup"><span data-stu-id="021f6-371">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="021f6-372">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="021f6-372">The preceding code:</span></span>

* <span data-ttu-id="021f6-373">Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="021f6-373">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="021f6-374">Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>`, à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="021f6-374">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="021f6-375">Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="021f6-375">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="021f6-376">Compte les objets et les valeurs de propriété `name` qui se terminent par « University ».</span><span class="sxs-lookup"><span data-stu-id="021f6-376">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="021f6-377">Voici un exemple JSON que le code précédent peut lire.</span><span class="sxs-lookup"><span data-stu-id="021f6-377">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="021f6-378">Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :</span><span class="sxs-lookup"><span data-stu-id="021f6-378">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="021f6-379">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="021f6-379">Additional resources</span></span>

* [<span data-ttu-id="021f6-380">Vue d’ensemble de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-380">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="021f6-381">Informations de référence sur l’API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-381">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="021f6-382">Écrire des convertisseurs personnalisés pour System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-382">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="021f6-383">Prise en charge des valeurs DateTime et DateTimeOffset dans System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="021f6-383">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="021f6-384">GitHub problèmes dans le référentiel dotnet/corefx intitulé JSON-fonctionnalité-doc</span><span class="sxs-lookup"><span data-stu-id="021f6-384">GitHub issues in the dotnet/corefx repository labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
