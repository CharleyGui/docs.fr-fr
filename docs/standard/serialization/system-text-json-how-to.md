---
title: Comment sérialiser JSON-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8ccd7afe4abb928e7723aa740507774012fc85d1
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083111"
---
# <a name="how-to-serialize-json-in-net"></a><span data-ttu-id="54472-102">Comment sérialiser JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="54472-102">How to serialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54472-103">La documentation de sérialisation JSON est en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="54472-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="54472-104">Cet article ne traite pas de tous les scénarios.</span><span class="sxs-lookup"><span data-stu-id="54472-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="54472-105">Pour plus d’informations, examinez les [problèmes liés à System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) dans le référentiel dotnet/Corefx sur GitHub, en particulier ceux étiquetés [JSON-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="54472-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="54472-106">Cet article explique comment utiliser l' <xref:System.Text.Json> espace de noms pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="54472-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="54472-107">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="54472-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="54472-108">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="54472-108">Namespaces</span></span>

<span data-ttu-id="54472-109">L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="54472-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="54472-110">L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="54472-111">Par conséquent, les exemples de code présentés dans cet article requièrent l’une des `using` directives suivantes, ou les deux :</span><span class="sxs-lookup"><span data-stu-id="54472-111">Therefore, the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="54472-112">Les attributs de <xref:System.Runtime.Serialization> l’espace de noms ne `System.Text.Json`sont actuellement pas pris en charge dans.</span><span class="sxs-lookup"><span data-stu-id="54472-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="54472-113">Comment écrire des objets .NET dans JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="54472-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="54472-114">Pour écrire du code JSON dans une chaîne, <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> appelez la méthode.</span><span class="sxs-lookup"><span data-stu-id="54472-114">To write JSON to a string, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="54472-115">L’exemple suivant utilise une surcharge avec un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="54472-115">The following example uses an overload with a generic type parameter:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="54472-116">Vous pouvez omettre le paramètre de type générique et utiliser l’inférence de type générique à la place :</span><span class="sxs-lookup"><span data-stu-id="54472-116">You can omit the generic type parameter and use generic type inference instead:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="54472-117">Voici un exemple de type à sérialiser, qui contient des collections et des classes imbriquées :</span><span class="sxs-lookup"><span data-stu-id="54472-117">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

