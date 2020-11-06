---
title: Comment sérialiser et désérialiser JSON à l’aide de C#-.NET
description: "Découvrez comment utiliser l' :::no-loc(System.Text.Json)::: espace de noms pour sérialiser et désérialiser à partir de JSON dans .net. Comprend un exemple de code."
ms.date: 11/05/2020
no-loc:
- ':::no-loc(System.Text.Json):::'
- ':::no-loc(Newtonsoft.Json):::'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c1358b2b63a92cb50b853043adbfaae23ccd897
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329870"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="de54e-104">Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="de54e-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="de54e-105">Cet article explique comment utiliser l' <xref::::no-loc(System.Text.Json):::?displayProperty=fullName> espace de noms pour sérialiser et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="de54e-105">This article shows how to use the <xref::::no-loc(System.Text.Json):::?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="de54e-106">Si vous transférez du code existant à partir de `:::no-loc(Newtonsoft.Json):::` , consultez [Comment migrer vers `:::no-loc(System.Text.Json):::` ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="de54e-106">If you're porting existing code from `:::no-loc(Newtonsoft.Json):::`, see [How to migrate to `:::no-loc(System.Text.Json):::`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="de54e-107">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="de54e-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="de54e-108">La majeure partie de l’exemple de code de sérialisation affecte <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` la valeur « joli Printing » au format JSON (avec mise en retrait et espace blanc pour la lisibilité humaine).</span><span class="sxs-lookup"><span data-stu-id="de54e-108">Most of the serialization sample code sets <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="de54e-109">Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="de54e-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="de54e-110">Les exemples de code font référence à la classe et aux variantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="de54e-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="de54e-111">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="de54e-111">Namespaces</span></span>

<span data-ttu-id="de54e-112">L' <xref::::no-loc(System.Text.Json):::> espace de noms contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="de54e-112">The <xref::::no-loc(System.Text.Json):::> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="de54e-113">L' <xref::::no-loc(System.Text.Json):::.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-113">The <xref::::no-loc(System.Text.Json):::.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="de54e-114">Les exemples de code présentés dans cet article requièrent des `using` directives pour l’un de ces espaces de noms ou les deux :</span><span class="sxs-lookup"><span data-stu-id="de54e-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using :::no-loc(System.Text.Json):::;
using :::no-loc(System.Text.Json):::.Serialization;
```

<span data-ttu-id="de54e-115">Les attributs de l' <xref:System.Runtime.Serialization> espace de noms ne sont pas pris en charge dans `:::no-loc(System.Text.Json):::` .</span><span class="sxs-lookup"><span data-stu-id="de54e-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `:::no-loc(System.Text.Json):::`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="de54e-116">Comment écrire des objets .NET dans JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="de54e-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="de54e-117">Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="de54e-117">To write JSON to a string or to a file, call the <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="de54e-118">L’exemple suivant crée JSON sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="de54e-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-119">L’exemple suivant utilise du code synchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-120">L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-121">Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="de54e-122">Une surcharge de `Serialize()` prend un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="de54e-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="de54e-123">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="de54e-123">Serialization example</span></span>

<span data-ttu-id="de54e-124">Voici un exemple de classe qui contient des propriétés de type collection et un type défini par l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="de54e-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> <span data-ttu-id="de54e-125">« POCO » signifie « [Plain Old CLR Object](https://en.wikipedia.org/wiki/Plain_old_CLR_object)».</span><span class="sxs-lookup"><span data-stu-id="de54e-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="de54e-126">Un POCO est un type .NET qui ne dépend d’aucun type spécifique à l’infrastructure, par exemple par le biais de l’héritage ou des attributs.</span><span class="sxs-lookup"><span data-stu-id="de54e-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="de54e-127">La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="de54e-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="de54e-128">La sortie JSON est minimisés par défaut :</span><span class="sxs-lookup"><span data-stu-id="de54e-128">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="de54e-129">L’exemple suivant montre le même JSON, mais formaté (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="de54e-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="de54e-130">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="de54e-130">Serialize to UTF-8</span></span>

<span data-ttu-id="de54e-131">Pour sérialiser vers UTF-8, appelez la <xref::::no-loc(System.Text.Json):::.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :</span><span class="sxs-lookup"><span data-stu-id="de54e-131">To serialize to UTF-8, call the <xref::::no-loc(System.Text.Json):::.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-132">Une <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A> surcharge qui prend un <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter> est également disponible.</span><span class="sxs-lookup"><span data-stu-id="de54e-132">A <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A> overload that takes a <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="de54e-133">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="de54e-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="de54e-134">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="de54e-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="de54e-135">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="de54e-135">Serialization behavior</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="de54e-136">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="de54e-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="de54e-137">Vous pouvez [spécifier des propriétés à ignorer](#ignore-properties).</span><span class="sxs-lookup"><span data-stu-id="de54e-137">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="de54e-138">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="de54e-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="de54e-139">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="de54e-139">By default, JSON is minified.</span></span> <span data-ttu-id="de54e-140">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="de54e-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="de54e-141">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="de54e-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="de54e-142">Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="de54e-142">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="de54e-143">Par défaut, les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="de54e-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="de54e-144">Vous pouvez [conserver les références et gérer les références circulaires](#preserve-references-and-handle-circular-references).</span><span class="sxs-lookup"><span data-stu-id="de54e-144">You can [preserve references and handle circular references](#preserve-references-and-handle-circular-references).</span></span>
* <span data-ttu-id="de54e-145">Par défaut, les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="de54e-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="de54e-146">Vous pouvez [inclure des champs](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="de54e-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="de54e-147">Lorsque vous utilisez :::no-loc(System.Text.Json)::: indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="de54e-147">When you use :::no-loc(System.Text.Json)::: indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="de54e-148">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="de54e-148">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="de54e-149">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="de54e-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="de54e-150">Vous pouvez [spécifier des propriétés à ignorer](#ignore-properties).</span><span class="sxs-lookup"><span data-stu-id="de54e-150">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="de54e-151">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="de54e-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="de54e-152">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="de54e-152">By default, JSON is minified.</span></span> <span data-ttu-id="de54e-153">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="de54e-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="de54e-154">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="de54e-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="de54e-155">Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="de54e-155">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="de54e-156">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="de54e-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="de54e-157">Les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="de54e-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="de54e-158">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="de54e-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="de54e-159">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="de54e-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="de54e-160">[Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="de54e-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="de54e-161">Tableaux unidimensionnels et en escalier ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="de54e-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="de54e-162">Collections et dictionnaires à partir des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="de54e-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="de54e-163">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="de54e-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="de54e-164">[Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="de54e-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="de54e-165">Tableaux unidimensionnels et en escalier ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="de54e-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="de54e-166">`Dictionary<string,TValue>` où `TValue` est `object` , `JsonElement` ou un poco.</span><span class="sxs-lookup"><span data-stu-id="de54e-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="de54e-167">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="de54e-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="de54e-168">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="de54e-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="de54e-169">Comment lire JSON dans des objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="de54e-169">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="de54e-170">Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la <xref::::no-loc(System.Text.Json):::.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="de54e-170">To deserialize from a string or a file, call the <xref::::no-loc(System.Text.Json):::.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="de54e-171">L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la `WeatherForecastWithPOCOs` classe indiquée précédemment pour l' [exemple de sérialisation](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="de54e-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="de54e-172">Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="de54e-173">Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la <xref::::no-loc(System.Text.Json):::.JsonSerializer.DeserializeAsync%2A> méthode :</span><span class="sxs-lookup"><span data-stu-id="de54e-173">To deserialize from a file by using asynchronous code, call the <xref::::no-loc(System.Text.Json):::.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="de54e-174">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="de54e-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="de54e-175">Pour désérialiser à partir d’UTF-8, appelez une <xref::::no-loc(System.Text.Json):::.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> surcharge qui accepte un `Utf8JsonReader` ou un `ReadOnlySpan<byte>` , comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="de54e-175">To deserialize from UTF-8, call a <xref::::no-loc(System.Text.Json):::.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="de54e-176">Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="de54e-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="de54e-177">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="de54e-177">Deserialization behavior</span></span>

<span data-ttu-id="de54e-178">Les comportements suivants s’appliquent lors de la désérialisation de JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="de54e-179">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="de54e-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="de54e-180">Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="de54e-180">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="de54e-181">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="de54e-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="de54e-182">Les constructeurs non publics sont ignorés par le sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="de54e-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="de54e-183">La désérialisation des objets immuables ou des propriétés en lecture seule est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="de54e-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="de54e-184">Consultez [les types immuables et les enregistrements](#immutable-types-and-records).</span><span class="sxs-lookup"><span data-stu-id="de54e-184">See [Immutable types and Records](#immutable-types-and-records).</span></span>
* <span data-ttu-id="de54e-185">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="de54e-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="de54e-186">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="de54e-186">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="de54e-187">Par défaut, les champs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="de54e-187">By default, fields are ignored.</span></span> <span data-ttu-id="de54e-188">Vous pouvez [inclure des champs](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="de54e-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="de54e-189">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="de54e-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="de54e-190">Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="de54e-190">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="de54e-191">La [profondeur maximale par défaut](xref::::no-loc(System.Text.Json):::.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="de54e-191">The [default maximum depth](xref::::no-loc(System.Text.Json):::.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="de54e-192">Lorsque vous utilisez :::no-loc(System.Text.Json)::: indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="de54e-192">When you use :::no-loc(System.Text.Json)::: indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="de54e-193">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="de54e-193">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="de54e-194">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="de54e-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="de54e-195">Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="de54e-195">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span> <span data-ttu-id="de54e-196">Par défaut, les applications ASP.NET Core [spécifient le non-respect](#web-defaults-for-jsonserializeroptions)de la casse.</span><span class="sxs-lookup"><span data-stu-id="de54e-196">ASP.NET Core apps [specify case-insensitivity by default](#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="de54e-197">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="de54e-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="de54e-198">Un constructeur sans paramètre, qui peut être public, Internal ou Private, est utilisé pour la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="de54e-199">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="de54e-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="de54e-200">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="de54e-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="de54e-201">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="de54e-201">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="de54e-202">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="de54e-202">Fields aren't supported.</span></span>
* <span data-ttu-id="de54e-203">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="de54e-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="de54e-204">Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="de54e-204">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="de54e-205">La [profondeur maximale par défaut](xref::::no-loc(System.Text.Json):::.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="de54e-205">The [default maximum depth](xref::::no-loc(System.Text.Json):::.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="de54e-206">Lorsque vous utilisez :::no-loc(System.Text.Json)::: indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="de54e-206">When you use :::no-loc(System.Text.Json)::: indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="de54e-207">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="de54e-207">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="de54e-208">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="de54e-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="de54e-209">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="de54e-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="de54e-210">Pour imprimer la sortie JSON, définissez <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true` :</span><span class="sxs-lookup"><span data-stu-id="de54e-210">To pretty-print the JSON output, set <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="de54e-211">Voici un exemple de type à sérialiser et à imprimer une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a><span data-ttu-id="de54e-212">Inclure les champs</span><span class="sxs-lookup"><span data-stu-id="de54e-212">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-213">Utilisez le <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> paramètre global ou l’attribut [[JsonInclude]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIncludeAttribute) pour inclure les champs lors de la sérialisation ou de la désérialisation, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-213">Use the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

<span data-ttu-id="de54e-214">Pour ignorer les champs en lecture seule, utilisez le <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.</span><span class="sxs-lookup"><span data-stu-id="de54e-214">To ignore read-only fields, use the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-215">Les champs ne sont pas pris en charge dans :::no-loc(System.Text.Json)::: dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-215">Fields are not supported in :::no-loc(System.Text.Json)::: in .NET Core 3.1.</span></span> <span data-ttu-id="de54e-216">Les [convertisseurs personnalisés](system-text-json-converters-how-to.md) peuvent fournir cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="de54e-216">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="customize-json-names-and-values"></a><span data-ttu-id="de54e-217">Personnaliser les noms et les valeurs JSON</span><span class="sxs-lookup"><span data-stu-id="de54e-217">Customize JSON names and values</span></span>

<span data-ttu-id="de54e-218">Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse.</span><span class="sxs-lookup"><span data-stu-id="de54e-218">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="de54e-219">Les valeurs enum sont représentées sous forme de nombres.</span><span class="sxs-lookup"><span data-stu-id="de54e-219">Enum values are represented as numbers.</span></span> <span data-ttu-id="de54e-220">Cette section explique comment :</span><span class="sxs-lookup"><span data-stu-id="de54e-220">This section explains how to:</span></span>

* [<span data-ttu-id="de54e-221">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="de54e-221">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="de54e-222">Convertir tous les noms de propriété en casse mixte</span><span class="sxs-lookup"><span data-stu-id="de54e-222">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="de54e-223">Implémenter une stratégie d’attribution de noms de propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="de54e-223">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="de54e-224">Convertir les clés du dictionnaire en casse mixte</span><span class="sxs-lookup"><span data-stu-id="de54e-224">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="de54e-225">Convertir des enums en chaînes et casse mixte</span><span class="sxs-lookup"><span data-stu-id="de54e-225">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="de54e-226">Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="de54e-226">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="de54e-227">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="de54e-227">Customize individual property names</span></span>

<span data-ttu-id="de54e-228">Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref::::no-loc(System.Text.Json):::.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="de54e-228">To set the name of individual properties, use the [[JsonPropertyName]](xref::::no-loc(System.Text.Json):::.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="de54e-229">Voici un exemple de type pour sérialiser et JSON obtenu :</span><span class="sxs-lookup"><span data-stu-id="de54e-229">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="de54e-230">Nom de propriété défini par cet attribut :</span><span class="sxs-lookup"><span data-stu-id="de54e-230">The property name set by this attribute:</span></span>

* <span data-ttu-id="de54e-231">S’applique dans les deux directions, pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-231">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="de54e-232">Est prioritaire sur les stratégies d’attribution de noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="de54e-232">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="de54e-233">Utiliser la casse mixte pour tous les noms de propriété JSON</span><span class="sxs-lookup"><span data-stu-id="de54e-233">Use camel case for all JSON property names</span></span>

<span data-ttu-id="de54e-234">Pour utiliser la casse mixte pour tous les noms de propriétés JSON, affectez <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> la valeur à `JsonNamingPolicy.CamelCase` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-234">To use camel case for all JSON property names, set <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="de54e-235">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-235">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="de54e-236">La stratégie de nommage de propriété casse mixte :</span><span class="sxs-lookup"><span data-stu-id="de54e-236">The camel case property naming policy:</span></span>

* <span data-ttu-id="de54e-237">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-237">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="de54e-238">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="de54e-238">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="de54e-239">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.</span><span class="sxs-lookup"><span data-stu-id="de54e-239">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="de54e-240">Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée</span><span class="sxs-lookup"><span data-stu-id="de54e-240">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="de54e-241">Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy> et substituez la <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy.ConvertName%2A> méthode, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-241">To use a custom JSON property naming policy, create a class that derives from <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy> and override the <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="de54e-242">Définissez ensuite la <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :</span><span class="sxs-lookup"><span data-stu-id="de54e-242">Then set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-243">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-243">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="de54e-244">La stratégie d’attribution de noms de propriété JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-244">The JSON property naming policy:</span></span>

* <span data-ttu-id="de54e-245">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-245">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="de54e-246">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="de54e-246">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="de54e-247">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.</span><span class="sxs-lookup"><span data-stu-id="de54e-247">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="de54e-248">Clés de dictionnaire de casse mixte</span><span class="sxs-lookup"><span data-stu-id="de54e-248">Camel case dictionary keys</span></span>

<span data-ttu-id="de54e-249">Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>` , les `string` clés peuvent être converties en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="de54e-249">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="de54e-250">Pour ce faire, affectez <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.DictionaryKeyPolicy> à `JsonNamingPolicy.CamelCase` la valeur, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-250">To do that, set <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-251">La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` provoquerait une sortie JSON similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-251">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="de54e-252">La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-252">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="de54e-253">Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="de54e-253">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="de54e-254">Enums en tant que chaînes</span><span class="sxs-lookup"><span data-stu-id="de54e-254">Enums as strings</span></span>

<span data-ttu-id="de54e-255">Par défaut, les enums sont sérialisés en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="de54e-255">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="de54e-256">Pour sérialiser les noms d’enum sous forme de chaînes, utilisez <xref::::no-loc(System.Text.Json):::.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="de54e-256">To serialize enum names as strings, use the <xref::::no-loc(System.Text.Json):::.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="de54e-257">Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :</span><span class="sxs-lookup"><span data-stu-id="de54e-257">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="de54e-258">Si le résumé est `Hot` , par défaut, le JSON sérialisé a la valeur numérique 3 :</span><span class="sxs-lookup"><span data-stu-id="de54e-258">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="de54e-259">L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :</span><span class="sxs-lookup"><span data-stu-id="de54e-259">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-260">Le JSON obtenu ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-260">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="de54e-261">Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-261">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a><span data-ttu-id="de54e-262">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="de54e-262">Ignore properties</span></span>

<span data-ttu-id="de54e-263">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="de54e-263">By default, all public properties are serialized.</span></span> <span data-ttu-id="de54e-264">Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="de54e-264">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="de54e-265">Cette section explique comment ignorer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="de54e-265">This section explains how to ignore:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="de54e-266">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="de54e-266">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="de54e-267">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="de54e-267">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="de54e-268">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="de54e-268">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="de54e-269">Toutes les propriétés de valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="de54e-269">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="de54e-270">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="de54e-270">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="de54e-271">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="de54e-271">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="de54e-272">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="de54e-272">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a><span data-ttu-id="de54e-273">Ignorer les propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="de54e-273">Ignore individual properties</span></span>

<span data-ttu-id="de54e-274">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="de54e-274">To ignore individual properties, use the [[JsonIgnore]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="de54e-275">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-275">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-276">Vous pouvez spécifier une exclusion conditionnelle en définissant la propriété de l’attribut [[JsonIgnore]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreAttribute) `Condition` .</span><span class="sxs-lookup"><span data-stu-id="de54e-276">You can specify conditional exclusion by setting the [[JsonIgnore]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="de54e-277">L' <xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreCondition> énumération fournit les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="de54e-277">The <xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="de54e-278">`Always` -La propriété est toujours ignorée.</span><span class="sxs-lookup"><span data-stu-id="de54e-278">`Always` - The property is always ignored.</span></span> <span data-ttu-id="de54e-279">Si aucun `Condition` n’est spécifié, cette option est utilisée.</span><span class="sxs-lookup"><span data-stu-id="de54e-279">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="de54e-280">`Never` -La propriété est toujours sérialisée et désérialisée, quels que soient `DefaultIgnoreCondition` les `IgnoreReadOnlyProperties` `IgnoreReadOnlyFields` paramètres globaux, et.</span><span class="sxs-lookup"><span data-stu-id="de54e-280">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="de54e-281">`WhenWritingDefault` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` ou d’un type valeur `default` .</span><span class="sxs-lookup"><span data-stu-id="de54e-281">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null` or a value type `default`.</span></span>
* <span data-ttu-id="de54e-282">`WhenWritingNull` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` .</span><span class="sxs-lookup"><span data-stu-id="de54e-282">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`.</span></span>

<span data-ttu-id="de54e-283">L’exemple suivant illustre l’utilisation de la propriété de l’attribut [[JsonIgnore]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreAttribute) `Condition` :</span><span class="sxs-lookup"><span data-stu-id="de54e-283">The following example illustrates use of the [[JsonIgnore]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a><span data-ttu-id="de54e-284">Ignorer toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="de54e-284">Ignore all read-only properties</span></span>

<span data-ttu-id="de54e-285">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="de54e-285">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="de54e-286">Pour ignorer toutes les propriétés en lecture seule lors de la sérialisation, affectez la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> à `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-286">To ignore all read-only properties when serializing, set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-287">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-287">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="de54e-288">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-288">This option applies only to serialization.</span></span> <span data-ttu-id="de54e-289">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="de54e-289">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-290">Cette option s’applique uniquement aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="de54e-290">This option applies only to properties.</span></span> <span data-ttu-id="de54e-291">Pour ignorer les champs en lecture seule lors de la [sérialisation des champs](#include-fields), utilisez le <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.</span><span class="sxs-lookup"><span data-stu-id="de54e-291">To ignore read-only fields when [serializing fields](#include-fields), use the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

### <a name="ignore-all-null-value-properties"></a><span data-ttu-id="de54e-292">Ignorer toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="de54e-292">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-293">Pour ignorer toutes les propriétés de valeur null, affectez la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreCondition.WhenWritingNull> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-293">To ignore all null-value properties, set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-294">Pour ignorer toutes les propriétés de valeur null lors de la sérialisation, affectez la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreNullValues> à la propriété `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-294">To ignore all null-value properties when serializing, set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-295">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-295">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="de54e-296">Property</span><span class="sxs-lookup"><span data-stu-id="de54e-296">Property</span></span> |<span data-ttu-id="de54e-297">Valeur</span><span class="sxs-lookup"><span data-stu-id="de54e-297">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="de54e-298">Date</span><span class="sxs-lookup"><span data-stu-id="de54e-298">Date</span></span>    | <span data-ttu-id="de54e-299">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="de54e-299">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="de54e-300">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="de54e-300">TemperatureCelsius</span></span>| <span data-ttu-id="de54e-301">25</span><span class="sxs-lookup"><span data-stu-id="de54e-301">25</span></span> |
| <span data-ttu-id="de54e-302">Résumé</span><span class="sxs-lookup"><span data-stu-id="de54e-302">Summary</span></span>| <span data-ttu-id="de54e-303">null</span><span class="sxs-lookup"><span data-stu-id="de54e-303">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a><span data-ttu-id="de54e-304">Ignorer toutes les propriétés de valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="de54e-304">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-305">Pour empêcher la sérialisation des valeurs par défaut dans les propriétés de type valeur, affectez la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreCondition.WhenWritingDefault> , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-305">To prevent serialization of default values in value type properties, set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref::::no-loc(System.Text.Json):::.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="de54e-306">Le `WhenWritingDefault` paramètre empêche également la sérialisation des propriétés de type de référence de valeur null.</span><span class="sxs-lookup"><span data-stu-id="de54e-306">The `WhenWritingDefault` setting also prevents serialization of null-value reference type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-307">Il n’existe aucune méthode intégrée pour empêcher la sérialisation des propriétés avec des valeurs par défaut de type valeur dans :::no-loc(System.Text.Json)::: dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-307">There is no built-in way to prevent serialization of properties with value type defaults in :::no-loc(System.Text.Json)::: in .NET Core 3.1.</span></span>
::: zone-end

## <a name="customize-character-encoding"></a><span data-ttu-id="de54e-308">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="de54e-308">Customize character encoding</span></span>

<span data-ttu-id="de54e-309">Par défaut, le sérialiseur échappe tous les caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="de54e-309">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="de54e-310">Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.</span><span class="sxs-lookup"><span data-stu-id="de54e-310">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="de54e-311">Par exemple, si la `Summary` propriété a la valeur cyrillique Жарко, l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="de54e-311">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="de54e-312">Sérialiser les jeux de caractères de la langue</span><span class="sxs-lookup"><span data-stu-id="de54e-312">Serialize language character sets</span></span>

<span data-ttu-id="de54e-313">Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-313">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="de54e-314">Ce code n’échappe pas aux caractères cyrilliques ou grecs.</span><span class="sxs-lookup"><span data-stu-id="de54e-314">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="de54e-315">Si la `Summary` propriété a la valeur cyrillique Жарко, l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="de54e-315">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="de54e-316">Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="de54e-316">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="de54e-317">Sérialiser des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="de54e-317">Serialize specific characters</span></span>

<span data-ttu-id="de54e-318">Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés.</span><span class="sxs-lookup"><span data-stu-id="de54e-318">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="de54e-319">L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :</span><span class="sxs-lookup"><span data-stu-id="de54e-319">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="de54e-320">Voici un exemple de JSON généré par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="de54e-320">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="de54e-321">Sérialiser tous les caractères</span><span class="sxs-lookup"><span data-stu-id="de54e-321">Serialize all characters</span></span>

<span data-ttu-id="de54e-322">Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-322">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="de54e-323">Par rapport à l’encodeur par défaut, l' `UnsafeRelaxedJsonEscaping` encodeur est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :</span><span class="sxs-lookup"><span data-stu-id="de54e-323">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="de54e-324">Elle n’échappe pas les caractères HTML, tels que `<` ,, `>` `&` et `'` .</span><span class="sxs-lookup"><span data-stu-id="de54e-324">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="de54e-325">Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu* de caractères.</span><span class="sxs-lookup"><span data-stu-id="de54e-325">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="de54e-326">Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="de54e-326">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="de54e-327">Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="de54e-327">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="de54e-328">N’autorisez jamais l' `UnsafeRelaxedJsonEscaping` émission de la sortie brute dans une page HTML ou un `<script>` élément.</span><span class="sxs-lookup"><span data-stu-id="de54e-328">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="de54e-329">Sérialiser les propriétés des classes dérivées</span><span class="sxs-lookup"><span data-stu-id="de54e-329">Serialize properties of derived classes</span></span>

<span data-ttu-id="de54e-330">La sérialisation d’une hiérarchie de type polymorphe n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="de54e-330">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="de54e-331">Par exemple, si une propriété est définie comme une interface ou une classe abstraite, seules les propriétés définies sur l’interface ou la classe abstraite sont sérialisées, même si le type de runtime a des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="de54e-331">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="de54e-332">Les exceptions à ce comportement sont expliquées dans cette section.</span><span class="sxs-lookup"><span data-stu-id="de54e-332">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="de54e-333">Par exemple, supposons que vous avez une `WeatherForecast` classe et une classe dérivée `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="de54e-333">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="de54e-334">Et supposons que l’argument de type de la `Serialize` méthode au moment de la compilation est `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="de54e-334">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="de54e-335">Dans ce scénario, la `WindSpeed` propriété n’est pas sérialisée, même si l' `weatherForecast` objet est en fait un `WeatherForecastDerived` objet.</span><span class="sxs-lookup"><span data-stu-id="de54e-335">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="de54e-336">Seules les propriétés de la classe de base sont sérialisées :</span><span class="sxs-lookup"><span data-stu-id="de54e-336">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="de54e-337">Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.</span><span class="sxs-lookup"><span data-stu-id="de54e-337">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="de54e-338">Pour sérialiser les propriétés du type dérivé dans l’exemple précédent, utilisez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="de54e-338">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="de54e-339">Appelez une surcharge de <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="de54e-339">Call an overload of <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="de54e-340">Déclarez l’objet à sérialiser en tant que `object` .</span><span class="sxs-lookup"><span data-stu-id="de54e-340">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="de54e-341">Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la `WindSpeed` propriété dans la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-341">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="de54e-342">Ces approches fournissent la sérialisation polymorphe uniquement pour l’objet racine à sérialiser, et non pour les propriétés de cet objet racine.</span><span class="sxs-lookup"><span data-stu-id="de54e-342">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="de54e-343">Vous pouvez obtenir la sérialisation polymorphe pour les objets de niveau inférieur si vous les définissez en tant que type `object` .</span><span class="sxs-lookup"><span data-stu-id="de54e-343">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="de54e-344">Par exemple, supposons que votre `WeatherForecast` classe ait une propriété nommée `PreviousForecast` qui peut être définie en tant que type `WeatherForecast` ou `object` :</span><span class="sxs-lookup"><span data-stu-id="de54e-344">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="de54e-345">Si la `PreviousForecast` propriété contient une instance de `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="de54e-345">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="de54e-346">La sortie JSON de la sérialisation `WeatherForecastWithPrevious` **n’inclut pas** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="de54e-346">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="de54e-347">La sortie JSON de la sérialisation `WeatherForecastWithPreviousAsObject` **comprend** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="de54e-347">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="de54e-348">Pour sérialiser `WeatherForecastWithPreviousAsObject` , il n’est pas nécessaire d’appeler `Serialize<object>` ou `GetType` parce que l’objet racine n’est pas celui d’un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="de54e-348">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="de54e-349">L’exemple de code suivant n’appelle pas `Serialize<object>` ou `GetType` :</span><span class="sxs-lookup"><span data-stu-id="de54e-349">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="de54e-350">Le code précédent sérialise correctement `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="de54e-350">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="de54e-351">La même approche de la définition des propriétés `object` fonctionne avec les interfaces.</span><span class="sxs-lookup"><span data-stu-id="de54e-351">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="de54e-352">Supposons que vous disposez de l’interface et de l’implémentation suivantes, et que vous souhaitez sérialiser une classe avec des propriétés qui contiennent des instances d’implémentation :</span><span class="sxs-lookup"><span data-stu-id="de54e-352">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="de54e-353">Lorsque vous sérialisez une instance de `Forecasts` , `Tuesday` affiche uniquement la `WindSpeed` propriété, car `Tuesday` est défini comme `object` suit :</span><span class="sxs-lookup"><span data-stu-id="de54e-353">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="de54e-354">L’exemple suivant montre le code JSON qui résulte du code précédent :</span><span class="sxs-lookup"><span data-stu-id="de54e-354">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="de54e-355">Pour plus d’informations sur **la sérialisation** polymorphe et sur la **désérialisation** , consultez [Comment migrer de :::no-loc(Newtonsoft.Json)::: vers :::no-loc(System.Text.Json):::](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="de54e-355">For more information about polymorphic **serialization** , and for information about **deserialization** , see [How to migrate from :::no-loc(Newtonsoft.Json)::: to :::no-loc(System.Text.Json):::](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="de54e-356">Autoriser les commentaires et les virgules de fin</span><span class="sxs-lookup"><span data-stu-id="de54e-356">Allow comments and trailing commas</span></span>

<span data-ttu-id="de54e-357">Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-357">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="de54e-358">Pour autoriser les commentaires dans le JSON, affectez à la propriété la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="de54e-358">To allow comments in the JSON, set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="de54e-359">Et pour autoriser les virgules de fin, affectez à la propriété la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="de54e-359">And to allow trailing commas, set the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="de54e-360">L’exemple suivant montre comment autoriser les deux :</span><span class="sxs-lookup"><span data-stu-id="de54e-360">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="de54e-361">Voici un exemple de code JSON avec des commentaires et une virgule de fin :</span><span class="sxs-lookup"><span data-stu-id="de54e-361">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="de54e-362">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="de54e-362">Case-insensitive property matching</span></span>

<span data-ttu-id="de54e-363">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="de54e-363">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="de54e-364">Pour modifier ce comportement, affectez à la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="de54e-364">To change that behavior, set <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="de54e-365">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="de54e-365">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="de54e-366">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="de54e-366">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="de54e-367">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="de54e-367">Handle overflow JSON</span></span>

<span data-ttu-id="de54e-368">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="de54e-368">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="de54e-369">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-369">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="de54e-370">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-370">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="de54e-371">Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` `SummaryWords` Propriétés et ne sont pas visibles et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="de54e-371">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="de54e-372">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [[JsonExtensionData]](xref::::no-loc(System.Text.Json):::.Serialization.JsonExtensionDataAttribute) à une propriété de `Dictionary<string,object>` type `Dictionary<string,JsonElement>` ou :</span><span class="sxs-lookup"><span data-stu-id="de54e-372">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref::::no-loc(System.Text.Json):::.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="de54e-373">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la `ExtensionData` propriété :</span><span class="sxs-lookup"><span data-stu-id="de54e-373">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="de54e-374">Property</span><span class="sxs-lookup"><span data-stu-id="de54e-374">Property</span></span> |<span data-ttu-id="de54e-375">Valeur</span><span class="sxs-lookup"><span data-stu-id="de54e-375">Value</span></span>  |<span data-ttu-id="de54e-376">Notes</span><span class="sxs-lookup"><span data-stu-id="de54e-376">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="de54e-377">Date</span><span class="sxs-lookup"><span data-stu-id="de54e-377">Date</span></span>    | <span data-ttu-id="de54e-378">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="de54e-378">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="de54e-379">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="de54e-379">TemperatureCelsius</span></span>| <span data-ttu-id="de54e-380">0</span><span class="sxs-lookup"><span data-stu-id="de54e-380">0</span></span> | <span data-ttu-id="de54e-381">Incompatibilité sensible à la casse ( `temperatureCelsius` dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="de54e-381">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="de54e-382">Résumé</span><span class="sxs-lookup"><span data-stu-id="de54e-382">Summary</span></span> | <span data-ttu-id="de54e-383">Chaud</span><span class="sxs-lookup"><span data-stu-id="de54e-383">Hot</span></span> ||
| <span data-ttu-id="de54e-384">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="de54e-384">ExtensionData</span></span> | <span data-ttu-id="de54e-385">temperatureCelsius : 25</span><span class="sxs-lookup"><span data-stu-id="de54e-385">temperatureCelsius: 25</span></span> |<span data-ttu-id="de54e-386">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="de54e-386">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="de54e-387">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="de54e-387">DatesAvailable:</span></span><br>  <span data-ttu-id="de54e-388">DE 8/1/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="de54e-388">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="de54e-389">DE 8/2/2019 12:00:00 À 07:00</span><span class="sxs-lookup"><span data-stu-id="de54e-389">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="de54e-390">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="de54e-390">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="de54e-391">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="de54e-391">SummaryWords:</span></span><br><span data-ttu-id="de54e-392">Froid</span><span class="sxs-lookup"><span data-stu-id="de54e-392">Cool</span></span><br><span data-ttu-id="de54e-393">Venteux</span><span class="sxs-lookup"><span data-stu-id="de54e-393">Windy</span></span><br><span data-ttu-id="de54e-394">Humide</span><span class="sxs-lookup"><span data-stu-id="de54e-394">Humid</span></span> |<span data-ttu-id="de54e-395">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="de54e-395">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="de54e-396">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="de54e-396">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="de54e-397">Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-397">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="de54e-398">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="de54e-398">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="de54e-399">Conserver les références et gérer les références circulaires</span><span class="sxs-lookup"><span data-stu-id="de54e-399">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="de54e-400">Pour conserver les références et gérer les références circulaires, affectez à la valeur <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.ReferenceHandler%2A> <xref::::no-loc(System.Text.Json):::.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="de54e-400">To preserve references and handle circular references, set <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.ReferenceHandler%2A> to <xref::::no-loc(System.Text.Json):::.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="de54e-401">Ce paramètre entraîne le comportement suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-401">This setting causes the following behavior:</span></span>

* <span data-ttu-id="de54e-402">Lors de la sérialisation :</span><span class="sxs-lookup"><span data-stu-id="de54e-402">On serialize:</span></span>

  <span data-ttu-id="de54e-403">Lors de l’écriture de types complexes, le sérialiseur écrit également des propriétés de métadonnées ( `$id` , `$values` et `$ref` ).</span><span class="sxs-lookup"><span data-stu-id="de54e-403">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="de54e-404">Lors de la désérialisation :</span><span class="sxs-lookup"><span data-stu-id="de54e-404">On deserialize:</span></span>

  <span data-ttu-id="de54e-405">Les métadonnées sont attendues (même si elles ne sont pas obligatoires) et le désérialiseur essaie de le comprendre.</span><span class="sxs-lookup"><span data-stu-id="de54e-405">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="de54e-406">Le code suivant illustre l’utilisation du `Preserve` paramètre.</span><span class="sxs-lookup"><span data-stu-id="de54e-406">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="de54e-407">Cette fonctionnalité ne peut pas être utilisée pour conserver des types valeur ou des types immuables.</span><span class="sxs-lookup"><span data-stu-id="de54e-407">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="de54e-408">Lors de la désérialisation, l’instance d’un type immuable est créée après la lecture de la charge utile entière.</span><span class="sxs-lookup"><span data-stu-id="de54e-408">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="de54e-409">Il serait donc impossible de désérialiser la même instance si une référence à celle-ci apparaît dans la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-409">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="de54e-410">Pour les types valeur, les types immuables et les tableaux, aucune métadonnée de référence n’est sérialisée.</span><span class="sxs-lookup"><span data-stu-id="de54e-410">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="de54e-411">Lors de la désérialisation, une exception est levée si `$ref` ou `$id` est trouvé.</span><span class="sxs-lookup"><span data-stu-id="de54e-411">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="de54e-412">Toutefois, les types valeur ignorent `$id` (et, `$values` dans le cas des collections) qu’il est possible de désérialiser les charges utiles qui ont été sérialisées à l’aide de :::no-loc(Newtonsoft.Json)::: .</span><span class="sxs-lookup"><span data-stu-id="de54e-412">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using :::no-loc(Newtonsoft.Json):::.</span></span>  <span data-ttu-id="de54e-413">:::no-loc(Newtonsoft.Json)::: sérialise les métadonnées de ces types.</span><span class="sxs-lookup"><span data-stu-id="de54e-413">:::no-loc(Newtonsoft.Json)::: does serialize metadata for such types.</span></span>

<span data-ttu-id="de54e-414">Pour déterminer si les objets sont égaux, :::no-loc(System.Text.Json)::: utilise <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , qui utilise l’égalité <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> de référence () au lieu de l’égalité des valeurs (lors de la comparaison de <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> deux instances d’objet.</span><span class="sxs-lookup"><span data-stu-id="de54e-414">To determine if objects are equal, :::no-loc(System.Text.Json)::: uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="de54e-415">Pour plus d’informations sur la façon dont les références sont sérialisées et désérialisées, consultez <xref::::no-loc(System.Text.Json):::.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="de54e-415">For more information about how references are serialized and deserialized, see <xref::::no-loc(System.Text.Json):::.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="de54e-416">La <xref::::no-loc(System.Text.Json):::.Serialization.ReferenceResolver> classe définit le comportement de préservation des références sur la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="de54e-416">The <xref::::no-loc(System.Text.Json):::.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="de54e-417">Créez une classe dérivée pour spécifier un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="de54e-417">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="de54e-418">Pour obtenir un exemple, consultez [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="de54e-418">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-419">:::no-loc(System.Text.Json)::: dans .NET Core 3,1 prend uniquement en charge la sérialisation par valeur et lève une exception pour les références circulaires.</span><span class="sxs-lookup"><span data-stu-id="de54e-419">:::no-loc(System.Text.Json)::: in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="de54e-420">Autoriser ou écrire des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="de54e-420">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="de54e-421">Certains sérialiseurs encodent les nombres sous forme de chaînes JSON (entourées de guillemets).</span><span class="sxs-lookup"><span data-stu-id="de54e-421">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="de54e-422">Par exemple : `{"DegreesCelsius":"23"}` au lieu de `{"DegreesCelsius":23}` .</span><span class="sxs-lookup"><span data-stu-id="de54e-422">For example: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="de54e-423">Pour sérialiser des nombres entre guillemets ou accepter des nombres dans des guillemets dans le graphique d’objet d’entrée entier, définissez <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-423">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

<span data-ttu-id="de54e-424">Lorsque vous utilisez :::no-loc(System.Text.Json)::: indirectement par le biais de ASP.net Core, les nombres entre guillemets sont autorisés lors de la désérialisation, car ASP.net Core spécifie les [options par défaut du Web](xref::::no-loc(System.Text.Json):::.JsonSerializerDefaults.Web).</span><span class="sxs-lookup"><span data-stu-id="de54e-424">When you use :::no-loc(System.Text.Json)::: indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref::::no-loc(System.Text.Json):::.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="de54e-425">Pour autoriser ou écrire des nombres entre guillemets pour des propriétés, des champs ou des types spécifiques, utilisez l’attribut [[JsonNumberHandling]](xref::::no-loc(System.Text.Json):::.Serialization.JsonNumberHandlingAttribute) .</span><span class="sxs-lookup"><span data-stu-id="de54e-425">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref::::no-loc(System.Text.Json):::.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-426">:::no-loc(System.Text.Json)::: dans .NET Core 3,1 ne prend pas en charge la sérialisation ou la désérialisation des nombres placés entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="de54e-426">:::no-loc(System.Text.Json)::: in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="de54e-427">Pour plus d’informations, consultez [autoriser ou écrire des nombres dans des guillemets](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="de54e-427">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="immutable-types-and-records"></a><span data-ttu-id="de54e-428">Enregistrements et types immuables</span><span class="sxs-lookup"><span data-stu-id="de54e-428">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-429">:::no-loc(System.Text.Json)::: peut utiliser un constructeur paramétrable, ce qui rend possible la désérialisation d’une classe ou d’un struct immuable.</span><span class="sxs-lookup"><span data-stu-id="de54e-429">:::no-loc(System.Text.Json)::: can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="de54e-430">Pour une classe, si le seul constructeur est un constructeur paramétrable, ce constructeur sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="de54e-430">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="de54e-431">Pour un struct ou une classe avec plusieurs constructeurs, spécifiez celui-ci à utiliser en appliquant l’attribut [[JsonConstructor]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConstructorAttribute.%23ctor%2A) .</span><span class="sxs-lookup"><span data-stu-id="de54e-431">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="de54e-432">Lorsque l’attribut n’est pas utilisé, un constructeur sans paramètre public est toujours utilisé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="de54e-432">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="de54e-433">L’attribut peut uniquement être utilisé avec des constructeurs publics.</span><span class="sxs-lookup"><span data-stu-id="de54e-433">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="de54e-434">L’exemple suivant utilise l' `[JsonConstructor]` attribut :</span><span class="sxs-lookup"><span data-stu-id="de54e-434">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="de54e-435">Les enregistrements en C# 9 sont également pris en charge, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-435">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="de54e-436">Pour les types immuables, car tous leurs accesseurs set de propriété sont non publics, consultez la section suivante à propos des [accesseurs de propriété non publics](#non-public-property-accessors).</span><span class="sxs-lookup"><span data-stu-id="de54e-436">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-437">`JsonConstructorAttribute` et la prise en charge des enregistrements C# 9 ne sont pas disponibles dans .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-437">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="de54e-438">Accesseurs de propriété non publics</span><span class="sxs-lookup"><span data-stu-id="de54e-438">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-439">Pour activer l’utilisation d’un accesseur de propriété non public, utilisez l’attribut [[JsonInclude]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIncludeAttribute) , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-439">To enable use of a non-public property accessor, use the [[JsonInclude]](xref::::no-loc(System.Text.Json):::.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-440">Les accesseurs de propriété non publics ne sont pas pris en charge dans .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-440">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="de54e-441">Pour plus d’informations, consultez [l' :::no-loc(Newtonsoft.Json)::: article migrer à partir de](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="de54e-441">For more information, see [the Migrate from :::no-loc(Newtonsoft.Json)::: article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="de54e-442">Copier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="de54e-442">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-443">Il existe un [constructeur JsonSerializerOptions] (XREF : :::no-loc(System.Text.Json)::: . JsonSerializerOptions .% 23ctor ( :::no-loc(System.Text.Json)::: . JsonSerializerOptions)) qui vous permet de créer une nouvelle instance avec les mêmes options qu’une instance existante, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-443">There is a [JsonSerializerOptions constructor](xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.%23ctor(:::no-loc(System.Text.Json):::.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-444">Un `JsonSerializerOptions` constructeur qui prend une instance existante n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-444">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="de54e-445">Valeurs par défaut Web pour JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="de54e-445">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="de54e-446">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="de54e-446">Here are the options that have different defaults for web apps:</span></span>

* <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy> = <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy.CamelCase>
* <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.NumberHandling%2A> = <xref::::no-loc(System.Text.Json):::.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="de54e-447">Il y a un [constructeur JsonSerializerOptions] (XREF : :::no-loc(System.Text.Json)::: . JsonSerializerOptions .% 23ctor ( :::no-loc(System.Text.Json)::: . JsonSerializerDefaults) ? View = net-5,0&Preserve-View = true) qui vous permet de créer une nouvelle instance avec les options par défaut que ASP.NET Core utilise pour Web Apps, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-447">There's a [JsonSerializerOptions constructor](xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.%23ctor(:::no-loc(System.Text.Json):::.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-448">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="de54e-448">Here are the options that have different defaults for web apps:</span></span>

* <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy> = <xref::::no-loc(System.Text.Json):::.JsonNamingPolicy.CamelCase>

<span data-ttu-id="de54e-449">Un `JsonSerializerOptions` constructeur qui spécifie un jeu de valeurs par défaut n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-449">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="de54e-450">Méthodes d’extension HttpClient et HttpContent</span><span class="sxs-lookup"><span data-stu-id="de54e-450">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="de54e-451">La sérialisation et la désérialisation des charges utiles JSON à partir du réseau sont des opérations courantes.</span><span class="sxs-lookup"><span data-stu-id="de54e-451">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="de54e-452">Les méthodes d’extension sur [httpclient](xref:System.Net.Http.Json.HttpClientJsonExtensions) et [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) vous permettent d’effectuer ces opérations sur une seule ligne de code.</span><span class="sxs-lookup"><span data-stu-id="de54e-452">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="de54e-453">Ces méthodes d’extension utilisent [des valeurs par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="de54e-453">These extension methods use [web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="de54e-454">L’exemple suivant illustre l’utilisation de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> et <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="de54e-454">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

<span data-ttu-id="de54e-455">Il existe également des méthodes d’extension pour :::no-loc(System.Text.Json)::: sur [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span><span class="sxs-lookup"><span data-stu-id="de54e-455">There are also extension methods for :::no-loc(System.Text.Json)::: on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="de54e-456">Les méthodes d’extension sur `HttpClient` et ne `HttpContent` sont pas disponibles dans :::no-loc(System.Text.Json)::: dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="de54e-456">Extension methods on `HttpClient` and `HttpContent` are not available in :::no-loc(System.Text.Json)::: in .NET Core 3.1.</span></span>
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="de54e-457">Utf8JsonReader, Utf8JsonWriter et JsonDocument</span><span class="sxs-lookup"><span data-stu-id="de54e-457">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="de54e-458"><xref::::no-loc(System.Text.Json):::.Utf8JsonReader?displayProperty=fullName> est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un ou d’un `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="de54e-458"><xref::::no-loc(System.Text.Json):::.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="de54e-459">Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="de54e-459">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="de54e-460">La <xref::::no-loc(System.Text.Json):::.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonReader` couvertures.</span><span class="sxs-lookup"><span data-stu-id="de54e-460">The <xref::::no-loc(System.Text.Json):::.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="de54e-461"><xref::::no-loc(System.Text.Json):::.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants tels que `String` , `Int32` et `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="de54e-461"><xref::::no-loc(System.Text.Json):::.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="de54e-462">Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="de54e-462">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="de54e-463">La <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonWriter` couvertures.</span><span class="sxs-lookup"><span data-stu-id="de54e-463">The <xref::::no-loc(System.Text.Json):::.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="de54e-464"><xref::::no-loc(System.Text.Json):::.JsonDocument?displayProperty=fullName> offre la possibilité de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="de54e-464"><xref::::no-loc(System.Text.Json):::.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="de54e-465">Le DOM fournit un accès aléatoire aux données dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-465">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="de54e-466">Les éléments JSON qui composent la charge utile sont accessibles via le <xref::::no-loc(System.Text.Json):::.JsonElement> type.</span><span class="sxs-lookup"><span data-stu-id="de54e-466">The JSON elements that compose the payload can be accessed via the <xref::::no-loc(System.Text.Json):::.JsonElement> type.</span></span> <span data-ttu-id="de54e-467">Le `JsonElement` type fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .net courants.</span><span class="sxs-lookup"><span data-stu-id="de54e-467">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="de54e-468">`JsonDocument` expose une <xref::::no-loc(System.Text.Json):::.JsonDocument.RootElement> propriété.</span><span class="sxs-lookup"><span data-stu-id="de54e-468">`JsonDocument` exposes a <xref::::no-loc(System.Text.Json):::.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="de54e-469">Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-469">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="de54e-470">Utiliser JsonDocument pour l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="de54e-470">Use JsonDocument for access to data</span></span>

<span data-ttu-id="de54e-471">L’exemple suivant montre comment utiliser la <xref::::no-loc(System.Text.Json):::.JsonDocument> classe pour l’accès aléatoire aux données d’une chaîne JSON :</span><span class="sxs-lookup"><span data-stu-id="de54e-471">The following example shows how to use the <xref::::no-loc(System.Text.Json):::.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="de54e-472">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="de54e-472">The preceding code:</span></span>

* <span data-ttu-id="de54e-473">Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="de54e-473">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="de54e-474">Calcule une qualité moyenne pour les objets d’un `Students` tableau qui ont une `Grade` propriété.</span><span class="sxs-lookup"><span data-stu-id="de54e-474">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="de54e-475">Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.</span><span class="sxs-lookup"><span data-stu-id="de54e-475">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="de54e-476">Compte les élèves en incrémentant une `count` variable à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="de54e-476">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="de54e-477">Une alternative consiste à appeler <xref::::no-loc(System.Text.Json):::.JsonElement.GetArrayLength%2A> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-477">An alternative is to call <xref::::no-loc(System.Text.Json):::.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="de54e-478">Voici un exemple du JSON traité par ce code :</span><span class="sxs-lookup"><span data-stu-id="de54e-478">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="de54e-479">Utiliser JsonDocument pour écrire du code JSON</span><span class="sxs-lookup"><span data-stu-id="de54e-479">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="de54e-480">L’exemple suivant montre comment écrire du code JSON à partir d’un <xref::::no-loc(System.Text.Json):::.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="de54e-480">The following example shows how to write JSON from a <xref::::no-loc(System.Text.Json):::.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="de54e-481">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="de54e-481">The preceding code:</span></span>

* <span data-ttu-id="de54e-482">Lit un fichier JSON, charge les données dans un `JsonDocument` et écrit le format JSON (Pretty-imprimed) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="de54e-482">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="de54e-483">Utilise <xref::::no-loc(System.Text.Json):::.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.</span><span class="sxs-lookup"><span data-stu-id="de54e-483">Uses <xref::::no-loc(System.Text.Json):::.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="de54e-484">Lorsque vous avez terminé, appelle <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter.Flush%2A> sur le writer.</span><span class="sxs-lookup"><span data-stu-id="de54e-484">When finished, calls <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="de54e-485">Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="de54e-485">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="de54e-486">Voici un exemple d’entrée JSON à traiter par l’exemple de code :</span><span class="sxs-lookup"><span data-stu-id="de54e-486">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="de54e-487">Le résultat est la sortie JSON imprimée suivante :</span><span class="sxs-lookup"><span data-stu-id="de54e-487">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="de54e-488">Utiliser Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="de54e-488">Use Utf8JsonWriter</span></span>

<span data-ttu-id="de54e-489">L’exemple suivant montre comment utiliser la <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter> classe :</span><span class="sxs-lookup"><span data-stu-id="de54e-489">The following example shows how to use the <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="de54e-490">Utiliser Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="de54e-490">Use Utf8JsonReader</span></span>

<span data-ttu-id="de54e-491">L’exemple suivant montre comment utiliser la <xref::::no-loc(System.Text.Json):::.Utf8JsonReader> classe :</span><span class="sxs-lookup"><span data-stu-id="de54e-491">The following example shows how to use the <xref::::no-loc(System.Text.Json):::.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="de54e-492">Le code précédent suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="de54e-492">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="de54e-493">Filtrer les données à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="de54e-493">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="de54e-494">L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur :</span><span class="sxs-lookup"><span data-stu-id="de54e-494">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="de54e-495">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="de54e-495">The preceding code:</span></span>

* <span data-ttu-id="de54e-496">Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="de54e-496">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="de54e-497">Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».</span><span class="sxs-lookup"><span data-stu-id="de54e-497">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="de54e-498">Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="de54e-498">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="de54e-499">Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>` , à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="de54e-499">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="de54e-500">Si le fichier contient une marque d’ordre d’octet (BOM) UTF-8, supprimez-le avant de passer les octets au `Utf8JsonReader` , puisque le lecteur attend du texte.</span><span class="sxs-lookup"><span data-stu-id="de54e-500">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="de54e-501">Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="de54e-501">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="de54e-502">Voici un exemple JSON que le code précédent peut lire.</span><span class="sxs-lookup"><span data-stu-id="de54e-502">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="de54e-503">Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :</span><span class="sxs-lookup"><span data-stu-id="de54e-503">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="de54e-504">Lire à partir d’un flux à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="de54e-504">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="de54e-505">Lors de la lecture d’un fichier volumineux (un gigaoctet ou plus en taille, par exemple), vous pouvez éviter d’avoir à charger la totalité du fichier en mémoire en même temps.</span><span class="sxs-lookup"><span data-stu-id="de54e-505">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="de54e-506">Pour ce scénario, vous pouvez utiliser un <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="de54e-506">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="de54e-507">Lorsque vous utilisez le `Utf8JsonReader` pour lire un flux, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="de54e-507">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="de54e-508">La mémoire tampon contenant la charge utile JSON partielle doit être au moins aussi grande que le plus grand jeton JSON au sein de celle-ci afin que le lecteur puisse avancer la progression.</span><span class="sxs-lookup"><span data-stu-id="de54e-508">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="de54e-509">La mémoire tampon doit être au moins aussi grande que la plus grande séquence d’espaces blancs dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-509">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="de54e-510">Le lecteur n’effectue pas le suivi des données qu’il a lues jusqu’à ce qu’il Lise complètement le suivant <xref::::no-loc(System.Text.Json):::.Utf8JsonReader.TokenType%2A> dans la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-510">The reader doesn't keep track of the data it has read until it completely reads the next <xref::::no-loc(System.Text.Json):::.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="de54e-511">Ainsi, lorsqu’il y a des octets restants dans la mémoire tampon, vous devez les transmettre à nouveau au lecteur.</span><span class="sxs-lookup"><span data-stu-id="de54e-511">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="de54e-512">Vous pouvez utiliser <xref::::no-loc(System.Text.Json):::.Utf8JsonReader.BytesConsumed%2A> pour déterminer le nombre d’octets restants.</span><span class="sxs-lookup"><span data-stu-id="de54e-512">You can use <xref::::no-loc(System.Text.Json):::.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="de54e-513">Le code suivant illustre comment lire à partir d’un flux.</span><span class="sxs-lookup"><span data-stu-id="de54e-513">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="de54e-514">L’exemple montre un <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="de54e-514">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="de54e-515">Un code similaire fonctionne avec un <xref:System.IO.FileStream> , sauf lorsque `FileStream` contient une nomenclature UTF-8 au début.</span><span class="sxs-lookup"><span data-stu-id="de54e-515">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="de54e-516">Dans ce cas, vous devez supprimer ces trois octets de la mémoire tampon avant de passer les octets restants à `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="de54e-516">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="de54e-517">Dans le cas contraire, le lecteur lèvera une exception, puisque la nomenclature n’est pas considérée comme une partie valide du JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-517">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="de54e-518">L’exemple de code commence par une mémoire tampon de 4 Ko et double la taille de la mémoire tampon chaque fois qu’il détecte que la taille n’est pas assez grande pour contenir un jeton JSON complet, ce qui est nécessaire pour que le lecteur fasse progresser la progression sur la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="de54e-518">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="de54e-519">L’exemple JSON fourni dans l’extrait de code déclenche une augmentation de la taille de la mémoire tampon uniquement si vous définissez une très petite taille de mémoire tampon initiale, par exemple 10 octets.</span><span class="sxs-lookup"><span data-stu-id="de54e-519">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="de54e-520">Si vous définissez la taille de la mémoire tampon initiale sur 10, les `Console.WriteLine` instructions illustrent la cause et l’effet de la taille de la mémoire tampon augmente.</span><span class="sxs-lookup"><span data-stu-id="de54e-520">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="de54e-521">Au niveau de la taille de la mémoire tampon initiale de 4 Ko, la totalité de l’exemple JSON est affichée par chaque `Console.WriteLine` , et la taille de la mémoire tampon ne doit jamais être augmentée.</span><span class="sxs-lookup"><span data-stu-id="de54e-521">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="de54e-522">L’exemple précédent n’affecte aucune limite à la taille maximale de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="de54e-522">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="de54e-523">Si la taille du jeton est trop grande, le code peut échouer avec une <xref:System.OutOfMemoryException> exception.</span><span class="sxs-lookup"><span data-stu-id="de54e-523">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="de54e-524">Cela peut se produire si le JSON contient un jeton d’une taille d’environ 1 Go, car le doublement de la taille de 1 Go donne une taille trop importante pour tenir dans une `int32` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="de54e-524">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="de54e-525">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="de54e-525">Additional resources</span></span>

* [<span data-ttu-id="de54e-526">:::no-loc(System.Text.Json)::: vue</span><span class="sxs-lookup"><span data-stu-id="de54e-526">:::no-loc(System.Text.Json)::: overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="de54e-527">Guide pratique pour écrire des convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="de54e-527">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="de54e-528">Migration à partir de :::no-loc(Newtonsoft.Json):::</span><span class="sxs-lookup"><span data-stu-id="de54e-528">How to migrate from :::no-loc(Newtonsoft.Json):::</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="de54e-529">Prise en charge des valeurs DateTime et DateTimeOffset dans :::no-loc(System.Text.Json):::</span><span class="sxs-lookup"><span data-stu-id="de54e-529">DateTime and DateTimeOffset support in :::no-loc(System.Text.Json):::</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="de54e-530">[:::no-loc(System.Text.Json)::: Référence d’API](xref::::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="de54e-530">[:::no-loc(System.Text.Json)::: API reference](xref::::no-loc(System.Text.Json):::)</span></span>
<!-- * [:::no-loc(System.Text.Json)::: roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/roadmap/README.md)-->
