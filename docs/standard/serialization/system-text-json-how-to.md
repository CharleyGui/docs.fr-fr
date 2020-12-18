---
title: Comment sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Découvrez comment utiliser l' System.Text.Json espace de noms pour sérialiser et désérialiser à partir de JSON dans .net. Comprend un exemple de code.
ms.date: 12/16/2020
ms.custom: contperf-fy21q2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: b69dfd6238f529c3b315d63a93a82da0f316f459
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678258"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="ab686-104">Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="ab686-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="ab686-105">Cet article explique comment utiliser l' <xref:System.Text.Json?displayProperty=fullName> espace de noms pour sérialiser et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="ab686-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="ab686-106">Si vous transférez du code existant à partir de `Newtonsoft.Json` , consultez [Comment migrer vers `System.Text.Json` ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="ab686-107">Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="ab686-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="ab686-108">La majeure partie de l’exemple de code de sérialisation affecte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` la valeur « joli Printing » au format JSON (avec mise en retrait et espace blanc pour la lisibilité humaine).</span><span class="sxs-lookup"><span data-stu-id="ab686-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="ab686-109">Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="ab686-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="ab686-110">Les exemples de code font référence à la classe et aux variantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab686-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a><span data-ttu-id="ab686-111">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="ab686-111">Namespaces</span></span>

<span data-ttu-id="ab686-112">L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types.</span><span class="sxs-lookup"><span data-stu-id="ab686-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="ab686-113">L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="ab686-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="ab686-114">Les exemples de code présentés dans cet article requièrent des `using` directives pour l’un de ces espaces de noms ou les deux :</span><span class="sxs-lookup"><span data-stu-id="ab686-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="ab686-115">Les attributs de l' <xref:System.Runtime.Serialization> espace de noms ne sont pas pris en charge dans `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="ab686-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="ab686-116">Comment écrire des objets .NET au format JSON (sérialiser)</span><span class="sxs-lookup"><span data-stu-id="ab686-116">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="ab686-117">Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="ab686-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab686-118">L’exemple suivant crée JSON sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="ab686-118">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="ab686-119">L’exemple suivant utilise du code synchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="ab686-119">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="ab686-120">L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :</span><span class="sxs-lookup"><span data-stu-id="ab686-120">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="ab686-121">Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="ab686-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="ab686-122">Une surcharge de `Serialize()` prend un paramètre de type générique :</span><span class="sxs-lookup"><span data-stu-id="ab686-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="ab686-123">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="ab686-123">Serialization example</span></span>

<span data-ttu-id="ab686-124">Voici un exemple de classe qui contient des propriétés de type collection et un type défini par l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="ab686-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="ab686-125">« POCO » signifie « [Plain Old CLR Object](https://en.wikipedia.org/wiki/Plain_old_CLR_object)».</span><span class="sxs-lookup"><span data-stu-id="ab686-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="ab686-126">Un POCO est un type .NET qui ne dépend d’aucun type spécifique à l’infrastructure, par exemple par le biais de l’héritage ou des attributs.</span><span class="sxs-lookup"><span data-stu-id="ab686-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="ab686-127">La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ab686-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="ab686-128">La sortie JSON est minimisés (les espaces blancs, les mises en retrait et les caractères de nouvelle ligne sont supprimés) par défaut :</span><span class="sxs-lookup"><span data-stu-id="ab686-128">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="ab686-129">L’exemple suivant montre le même JSON, mais formaté (autrement dit, avec un espace blanc et une mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="ab686-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

## <a name="serialize-to-utf-8"></a><span data-ttu-id="ab686-130">Sérialiser vers UTF-8</span><span class="sxs-lookup"><span data-stu-id="ab686-130">Serialize to UTF-8</span></span>