<span data-ttu-id="54472-118">La sortie JSON est minimisés par défaut :</span><span class="sxs-lookup"><span data-stu-id="54472-118">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="54472-119">L’exemple suivant montre le même JSON, mis en forme (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="54472-119">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="54472-120">Les surcharges <xref:System.Text.Json.JsonSerializer.Serialize%2A> de vous permettent de sérialiser <xref:System.IO.Stream>vers un.</span><span class="sxs-lookup"><span data-stu-id="54472-120">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="54472-121">Les `Stream` versions Async des surcharges sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="54472-121">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="54472-122">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="54472-122">Serialize to UTF-8</span></span>

<span data-ttu-id="54472-123">Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :</span><span class="sxs-lookup"><span data-stu-id="54472-123">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="54472-124">En guise d’alternative <xref:System.Text.Json.JsonSerializer.Serialize%2A> , une surcharge qui <xref:System.Text.Json.Utf8JsonWriter> prend un est disponible.</span><span class="sxs-lookup"><span data-stu-id="54472-124">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="54472-125">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="54472-125">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="54472-126">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="54472-126">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="54472-127">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="54472-127">Serialization behavior</span></span>

* <span data-ttu-id="54472-128">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="54472-128">By default, all public properties are serialized.</span></span> <span data-ttu-id="54472-129">Vous pouvez [spécifier les propriétés à exclure](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="54472-129">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="54472-130">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères HTML dans la plage ASCII et les caractères qui doivent être placés dans une séquence d’échappement conformément à [la spécification JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="54472-130">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="54472-131">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="54472-131">By default, JSON is minified.</span></span> <span data-ttu-id="54472-132">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="54472-132">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="54472-133">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="54472-133">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="54472-134">Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="54472-134">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="54472-135">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="54472-135">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="54472-136">Pour plus d’informations, consultez le [problème sur les références circulaires](https://github.com/dotnet/corefx/issues/38579) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="54472-136">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="54472-137">Actuellement, les champs sont exclus.</span><span class="sxs-lookup"><span data-stu-id="54472-137">Currently, fields are excluded.</span></span>

<span data-ttu-id="54472-138">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="54472-138">Supported types include:</span></span>

* <span data-ttu-id="54472-139">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="54472-139">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="54472-140">[Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="54472-140">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="54472-141">Tableaux unidimensionnels et en escalier (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="54472-141">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="54472-142">`Dictionary<string,TValue>`où `TValue` est `object` ,`JsonElement`ou un poco.</span><span class="sxs-lookup"><span data-stu-id="54472-142">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="54472-143">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="54472-143">Collections from the following namespaces.</span></span> <span data-ttu-id="54472-144">Pour plus d’informations, consultez le [problème sur la prise en charge de collection](https://github.com/dotnet/corefx/issues/36643) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="54472-144">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="54472-145">Comment lire JSON dans des objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="54472-145">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="54472-146">Pour désérialiser à partir d’une chaîne, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> appelez la méthode, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-146">To deserialize from a string, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method, as shown in the following example:</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="54472-147">Pour obtenir un exemple, consultez la section [Serialize](#how-to-write-net-objects-to-json-serialize) .</span><span class="sxs-lookup"><span data-stu-id="54472-147">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="54472-148">Les objets JSON et .NET sont identiques, mais le sens est inversé.</span><span class="sxs-lookup"><span data-stu-id="54472-148">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="54472-149">Les surcharges <xref:System.Text.Json.JsonSerializer.Deserialize*> de vous permettent de désérialiser `Stream`à partir d’un.</span><span class="sxs-lookup"><span data-stu-id="54472-149">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="54472-150">Les `Stream` versions Async des surcharges sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="54472-150">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="54472-151">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="54472-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="54472-152">Pour désérialiser à partir d’UTF-8, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> appelez une surcharge qui `Utf8JsonReader` accepte un `ReadOnlySpan<byte>`ou un, comme indiqué dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="54472-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples:</span></span>

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="54472-153">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="54472-153">Deserialization behavior</span></span>

* <span data-ttu-id="54472-154">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="54472-154">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="54472-155">Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="54472-155">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="54472-156">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="54472-156">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="54472-157">La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="54472-157">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="54472-158">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="54472-158">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="54472-159">Pour plus d’informations, consultez le [problème GitHub sur la prise en charge des objets immuables](https://github.com/dotnet/corefx/issues/38569) et le [problème sur la prise en charge des propriétés en lecture seule](https://github.com/dotnet/corefx/issues/38163) dans le référentiel dotnet/corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="54472-159">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="54472-160">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="54472-160">By default, enums are supported as numbers.</span></span>
* <span data-ttu-id="54472-161">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="54472-161">Fields aren't supported.</span></span>
* <span data-ttu-id="54472-162">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="54472-162">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="54472-163">Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas) si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="54472-163">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas) if needed.</span></span>
* <span data-ttu-id="54472-164">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="54472-164">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="54472-165">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="54472-165">Serialize to formatted JSON</span></span>

<span data-ttu-id="54472-166">Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur : `true`</span><span class="sxs-lookup"><span data-stu-id="54472-166">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="54472-167">Voici un exemple de type à sérialiser et une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-167">Here's an example type to be serialized and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="54472-168">Autoriser les commentaires et les virgules de fin</span><span class="sxs-lookup"><span data-stu-id="54472-168">Allow comments and trailing commas</span></span>

<span data-ttu-id="54472-169">Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON.</span><span class="sxs-lookup"><span data-stu-id="54472-169">By default comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="54472-170">Pour autoriser les commentaires dans le JSON, affectez <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> à `JsonCommentHandling.Skip`la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="54472-170">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="54472-171">Et pour autoriser les virgules de fin, affectez <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> à `true`la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="54472-171">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="54472-172">L’exemple suivant montre comment autoriser les deux :</span><span class="sxs-lookup"><span data-stu-id="54472-172">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="54472-173">Voici un exemple de code JSON avec des commentaires et une virgule de fin :</span><span class="sxs-lookup"><span data-stu-id="54472-173">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="54472-174">Personnaliser les noms JSON</span><span class="sxs-lookup"><span data-stu-id="54472-174">Customize JSON names</span></span>

<span data-ttu-id="54472-175">Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse.</span><span class="sxs-lookup"><span data-stu-id="54472-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="54472-176">Cette section explique comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="54472-176">This section explains how to:</span></span>

* <span data-ttu-id="54472-177">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="54472-177">Customize individual property names</span></span>
* <span data-ttu-id="54472-178">Convertir tous les noms de propriété en casse mixte</span><span class="sxs-lookup"><span data-stu-id="54472-178">Convert all property names to camel case</span></span>
* <span data-ttu-id="54472-179">Implémenter une stratégie d’attribution de noms de propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="54472-179">Implement a custom property naming policy</span></span>
* <span data-ttu-id="54472-180">Convertir les clés du dictionnaire en casse mixte</span><span class="sxs-lookup"><span data-stu-id="54472-180">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="54472-181">Actuellement, il n’existe pas de prise en charge pour la conversion automatique des enum en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="54472-181">Currently, there's no support for automatically converting enums to camel case.</span></span> <span data-ttu-id="54472-182">Pour plus d’informations, consultez le [problème sur la prise en charge de la casse mixte enum](https://github.com/dotnet/corefx/issues/37725) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="54472-182">For more information, see the [issue on enum camel case support](https://github.com/dotnet/corefx/issues/37725) in the dotnet/corefx repository on GitHub.</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="54472-183">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="54472-183">Customize individual property names</span></span>

<span data-ttu-id="54472-184">Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="54472-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="54472-185">Voici un exemple de type pour sérialiser et JSON obtenu :</span><span class="sxs-lookup"><span data-stu-id="54472-185">Here's an example type to serialize and resulting JSON:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="54472-186">Nom de propriété défini par cet attribut :</span><span class="sxs-lookup"><span data-stu-id="54472-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="54472-187">S’applique dans les deux directions, pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="54472-188">Est prioritaire sur les stratégies d’attribution de noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="54472-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="54472-189">Utiliser la casse mixte pour tous les noms de propriété JSON</span><span class="sxs-lookup"><span data-stu-id="54472-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="54472-190">Pour utiliser la casse mixte pour tous les noms de propriétés <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> JSON `JsonNamingPolicy.CamelCase`, affectez la valeur à, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="54472-191">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-191">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="54472-192">La stratégie de nommage de propriété casse mixte :</span><span class="sxs-lookup"><span data-stu-id="54472-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="54472-193">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="54472-194">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="54472-194">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="54472-195">Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée</span><span class="sxs-lookup"><span data-stu-id="54472-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="54472-196">Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe <xref:System.Text.Json.JsonNamingPolicy> qui dérive de <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> et substituez la méthode, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="54472-197">Définissez ensuite la <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :</span><span class="sxs-lookup"><span data-stu-id="54472-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="54472-198">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-198">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="54472-199">La stratégie d’attribution de noms de propriété JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="54472-200">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="54472-201">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="54472-201">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="54472-202">Clés de dictionnaire de casse mixte</span><span class="sxs-lookup"><span data-stu-id="54472-202">Camel case dictionary keys</span></span>

<span data-ttu-id="54472-203">Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>`, les `string` clés peuvent être converties en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="54472-203">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="54472-204">Pour ce faire, affectez `JsonNamingPolicy.CamelCase`à la valeur <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-204">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="54472-205">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-205">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="54472-206">Propriété</span><span class="sxs-lookup"><span data-stu-id="54472-206">Property</span></span> |<span data-ttu-id="54472-207">Valeur</span><span class="sxs-lookup"><span data-stu-id="54472-207">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="54472-208">Date</span><span class="sxs-lookup"><span data-stu-id="54472-208">Date</span></span>    | <span data-ttu-id="54472-209">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="54472-209">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="54472-210">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="54472-210">TemperatureC</span></span>| <span data-ttu-id="54472-211">25</span><span class="sxs-lookup"><span data-stu-id="54472-211">25</span></span> |
| <span data-ttu-id="54472-212">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="54472-212">Summary</span></span>| <span data-ttu-id="54472-213">Images</span><span class="sxs-lookup"><span data-stu-id="54472-213">Hot</span></span>|
| <span data-ttu-id="54472-214">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="54472-214">TemperatureRanges</span></span> | <span data-ttu-id="54472-215">Froid, 20</span><span class="sxs-lookup"><span data-stu-id="54472-215">Cold, 20</span></span><br><span data-ttu-id="54472-216">Chaud, 40</span><span class="sxs-lookup"><span data-stu-id="54472-216">Hot, 40</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

<span data-ttu-id="54472-217">La stratégie d’attribution de noms de casse mixte s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-217">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="54472-218">Exclure des propriétés</span><span class="sxs-lookup"><span data-stu-id="54472-218">Exclude properties</span></span>

<span data-ttu-id="54472-219">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="54472-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="54472-220">Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="54472-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="54472-221">Cette section explique comment exclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="54472-221">This section explains how to exclude:</span></span>

* <span data-ttu-id="54472-222">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="54472-222">Individual properties</span></span>
* <span data-ttu-id="54472-223">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="54472-223">All read-only properties</span></span>
* <span data-ttu-id="54472-224">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="54472-224">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="54472-225">Exclure des propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="54472-225">Exclude individual properties</span></span>

<span data-ttu-id="54472-226">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="54472-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="54472-227">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-227">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="54472-228">Exclure toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="54472-228">Exclude all read-only properties</span></span>

<span data-ttu-id="54472-229">Pour exclure toutes les propriétés en lecture seule, affectez `true`la <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> valeur à, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="54472-230">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-230">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="54472-231">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-231">This option applies only to serialization.</span></span> <span data-ttu-id="54472-232">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="54472-232">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="54472-233">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="54472-233">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="54472-234">Exclure toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="54472-234">Exclude all null value properties</span></span>

<span data-ttu-id="54472-235">Pour exclure toutes les propriétés de valeur null, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> affectez `true`à la propriété la valeur, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="54472-236">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="54472-237">Propriété</span><span class="sxs-lookup"><span data-stu-id="54472-237">Property</span></span> |<span data-ttu-id="54472-238">Valeur</span><span class="sxs-lookup"><span data-stu-id="54472-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="54472-239">Date</span><span class="sxs-lookup"><span data-stu-id="54472-239">Date</span></span>    | <span data-ttu-id="54472-240">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="54472-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="54472-241">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="54472-241">TemperatureC</span></span>| <span data-ttu-id="54472-242">25</span><span class="sxs-lookup"><span data-stu-id="54472-242">25</span></span> |
| <span data-ttu-id="54472-243">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="54472-243">Summary</span></span>| <span data-ttu-id="54472-244">Null</span><span class="sxs-lookup"><span data-stu-id="54472-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="54472-245">Ce paramètre s’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="54472-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="54472-246">Pendant la désérialisation, les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides.</span><span class="sxs-lookup"><span data-stu-id="54472-246">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="54472-247">Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="54472-247">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="54472-248">Pour plus d’informations, consultez le [problème sur les types valeur non Nullable](https://github.com/dotnet/corefx/issues/40922) dans le référentiel dotnet/Corefx sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="54472-248">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="54472-249">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="54472-249">Case-insensitive property matching</span></span>

<span data-ttu-id="54472-250">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="54472-250">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="54472-251">Pour modifier ce comportement, affectez <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> à `true`la valeur :</span><span class="sxs-lookup"><span data-stu-id="54472-251">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="54472-252">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="54472-252">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="54472-253">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="54472-253">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="54472-254">Inclure les propriétés des classes dérivées</span><span class="sxs-lookup"><span data-stu-id="54472-254">Include properties of derived classes</span></span>

<span data-ttu-id="54472-255">La sérialisation polymorphe n’est pas prise en charge lorsque vous spécifiez au moment de la compilation le type à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="54472-255">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="54472-256">Par exemple, supposons que vous `WeatherForecast` avez une classe et une `WeatherForecastWithWind`classe dérivée :</span><span class="sxs-lookup"><span data-stu-id="54472-256">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

<span data-ttu-id="54472-257">Et supposons que le type passé à la méthode au `Serialize` `WeatherForecast`moment de la compilation, ou inféré par celle-ci :</span><span class="sxs-lookup"><span data-stu-id="54472-257">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="54472-258">Dans ce scénario, la `WindSpeed` propriété n’est pas sérialisée, même `weatherForecast` si l’objet est `WeatherForecastWithWind` en fait un objet.</span><span class="sxs-lookup"><span data-stu-id="54472-258">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="54472-259">Seules les propriétés de la classe de base sont sérialisées :</span><span class="sxs-lookup"><span data-stu-id="54472-259">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="54472-260">Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.</span><span class="sxs-lookup"><span data-stu-id="54472-260">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="54472-261">Pour sérialiser les propriétés du type dérivé, utilisez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="54472-261">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="54472-262">Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="54472-262">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="54472-263">Déclarez l’objet à sérialiser en `object`tant que.</span><span class="sxs-lookup"><span data-stu-id="54472-263">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="54472-264">Dans l’exemple de scénario précédent, les deux approches `WindSpeed` entraînent l’inclusion de la propriété dans la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="54472-264">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="54472-265">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="54472-265">Handle overflow JSON</span></span>

<span data-ttu-id="54472-266">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="54472-266">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="54472-267">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-267">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="54472-268">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="54472-268">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
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

<span data-ttu-id="54472-269">Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` propriétés `SummaryWords` et ne sont pas visibles et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="54472-269">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="54472-270">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de `Dictionary<string,object>` type `Dictionary<string,JsonElement>`ou :</span><span class="sxs-lookup"><span data-stu-id="54472-270">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

<span data-ttu-id="54472-271">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé- `ExtensionData` valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="54472-271">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="54472-272">Propriété</span><span class="sxs-lookup"><span data-stu-id="54472-272">Property</span></span> |<span data-ttu-id="54472-273">Valeur</span><span class="sxs-lookup"><span data-stu-id="54472-273">Value</span></span>  |<span data-ttu-id="54472-274">Notes</span><span class="sxs-lookup"><span data-stu-id="54472-274">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="54472-275">Date</span><span class="sxs-lookup"><span data-stu-id="54472-275">Date</span></span>    | <span data-ttu-id="54472-276">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="54472-276">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="54472-277">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="54472-277">TemperatureC</span></span>| <span data-ttu-id="54472-278">0</span><span class="sxs-lookup"><span data-stu-id="54472-278">0</span></span> | <span data-ttu-id="54472-279">Incompatibilité sensible à la`temperatureC` casse (dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="54472-279">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="54472-280">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="54472-280">Summary</span></span> | <span data-ttu-id="54472-281">Images</span><span class="sxs-lookup"><span data-stu-id="54472-281">Hot</span></span> ||
| <span data-ttu-id="54472-282">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="54472-282">ExtensionData</span></span> | <span data-ttu-id="54472-283">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="54472-283">temperatureC: 25</span></span> |<span data-ttu-id="54472-284">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="54472-284">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="54472-285">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="54472-285">DatesAvailable:</span></span><br>  <span data-ttu-id="54472-286">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="54472-286">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="54472-287">DE 8/2/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="54472-287">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="54472-288">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="54472-288">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="54472-289">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="54472-289">SummaryWords:</span></span><br><span data-ttu-id="54472-290">Cool</span><span class="sxs-lookup"><span data-stu-id="54472-290">Cool</span></span><br><span data-ttu-id="54472-291">Venteux</span><span class="sxs-lookup"><span data-stu-id="54472-291">Windy</span></span><br><span data-ttu-id="54472-292">Humide</span><span class="sxs-lookup"><span data-stu-id="54472-292">Humid</span></span> |<span data-ttu-id="54472-293">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="54472-293">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="54472-294">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="54472-294">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
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

<span data-ttu-id="54472-295">Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="54472-295">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="54472-296">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="54472-296">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="54472-297">Utiliser Utf8JsonWriter directement</span><span class="sxs-lookup"><span data-stu-id="54472-297">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="54472-298">L’exemple suivant montre comment utiliser directement la <xref:System.Text.Json.Utf8JsonWriter> classe.</span><span class="sxs-lookup"><span data-stu-id="54472-298">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="54472-299">Utiliser Utf8JsonReader directement</span><span class="sxs-lookup"><span data-stu-id="54472-299">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="54472-300">L’exemple suivant montre comment utiliser directement la <xref:System.Text.Json.Utf8JsonReader> classe.</span><span class="sxs-lookup"><span data-stu-id="54472-300">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="54472-301">Le code suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="54472-301">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

## <a name="additional-resources"></a><span data-ttu-id="54472-302">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="54472-302">Additional resources</span></span>

* [<span data-ttu-id="54472-303">Vue d’ensemble de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="54472-303">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="54472-304">Informations de référence sur l’API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="54472-304">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="54472-305">Prise en charge des valeurs DateTime et DateTimeOffset dans System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="54472-305">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
