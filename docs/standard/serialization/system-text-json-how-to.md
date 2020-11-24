---
title: Comment sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Découvrez comment utiliser l' System.Text.Json espace de noms pour sérialiser et désérialiser à partir de JSON dans .net. Comprend un exemple de code.
ms.date: 11/05/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1e8c46e11d3a82ca0bce29f9cb7bbc749c219198
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676723"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET

Cet article explique comment utiliser l' <xref:System.Text.Json?displayProperty=fullName> espace de noms pour sérialiser et désérialiser à partir de JavaScript Object Notation (JSON). Si vous transférez du code existant à partir de `Newtonsoft.Json` , consultez [Comment migrer vers `System.Text.Json` ](system-text-json-migrate-from-newtonsoft-how-to.md).

Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).

La majeure partie de l’exemple de code de sérialisation affecte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` la valeur « joli Printing » au format JSON (avec mise en retrait et espace blanc pour la lisibilité humaine). Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.

Les exemples de code font référence à la classe et aux variantes suivantes :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>Espaces de noms

L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types. L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation. Les exemples de code présentés dans cet article requièrent des `using` directives pour l’un de ces espaces de noms ou les deux :

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Les attributs de l' <xref:System.Runtime.Serialization> espace de noms ne sont pas pris en charge dans `System.Text.Json` .

## <a name="how-to-write-net-objects-to-json-serialize"></a>Comment écrire des objets .NET dans JSON (sérialiser)

Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode.

L’exemple suivant crée JSON sous forme de chaîne :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

L’exemple suivant utilise du code synchrone pour créer un fichier JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation. Une surcharge de `Serialize()` prend un paramètre de type générique :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Exemple de sérialisation

Voici un exemple de classe qui contient des propriétés de type collection et un type défini par l’utilisateur :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> « POCO » signifie « [Plain Old CLR Object](https://en.wikipedia.org/wiki/Plain_old_CLR_object)». Un POCO est un type .NET qui ne dépend d’aucun type spécifique à l’infrastructure, par exemple par le biais de l’héritage ou des attributs.

La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant. La sortie JSON est minimisés par défaut :

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

L’exemple suivant montre le même JSON, mais formaté (autrement dit, avec un espace blanc et une mise en retrait) :

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

### <a name="serialize-to-utf-8"></a>Sérialiser vers UTF-8

Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

Une <xref:System.Text.Json.JsonSerializer.Serialize%2A> surcharge qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.

La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne. La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).

## <a name="serialization-behavior"></a>Comportements de sérialisation

::: zone pivot="dotnet-5-0"

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier des propriétés à ignorer](#ignore-properties).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).
* Par défaut, les références circulaires sont détectées et les exceptions levées. Vous pouvez [conserver les références et gérer les références circulaires](#preserve-references-and-handle-circular-references).
* Par défaut, les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés. Vous pouvez [inclure des champs](#include-fields).

Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents. Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier des propriétés à ignorer](#ignore-properties).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).
* Les références circulaires sont détectées et les exceptions levées.
* Les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés.
::: zone-end

Les types pris en charge sont les suivants :
::: zone pivot="dotnet-5-0"

* Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.
* [Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).
* Tableaux unidimensionnels et en escalier ( `T[][]` ).
* Collections et dictionnaires à partir des espaces de noms suivants.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.
* [Objets CLR Plain Old](https://en.wikipedia.org/wiki/Plain_old_CLR_object)définis par l’utilisateur (POCO).
* Tableaux unidimensionnels et en escalier ( `ArrayName[][]` ).
* `Dictionary<string,TValue>` où `TValue` est `object` , `JsonElement` ou un poco.
* Collections des espaces de noms suivants.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Comment lire JSON dans des objets .NET (désérialisation)

Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode.

L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la `WeatherForecastWithPOCOs` classe indiquée précédemment pour l' [exemple de sérialisation](#serialization-example):

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> méthode :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Désérialiser à partir d’UTF-8

Pour désérialiser à partir d’UTF-8, appelez une <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> surcharge qui accepte un `Utf8JsonReader` ou un `ReadOnlySpan<byte>` , comme indiqué dans les exemples suivants. Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Comportement de la désérialisation

Les comportements suivants s’appliquent lors de la désérialisation de JSON :

::: zone pivot="dotnet-5-0"

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* Les constructeurs non publics sont ignorés par le sérialiseur.
* La désérialisation des objets immuables ou des propriétés en lecture seule est prise en charge. Consultez [les types immuables et les enregistrements](#immutable-types-and-records).
* Par défaut, les enums sont pris en charge en tant que nombres. Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).
* Par défaut, les champs sont ignorés. Vous pouvez [inclure des champs](#include-fields).
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents. Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching). Par défaut, les applications ASP.NET Core [spécifient le non-respect](#web-defaults-for-jsonserializeroptions)de la casse.
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* Un constructeur sans paramètre, qui peut être public, Internal ou Private, est utilisé pour la désérialisation.
* La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.
* Par défaut, les enums sont pris en charge en tant que nombres. Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).
* Les champs ne sont pas pris en charge.
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents. Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).
::: zone-end

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="serialize-to-formatted-json"></a>Sérialiser au format JSON

Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Voici un exemple de type à sérialiser et à imprimer une sortie JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a>Inclure les champs

::: zone pivot="dotnet-5-0"
Utilisez le <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> paramètre global ou l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) pour inclure les champs lors de la sérialisation ou de la désérialisation, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

Pour ignorer les champs en lecture seule, utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.
::: zone-end

::: zone pivot="dotnet-core-3-1"
Les champs ne sont pas pris en charge dans System.Text.Json dans .net Core 3,1. Les [convertisseurs personnalisés](system-text-json-converters-how-to.md) peuvent fournir cette fonctionnalité.
::: zone-end

## <a name="customize-json-names-and-values"></a>Personnaliser les noms et les valeurs JSON

Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse. Les valeurs enum sont représentées sous forme de nombres. Cette section explique comment :

* [Personnaliser les noms de propriété individuels](#customize-individual-property-names)
* [Convertir tous les noms de propriété en casse mixte](#use-camel-case-for-all-json-property-names)
* [Implémenter une stratégie d’attribution de noms de propriété personnalisée](#use-a-custom-json-property-naming-policy)
* [Convertir les clés du dictionnaire en casse mixte](#camel-case-dictionary-keys)
* [Convertir des enums en chaînes et casse mixte](#enums-as-strings)

Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Personnaliser les noms de propriété individuels

Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Voici un exemple de type pour sérialiser et JSON obtenu :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

Nom de propriété défini par cet attribut :

* S’applique dans les deux directions, pour la sérialisation et la désérialisation.
* Est prioritaire sur les stratégies d’attribution de noms de propriété.

### <a name="use-camel-case-for-all-json-property-names"></a>Utiliser la casse mixte pour tous les noms de propriété JSON

Pour utiliser la casse mixte pour tous les noms de propriétés JSON, affectez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> la valeur à `JsonNamingPolicy.CamelCase` , comme indiqué dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Voici un exemple de classe pour sérialiser et la sortie JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

La stratégie de nommage de propriété casse mixte :

* S’applique à la sérialisation et à la désérialisation.
* Est substitué par des `[JsonPropertyName]` attributs. C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.

### <a name="use-a-custom-json-property-naming-policy"></a>Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée

Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> méthode, comme illustré dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

Définissez ensuite la <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Voici un exemple de classe pour sérialiser et la sortie JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

La stratégie d’attribution de noms de propriété JSON :

* S’applique à la sérialisation et à la désérialisation.
* Est substitué par des `[JsonPropertyName]` attributs. C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.

### <a name="camel-case-dictionary-keys"></a>Clés de dictionnaire de casse mixte

Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>` , les `string` clés peuvent être converties en casse mixte. Pour ce faire, affectez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> à `JsonNamingPolicy.CamelCase` la valeur, comme illustré dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` provoquerait une sortie JSON similaire à l’exemple suivant :

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

La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation. Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy` .