<span data-ttu-id="ab686-131">Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :</span><span class="sxs-lookup"><span data-stu-id="ab686-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="ab686-132">Une <xref:System.Text.Json.JsonSerializer.Serialize%2A> surcharge qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.</span><span class="sxs-lookup"><span data-stu-id="ab686-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="ab686-133">La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ab686-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="ab686-134">La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="ab686-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="ab686-135">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="ab686-135">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="ab686-136">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="ab686-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="ab686-137">Vous pouvez [spécifier des propriétés à ignorer](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-137">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="ab686-138">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="ab686-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="ab686-139">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="ab686-139">By default, JSON is minified.</span></span> <span data-ttu-id="ab686-140">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="ab686-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="ab686-141">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="ab686-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="ab686-142">Vous pouvez [personnaliser la casse du nom JSON](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-142">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="ab686-143">Par défaut, les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="ab686-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="ab686-144">Vous pouvez [conserver les références et gérer les références circulaires](system-text-json-preserve-references.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-144">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="ab686-145">Par défaut, les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ab686-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="ab686-146">Vous pouvez [inclure des champs](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="ab686-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="ab686-147">Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="ab686-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="ab686-148">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="ab686-148">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="ab686-149">Par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="ab686-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="ab686-150">Vous pouvez [spécifier des propriétés à ignorer](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-150">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="ab686-151">L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="ab686-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="ab686-152">Par défaut, JSON est minimisés.</span><span class="sxs-lookup"><span data-stu-id="ab686-152">By default, JSON is minified.</span></span> <span data-ttu-id="ab686-153">Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="ab686-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="ab686-154">Par défaut, la casse des noms JSON correspond aux noms .NET.</span><span class="sxs-lookup"><span data-stu-id="ab686-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="ab686-155">Vous pouvez [personnaliser la casse du nom JSON](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-155">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="ab686-156">Les références circulaires sont détectées et les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="ab686-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="ab686-157">Les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ab686-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="ab686-158">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="ab686-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="ab686-159">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="ab686-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="ab686-160">[Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="ab686-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="ab686-161">Tableaux unidimensionnels et en escalier ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="ab686-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="ab686-162">Collections et dictionnaires à partir des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="ab686-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="ab686-163">Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="ab686-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="ab686-164">[Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).</span><span class="sxs-lookup"><span data-stu-id="ab686-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="ab686-165">Tableaux unidimensionnels et en escalier ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="ab686-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="ab686-166">`Dictionary<string,TValue>` où `TValue` est `object` , `JsonElement` ou un poco.</span><span class="sxs-lookup"><span data-stu-id="ab686-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="ab686-167">Collections des espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="ab686-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="ab686-168">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="ab686-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="ab686-169">Comment lire JSON en tant qu’objets .NET (désérialisation)</span><span class="sxs-lookup"><span data-stu-id="ab686-169">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="ab686-170">Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="ab686-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab686-171">L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la `WeatherForecastWithPOCOs` classe indiquée précédemment pour l' [exemple de sérialisation](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="ab686-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="ab686-172">Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ab686-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="ab686-173">Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> méthode :</span><span class="sxs-lookup"><span data-stu-id="ab686-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

> [!TIP]
> <span data-ttu-id="ab686-174">Si vous souhaitez désérialiser JSON et que vous n’avez pas la classe dans laquelle la désérialiser, Visual Studio 2019 peut générer automatiquement la classe dont vous avez besoin :</span><span class="sxs-lookup"><span data-stu-id="ab686-174">If you have JSON that you want to deserialize, and you don't have the class to deserialize it into, Visual Studio 2019 can automatically generate the class you need:</span></span>
>
> 1. <span data-ttu-id="ab686-175">Copiez le JSON que vous devez désérialiser.</span><span class="sxs-lookup"><span data-stu-id="ab686-175">Copy the JSON that you need to deserialize.</span></span>
> 1. <span data-ttu-id="ab686-176">Créez un fichier de classe et supprimez le code du modèle.</span><span class="sxs-lookup"><span data-stu-id="ab686-176">Create a class file and delete the template code.</span></span>
> 1. <span data-ttu-id="ab686-177">Choisissez **Edition**  >  **coller spécial**  >  **coller JSON comme classes**.</span><span class="sxs-lookup"><span data-stu-id="ab686-177">Choose **Edit** > **Paste Special** > **Paste JSON as Classes**.</span></span>
>
> <span data-ttu-id="ab686-178">Le résultat est une classe que vous pouvez utiliser pour votre cible de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="ab686-178">The result is a class that you can use for your deserialization target.</span></span>

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="ab686-179">Désérialiser à partir d’UTF-8</span><span class="sxs-lookup"><span data-stu-id="ab686-179">Deserialize from UTF-8</span></span>

<span data-ttu-id="ab686-180">Pour désérialiser à partir d’UTF-8, appelez une <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> surcharge qui accepte un `ReadOnlySpan<byte>` ou un `Utf8JsonReader` , comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="ab686-180">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="ab686-181">Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="ab686-181">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="ab686-182">Comportement de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="ab686-182">Deserialization behavior</span></span>

<span data-ttu-id="ab686-183">Les comportements suivants s’appliquent lors de la désérialisation de JSON :</span><span class="sxs-lookup"><span data-stu-id="ab686-183">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="ab686-184">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="ab686-184">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="ab686-185">Vous pouvez [spécifier le non-respect de la casse](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-185">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="ab686-186">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="ab686-186">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="ab686-187">Les constructeurs non publics sont ignorés par le sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="ab686-187">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="ab686-188">La désérialisation des objets immuables ou des propriétés en lecture seule est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ab686-188">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="ab686-189">Consultez [les types immuables et les enregistrements](system-text-json-immutability.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-189">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="ab686-190">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="ab686-190">By default, enums are supported as numbers.</span></span> <span data-ttu-id="ab686-191">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](system-text-json-customize-properties.md#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="ab686-191">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="ab686-192">Par défaut, les champs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ab686-192">By default, fields are ignored.</span></span> <span data-ttu-id="ab686-193">Vous pouvez [inclure des champs](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="ab686-193">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="ab686-194">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="ab686-194">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="ab686-195">Vous pouvez [autoriser les commentaires et les virgules de fin](system-text-json-invalid-json.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-195">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="ab686-196">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="ab686-196">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="ab686-197">Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="ab686-197">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="ab686-198">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="ab686-198">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="ab686-199">Par défaut, la correspondance de nom de propriété respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="ab686-199">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="ab686-200">Vous pouvez [spécifier le non-respect de la casse](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-200">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="ab686-201">Par défaut, les applications ASP.NET Core [spécifient le non-respect](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)de la casse.</span><span class="sxs-lookup"><span data-stu-id="ab686-201">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="ab686-202">Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="ab686-202">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="ab686-203">Un constructeur sans paramètre, qui peut être public, Internal ou Private, est utilisé pour la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="ab686-203">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="ab686-204">La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ab686-204">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="ab686-205">Par défaut, les enums sont pris en charge en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="ab686-205">By default, enums are supported as numbers.</span></span> <span data-ttu-id="ab686-206">Vous pouvez [sérialiser les noms d’enum en tant que chaînes](system-text-json-customize-properties.md#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="ab686-206">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="ab686-207">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ab686-207">Fields aren't supported.</span></span>
* <span data-ttu-id="ab686-208">Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions.</span><span class="sxs-lookup"><span data-stu-id="ab686-208">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="ab686-209">Vous pouvez [autoriser les commentaires et les virgules de fin](system-text-json-invalid-json.md).</span><span class="sxs-lookup"><span data-stu-id="ab686-209">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="ab686-210">La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.</span><span class="sxs-lookup"><span data-stu-id="ab686-210">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="ab686-211">Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents.</span><span class="sxs-lookup"><span data-stu-id="ab686-211">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="ab686-212">Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="ab686-212">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="ab686-213">Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="ab686-213">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="ab686-214">Sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="ab686-214">Serialize to formatted JSON</span></span>

<span data-ttu-id="ab686-215">Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true` :</span><span class="sxs-lookup"><span data-stu-id="ab686-215">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="ab686-216">Voici un exemple de type à sérialiser et à imprimer une sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="ab686-216">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="ab686-217">Si vous utilisez `JsonSerializerOptions` à plusieurs reprises avec les mêmes options, ne créez pas une nouvelle `JsonSerializerOptions` instance à chaque fois que vous l’utilisez.</span><span class="sxs-lookup"><span data-stu-id="ab686-217">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="ab686-218">Réutilisez la même instance pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="ab686-218">Reuse the same instance for every call.</span></span> <span data-ttu-id="ab686-219">Pour plus d’informations, consultez [réutiliser des instances JsonSerializerOptions](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="ab686-219">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="ab686-220">Inclure les champs</span><span class="sxs-lookup"><span data-stu-id="ab686-220">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="ab686-221">Utilisez le <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> paramètre global ou l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) pour inclure les champs lors de la sérialisation ou de la désérialisation, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ab686-221">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="ab686-222">Pour ignorer les champs en lecture seule, utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.</span><span class="sxs-lookup"><span data-stu-id="ab686-222">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="ab686-223">Les champs ne sont pas pris en charge dans System.Text.Json dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ab686-223">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="ab686-224">Les [convertisseurs personnalisés](system-text-json-converters-how-to.md) peuvent fournir cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="ab686-224">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="ab686-225">Méthodes d’extension HttpClient et HttpContent</span><span class="sxs-lookup"><span data-stu-id="ab686-225">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="ab686-226">La sérialisation et la désérialisation des charges utiles JSON à partir du réseau sont des opérations courantes.</span><span class="sxs-lookup"><span data-stu-id="ab686-226">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="ab686-227">Les méthodes d’extension sur [httpclient](xref:System.Net.Http.Json.HttpClientJsonExtensions) et [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) vous permettent d’effectuer ces opérations sur une seule ligne de code.</span><span class="sxs-lookup"><span data-stu-id="ab686-227">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="ab686-228">Ces méthodes d’extension utilisent [des valeurs par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="ab686-228">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="ab686-229">L’exemple suivant illustre l’utilisation de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> et <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="ab686-229">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="ab686-230">Il existe également des méthodes d’extension pour System.Text.Json sur [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span><span class="sxs-lookup"><span data-stu-id="ab686-230">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="ab686-231">Les méthodes d’extension sur `HttpClient` et ne `HttpContent` sont pas disponibles dans System.Text.Json dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ab686-231">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="ab686-232">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab686-232">See also</span></span>

* [<span data-ttu-id="ab686-233">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="ab686-233">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ab686-234">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="ab686-234">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="ab686-235">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="ab686-235">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="ab686-236">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="ab686-236">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="ab686-237">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="ab686-237">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="ab686-238">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="ab686-238">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="ab686-239">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="ab686-239">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="ab686-240">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="ab686-240">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="ab686-241">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="ab686-241">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="ab686-242">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="ab686-242">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="ab686-243">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="ab686-243">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="ab686-244">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="ab686-244">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="ab686-245">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="ab686-245">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="ab686-246">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="ab686-246">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="ab686-247">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ab686-247">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="ab686-248">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="ab686-248">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="ab686-249">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="ab686-249">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