### <a name="enums-as-strings"></a>Enums en tant que chaînes

Par défaut, les enums sont sérialisés en tant que nombres. Pour sérialiser les noms d’enum sous forme de chaînes, utilisez <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .

Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Si le résumé est `Hot` , par défaut, le JSON sérialisé a la valeur numérique 3 :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Le JSON obtenu ressemble à l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a>Ignorer les propriétés

Par défaut, toutes les propriétés publiques sont sérialisées. Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options. Cette section explique comment ignorer les éléments suivants :

::: zone pivot="dotnet-5-0"

* [Propriétés individuelles](#ignore-individual-properties)
* [Toutes les propriétés en lecture seule](#ignore-all-read-only-properties)
* [Toutes les propriétés de valeur null](#ignore-all-null-value-properties)
* [Toutes les propriétés de valeur par défaut](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Propriétés individuelles](#ignore-individual-properties)
* [Toutes les propriétés en lecture seule](#ignore-all-read-only-properties)
* [Toutes les propriétés de valeur null](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a>Ignorer les propriétés individuelles

Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Voici un exemple de type pour sérialiser et la sortie JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
Vous pouvez spécifier une exclusion conditionnelle en définissant la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` . L' <xref:System.Text.Json.Serialization.JsonIgnoreCondition> énumération fournit les options suivantes :

* `Always` -La propriété est toujours ignorée. Si aucun `Condition` n’est spécifié, cette option est utilisée.
* `Never` -La propriété est toujours sérialisée et désérialisée, quels que soient `DefaultIgnoreCondition` les `IgnoreReadOnlyProperties` `IgnoreReadOnlyFields` paramètres globaux, et.
* `WhenWritingDefault` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` ou d’un type valeur `default` .
* `WhenWritingNull` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` .

L’exemple suivant illustre l’utilisation de la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a>Ignorer toutes les propriétés en lecture seule

Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public. Pour ignorer toutes les propriétés en lecture seule lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> à `true` , comme indiqué dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Voici un exemple de type pour sérialiser et la sortie JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Cette option s’applique uniquement à la sérialisation. Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.

::: zone pivot="dotnet-5-0"
Cette option s’applique uniquement aux propriétés. Pour ignorer les champs en lecture seule lors de la [sérialisation des champs](#include-fields), utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.
::: zone-end

### <a name="ignore-all-null-value-properties"></a>Ignorer toutes les propriétés de valeur null

::: zone pivot="dotnet-5-0"
Pour ignorer toutes les propriétés de valeur null, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> , comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
Pour ignorer toutes les propriétés de valeur null lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> à la propriété `true` , comme indiqué dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Voici un exemple d’objet pour sérialiser et la sortie JSON :

|Propriété |Value  |
|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00|
| TemperatureCelsius| 25 |
| Résumé| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a>Ignorer toutes les propriétés de valeur par défaut

::: zone pivot="dotnet-5-0"
Pour empêcher la sérialisation des valeurs par défaut dans les propriétés de type valeur, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

Le `WhenWritingDefault` paramètre empêche également la sérialisation des propriétés de type de référence de valeur null.

::: zone pivot="dotnet-core-3-1"
Il n’existe aucune méthode intégrée pour empêcher la sérialisation des propriétés avec des valeurs par défaut de type valeur dans System.Text.Json dans .net Core 3,1.
::: zone-end

## <a name="customize-character-encoding"></a>Personnaliser l’encodage de caractères

Par défaut, le sérialiseur échappe tous les caractères non-ASCII.  Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.  Par exemple, si la `Summary` propriété a la valeur cyrillique Жарко, l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Sérialiser les jeux de caractères de la langue

Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , comme illustré dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Ce code n’échappe pas aux caractères cyrilliques ou grecs. Si la `Summary` propriété a la valeur cyrillique Жарко, l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .

### <a name="serialize-specific-characters"></a>Sérialiser des caractères spécifiques

Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés. L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Voici un exemple de JSON généré par le code précédent :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Sérialiser tous les caractères

Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , comme illustré dans l’exemple suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Par rapport à l’encodeur par défaut, l' `UnsafeRelaxedJsonEscaping` encodeur est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :
>
> * Elle n’échappe pas les caractères HTML, tels que `<` ,, `>` `&` et `'` .
> * Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu* de caractères.
>
> Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8. Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8` . N’autorisez jamais l' `UnsafeRelaxedJsonEscaping` émission de la sortie brute dans une page HTML ou un `<script>` élément.

## <a name="serialize-properties-of-derived-classes"></a>Sérialiser les propriétés des classes dérivées

La sérialisation d’une hiérarchie de type polymorphe n’est pas prise en charge. Par exemple, si une propriété est définie comme une interface ou une classe abstraite, seules les propriétés définies sur l’interface ou la classe abstraite sont sérialisées, même si le type de runtime a des propriétés supplémentaires. Les exceptions à ce comportement sont expliquées dans cette section.

Par exemple, supposons que vous avez une `WeatherForecast` classe et une classe dérivée `WeatherForecastDerived` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

Et supposons que l’argument de type de la `Serialize` méthode au moment de la compilation est `WeatherForecast` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Dans ce scénario, la `WindSpeed` propriété n’est pas sérialisée, même si l' `weatherForecast` objet est en fait un `WeatherForecastDerived` objet. Seules les propriétés de la classe de base sont sérialisées :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.

Pour sérialiser les propriétés du type dérivé dans l’exemple précédent, utilisez l’une des approches suivantes :

* Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Déclarez l’objet à sérialiser en tant que `object` .

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la `WindSpeed` propriété dans la sortie JSON :

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> Ces approches fournissent la sérialisation polymorphe uniquement pour l’objet racine à sérialiser, et non pour les propriétés de cet objet racine.

Vous pouvez obtenir la sérialisation polymorphe pour les objets de niveau inférieur si vous les définissez en tant que type `object` . Par exemple, supposons que votre `WeatherForecast` classe ait une propriété nommée `PreviousForecast` qui peut être définie en tant que type `WeatherForecast` ou `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

Si la `PreviousForecast` propriété contient une instance de `WeatherForecastDerived` :

* La sortie JSON de la sérialisation `WeatherForecastWithPrevious` **n’inclut pas** `WindSpeed` .
* La sortie JSON de la sérialisation `WeatherForecastWithPreviousAsObject` **comprend** `WindSpeed` .

Pour sérialiser `WeatherForecastWithPreviousAsObject` , il n’est pas nécessaire d’appeler `Serialize<object>` ou `GetType` parce que l’objet racine n’est pas celui d’un type dérivé. L’exemple de code suivant n’appelle pas `Serialize<object>` ou `GetType` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

Le code précédent sérialise correctement `WeatherForecastWithPreviousAsObject` :

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

La même approche de la définition des propriétés `object` fonctionne avec les interfaces. Supposons que vous disposez de l’interface et de l’implémentation suivantes, et que vous souhaitez sérialiser une classe avec des propriétés qui contiennent des instances d’implémentation :

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

Lorsque vous sérialisez une instance de `Forecasts` , `Tuesday` affiche uniquement la `WindSpeed` propriété, car `Tuesday` est défini comme `object` suit :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

L’exemple suivant montre le code JSON qui résulte du code précédent :

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

Pour plus d’informations sur **la sérialisation** polymorphe et sur la **désérialisation**, consultez [Comment migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Autoriser les commentaires et les virgules de fin

Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON. Pour autoriser les commentaires dans le JSON, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> `JsonCommentHandling.Skip` .
Et pour autoriser les virgules de fin, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> `true` . L’exemple suivant montre comment autoriser les deux :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Voici un exemple de code JSON avec des commentaires et une virgule de fin :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Correspondance de propriété ne respectant pas la casse

Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible. Pour modifier ce comportement, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Voici un exemple de JSON avec les noms de propriété de casse mixte. Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Handle de dépassement JSON

Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible. Par exemple, supposons que votre type de cible est le suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

Et le JSON à désérialiser est le suivant :

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

Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` `SummaryWords` Propriétés et ne sont pas visibles et sont perdues. Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de `Dictionary<string,object>` type `Dictionary<string,JsonElement>` ou :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la `ExtensionData` propriété :

|Propriété |Valeur  |Notes  |
|---------|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00||
| TemperatureCelsius| 0 | Incompatibilité sensible à la casse ( `temperatureCelsius` dans le JSON), la propriété n’est donc pas définie. |
| Résumé | À chaud ||
| ExtensionData | temperatureCelsius : 25 |Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.|
|| DatesAvailable:<br>  DE 8/1/2019 12:00:00 À 07:00<br>DE 8/2/2019 12:00:00 À 07:00 |Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.|
| |SummaryWords:<br>Froid<br>Venteux<br>Humide |Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.|

Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :

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

Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON. Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.

## <a name="preserve-references-and-handle-circular-references"></a>Conserver les références et gérer les références circulaires

::: zone pivot="dotnet-5-0"

Pour conserver les références et gérer les références circulaires, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> . Ce paramètre entraîne le comportement suivant :

* Lors de la sérialisation :

  Lors de l’écriture de types complexes, le sérialiseur écrit également des propriétés de métadonnées ( `$id` , `$values` et `$ref` ).

* Lors de la désérialisation :

  Les métadonnées sont attendues (même si elles ne sont pas obligatoires) et le désérialiseur essaie de le comprendre.

Le code suivant illustre l’utilisation du `Preserve` paramètre.

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

Cette fonctionnalité ne peut pas être utilisée pour conserver des types valeur ou des types immuables. Lors de la désérialisation, l’instance d’un type immuable est créée après la lecture de la charge utile entière. Il serait donc impossible de désérialiser la même instance si une référence à celle-ci apparaît dans la charge utile JSON.

Pour les types valeur, les types immuables et les tableaux, aucune métadonnée de référence n’est sérialisée. Lors de la désérialisation, une exception est levée si `$ref` ou `$id` est trouvé. Toutefois, les types valeur ignorent `$id` (et, `$values` dans le cas des collections) qu’il est possible de désérialiser les charges utiles qui ont été sérialisées à l’aide de Newtonsoft.Json .  Newtonsoft.Json sérialise les métadonnées de ces types.

Pour déterminer si les objets sont égaux, System.Text.Json utilise <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , qui utilise l’égalité <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> de référence () au lieu de l’égalité des valeurs (lors de la comparaison de <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> deux instances d’objet.

Pour plus d’informations sur la façon dont les références sont sérialisées et désérialisées, consultez <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .

La <xref:System.Text.Json.Serialization.ReferenceResolver> classe définit le comportement de préservation des références sur la sérialisation et la désérialisation. Créez une classe dérivée pour spécifier un comportement personnalisé. Pour obtenir un exemple, consultez [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json dans .NET Core 3,1 prend uniquement en charge la sérialisation par valeur et lève une exception pour les références circulaires.
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a>Autoriser ou écrire des nombres entre guillemets

::: zone pivot="dotnet-5-0"

Certains sérialiseurs encodent les nombres sous forme de chaînes JSON (entourées de guillemets). Par exemple : `{"DegreesCelsius":"23"}` au lieu de `{"DegreesCelsius":23}` . Pour sérialiser des nombres entre guillemets ou accepter des nombres dans des guillemets dans le graphique d’objet d’entrée entier, définissez <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

Lorsque vous utilisez System.Text.Json indirectement par le biais de ASP.net Core, les nombres entre guillemets sont autorisés lors de la désérialisation, car ASP.net Core spécifie les [options par défaut du Web](xref:System.Text.Json.JsonSerializerDefaults.Web).

Pour autoriser ou écrire des nombres entre guillemets pour des propriétés, des champs ou des types spécifiques, utilisez l’attribut [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) .
::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json dans .NET Core 3,1 ne prend pas en charge la sérialisation ou la désérialisation des nombres placés entre guillemets. Pour plus d’informations, consultez [autoriser ou écrire des nombres dans des guillemets](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).
::: zone-end

## <a name="immutable-types-and-records"></a>Enregistrements et types immuables

::: zone pivot="dotnet-5-0"
System.Text.Json peut utiliser un constructeur paramétrable, ce qui rend possible la désérialisation d’une classe ou d’un struct immuable. Pour une classe, si le seul constructeur est un constructeur paramétrable, ce constructeur sera utilisé. Pour un struct ou une classe avec plusieurs constructeurs, spécifiez celui-ci à utiliser en appliquant l’attribut [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) . Lorsque l’attribut n’est pas utilisé, un constructeur sans paramètre public est toujours utilisé, le cas échéant. L’attribut peut uniquement être utilisé avec des constructeurs publics. L’exemple suivant utilise l' `[JsonConstructor]` attribut :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

Les enregistrements en C# 9 sont également pris en charge, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

Pour les types immuables, car tous leurs accesseurs set de propriété sont non publics, consultez la section suivante à propos des [accesseurs de propriété non publics](#non-public-property-accessors).
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` et la prise en charge des enregistrements C# 9 ne sont pas disponibles dans .NET Core 3,1.
::: zone-end

## <a name="non-public-property-accessors"></a>Accesseurs de propriété non publics

::: zone pivot="dotnet-5-0"
Pour activer l’utilisation d’un accesseur de propriété non public, utilisez l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Les accesseurs de propriété non publics ne sont pas pris en charge dans .NET Core 3,1. Pour plus d’informations, consultez [l' Newtonsoft.Json article migrer à partir de](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).
::: zone-end

## <a name="copy-jsonserializeroptions"></a>Copier JsonSerializerOptions

::: zone pivot="dotnet-5-0"
Il existe un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) qui vous permet de créer une nouvelle instance avec les mêmes options qu’une instance existante, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Un `JsonSerializerOptions` constructeur qui prend une instance existante n’est pas disponible dans .net Core 3,1.
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>Valeurs par défaut Web pour JsonSerializerOptions

::: zone pivot="dotnet-5-0"
Voici les options qui ont des valeurs par défaut différentes pour les applications Web :

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

Il y a un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults) ? View = net-5,0&Preserve-View = true) qui vous permet de créer une nouvelle instance avec les options par défaut que ASP.NET Core utilise pour Web Apps, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Voici les options qui ont des valeurs par défaut différentes pour les applications Web :

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

Un `JsonSerializerOptions` constructeur qui spécifie un jeu de valeurs par défaut n’est pas disponible dans .net Core 3,1.
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>Méthodes d’extension HttpClient et HttpContent

::: zone pivot="dotnet-5-0"

La sérialisation et la désérialisation des charges utiles JSON à partir du réseau sont des opérations courantes. Les méthodes d’extension sur [httpclient](xref:System.Net.Http.Json.HttpClientJsonExtensions) et [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) vous permettent d’effectuer ces opérations sur une seule ligne de code. Ces méthodes d’extension utilisent [des valeurs par défaut Web pour JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).

L’exemple suivant illustre l’utilisation de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> et <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

Il existe également des méthodes d’extension pour System.Text.Json sur [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).
::: zone-end

::: zone pivot="dotnet-core-3-1"
Les méthodes d’extension sur `HttpClient` et ne `HttpContent` sont pas disponibles dans System.Text.Json dans .net Core 3,1.
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter et JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un ou d’un `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` . Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés. La <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonReader` couvertures.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants tels que `String` , `Int32` et `DateTime` . Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés. La <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonWriter` couvertures.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> offre la possibilité de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader` . Le DOM fournit un accès aléatoire aux données dans une charge utile JSON. Les éléments JSON qui composent la charge utile sont accessibles via le <xref:System.Text.Json.JsonElement> type. Le `JsonElement` type fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .net courants. `JsonDocument` expose une <xref:System.Text.Json.JsonDocument.RootElement> propriété.

Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Utiliser JsonDocument pour l’accès aux données

L’exemple suivant montre comment utiliser la <xref:System.Text.Json.JsonDocument> classe pour l’accès aléatoire aux données d’une chaîne JSON :

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Le code précédent :

* Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString` .
* Calcule une qualité moyenne pour les objets d’un `Students` tableau qui ont une `Grade` propriété.
* Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.
* Compte les élèves en incrémentant une `count` variable à chaque itération. Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , comme illustré dans l’exemple suivant :

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Voici un exemple du JSON traité par ce code :

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Utiliser JsonDocument pour écrire du code JSON

L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Le code précédent :

* Lit un fichier JSON, charge les données dans un `JsonDocument` et écrit le format JSON (Pretty-imprimed) dans un fichier.
* Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.
* Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer. Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé.

Voici un exemple d’entrée JSON à traiter par l’exemple de code :

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

Le résultat est la sortie JSON imprimée suivante :

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utiliser Utf8JsonWriter

L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonWriter> classe :

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utiliser Utf8JsonReader

L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonReader> classe :

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Le code précédent suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrer les données à l’aide de Utf8JsonReader

L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

(Une [version Async de cet exemple](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs) est disponible.)

Le code précédent :

* Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.
* Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».
* Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8. Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>` , à l’aide du code suivant :

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Si le fichier contient une marque d’ordre d’octet (BOM) UTF-8, supprimez-le avant de passer les octets au `Utf8JsonReader` , puisque le lecteur attend du texte. Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.

Voici un exemple JSON que le code précédent peut lire. Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Lire à partir d’un flux à l’aide de Utf8JsonReader

Lors de la lecture d’un fichier volumineux (un gigaoctet ou plus en taille, par exemple), vous pouvez éviter d’avoir à charger la totalité du fichier en mémoire en même temps. Pour ce scénario, vous pouvez utiliser un <xref:System.IO.FileStream> .

Lorsque vous utilisez le `Utf8JsonReader` pour lire un flux, les règles suivantes s’appliquent :

* La mémoire tampon contenant la charge utile JSON partielle doit être au moins aussi grande que le plus grand jeton JSON au sein de celle-ci afin que le lecteur puisse avancer la progression.
* La mémoire tampon doit être au moins aussi grande que la plus grande séquence d’espaces blancs dans le JSON.
* Le lecteur n’effectue pas le suivi des données qu’il a lues jusqu’à ce qu’il Lise complètement le suivant <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> dans la charge utile JSON. Ainsi, lorsqu’il y a des octets restants dans la mémoire tampon, vous devez les transmettre à nouveau au lecteur. Vous pouvez utiliser <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> pour déterminer le nombre d’octets restants.

Le code suivant illustre comment lire à partir d’un flux. L’exemple montre un <xref:System.IO.MemoryStream> . Un code similaire fonctionne avec un <xref:System.IO.FileStream> , sauf lorsque `FileStream` contient une nomenclature UTF-8 au début. Dans ce cas, vous devez supprimer ces trois octets de la mémoire tampon avant de passer les octets restants à `Utf8JsonReader` . Dans le cas contraire, le lecteur lèvera une exception, puisque la nomenclature n’est pas considérée comme une partie valide du JSON.

L’exemple de code commence par une mémoire tampon de 4 Ko et double la taille de la mémoire tampon chaque fois qu’il détecte que la taille n’est pas assez grande pour contenir un jeton JSON complet, ce qui est nécessaire pour que le lecteur fasse progresser la progression sur la charge utile JSON. L’exemple JSON fourni dans l’extrait de code déclenche une augmentation de la taille de la mémoire tampon uniquement si vous définissez une très petite taille de mémoire tampon initiale, par exemple 10 octets. Si vous définissez la taille de la mémoire tampon initiale sur 10, les `Console.WriteLine` instructions illustrent la cause et l’effet de la taille de la mémoire tampon augmente. Au niveau de la taille de la mémoire tampon initiale de 4 Ko, la totalité de l’exemple JSON est affichée par chaque `Console.WriteLine` , et la taille de la mémoire tampon ne doit jamais être augmentée.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

L’exemple précédent n’affecte aucune limite à la taille maximale de la mémoire tampon. Si la taille du jeton est trop grande, le code peut échouer avec une <xref:System.OutOfMemoryException> exception. Cela peut se produire si le JSON contient un jeton d’une taille d’environ 1 Go, car le doublement de la taille de 1 Go donne une taille trop importante pour tenir dans une `int32` mémoire tampon.

## <a name="additional-resources"></a>Ressources supplémentaires

* [System.Text.Json vue](system-text-json-overview.md)
* [Guide pratique pour écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md)
* [Migration à partir de Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Prise en charge des valeurs DateTime et DateTimeOffset dans System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
