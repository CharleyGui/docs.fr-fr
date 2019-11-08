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
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740436"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>Comment sérialiser et désérialiser JSON dans .NET

> [!IMPORTANT]
> La documentation de sérialisation JSON est en cours de construction. Cet article ne traite pas de tous les scénarios. Pour plus d’informations, examinez les [problèmes liés à System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) dans le référentiel dotnet/Corefx sur GitHub, en particulier ceux étiquetés [JSON-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

Cet article explique comment utiliser l’espace de noms <xref:System.Text.Json> pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON). Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).

## <a name="namespaces"></a>Espaces de noms

L’espace de noms <xref:System.Text.Json> contient tous les points d’entrée et les principaux types. L’espace de noms <xref:System.Text.Json.Serialization> contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation. Les exemples de code présentés dans cet article requièrent des directives `using` pour l’un de ces espaces de noms ou les deux :

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Les attributs de l’espace de noms <xref:System.Runtime.Serialization> ne sont actuellement pas pris en charge dans `System.Text.Json`.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Comment écrire des objets .NET dans JSON (sérialiser)

Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.

L’exemple suivant crée JSON sous forme de chaîne :

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

L’exemple suivant utilise du code synchrone pour créer un fichier JSON :

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation. Une surcharge de `Serialize()` prend un paramètre de type générique :

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a>Exemple de sérialisation

Voici un exemple de type qui contient des collections et des classes imbriquées :

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

La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant. La sortie JSON est minimisés par défaut : 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

L’exemple suivant montre le même JSON, mis en forme (autrement dit, avec un espace blanc et une mise en retrait) :

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

### <a name="serialize-to-utf-8"></a>Sérialiser vers UTF-8

Pour sérialiser vers UTF-8, appelez la méthode <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> :

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.

La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne. La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).

## <a name="serialization-behavior"></a>Comportements de sérialisation

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier les propriétés à exclure](#exclude-properties-from-serialization).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères HTML dans la plage ASCII et les caractères qui doivent être placés dans une séquence d’échappement conformément à [la spécification JSON](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).
* Les références circulaires sont détectées et les exceptions levées. Pour plus d’informations, consultez le [problème sur les références circulaires](https://github.com/dotnet/corefx/issues/38579) dans le référentiel dotnet/Corefx sur GitHub.
* Actuellement, les champs sont exclus.

Les types pris en charge sont les suivants :

* Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.
* [Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).
* Tableaux unidimensionnels et en escalier (`ArrayName[][]`).
* `Dictionary<string,TValue>` où `TValue` est `object`, `JsonElement`ou POCO.
* Collections des espaces de noms suivants. Pour plus d’informations, consultez le [problème sur la prise en charge de collection](https://github.com/dotnet/corefx/issues/36643) dans le référentiel dotnet/Corefx sur GitHub.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Comment lire JSON dans des objets .NET (désérialisation)

Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

L’exemple suivant lit JSON à partir d’une chaîne :

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la méthode <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

Pour obtenir un exemple de type et le JSON correspondant, consultez la section [exemple de sérialisation](#serialization-example) .

### <a name="deserialize-from-utf-8"></a>Désérialiser à partir d’UTF-8

Pour désérialiser à partir d’UTF-8, appelez une surcharge <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> qui prend un `Utf8JsonReader` ou un `ReadOnlySpan<byte>`, comme indiqué dans les exemples suivants. Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>Comportement de la désérialisation

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.
* La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge. Pour plus d’informations, consultez le [problème GitHub sur la prise en charge des objets immuables](https://github.com/dotnet/corefx/issues/38569) et le [problème sur la prise en charge des propriétés en lecture seule](https://github.com/dotnet/corefx/issues/38163) dans le référentiel dotnet/corefx sur GitHub.
* Par défaut, les enums sont pris en charge en tant que nombres. Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).
* Les champs ne sont pas pris en charge.
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="serialize-to-formatted-json"></a>Sérialiser au format JSON

Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true`:

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple de type à sérialiser et à imprimer une sortie JSON :

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

## <a name="customize-json-names-and-values"></a>Personnaliser les noms et les valeurs JSON

Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse. Les valeurs enum sont représentées sous forme de nombres. Cette section explique comment effectuer les opérations suivantes :

* Personnaliser les noms de propriété individuels
* Convertir tous les noms de propriété en casse mixte
* Implémenter une stratégie d’attribution de noms de propriété personnalisée
* Convertir les clés du dictionnaire en casse mixte
* Convertir des enums en chaînes et casse mixte 

Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Personnaliser les noms de propriété individuels

Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Voici un exemple de type pour sérialiser et JSON obtenu :

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

Nom de propriété défini par cet attribut :

* S’applique dans les deux directions, pour la sérialisation et la désérialisation.
* Est prioritaire sur les stratégies d’attribution de noms de propriété.

### <a name="use-camel-case-for-all-json-property-names"></a>Utiliser la casse mixte pour tous les noms de propriété JSON

Pour utiliser la casse mixte pour tous les noms de propriété JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple de classe pour sérialiser et la sortie JSON :

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

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
* Est substitué par `[JsonPropertyName]` attributs. C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.

### <a name="use-a-custom-json-property-naming-policy"></a>Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée

Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la méthode <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, comme indiqué dans l’exemple suivant :

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Définissez ensuite la propriété <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur une instance de votre classe de stratégie d’attribution de noms :

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple de classe pour sérialiser et la sortie JSON :

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

La stratégie d’attribution de noms de propriété JSON :

* S’applique à la sérialisation et à la désérialisation.
* Est substitué par `[JsonPropertyName]` attributs. C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.

### <a name="camel-case-dictionary-keys"></a>Clés de dictionnaire de casse mixte

Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>`, les clés `string` peuvent être converties en casse mixte. Pour ce faire, définissez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` entraînerait une sortie JSON comme dans l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation. Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy`.

### <a name="enums-as-strings"></a>Enums en tant que chaînes

Par défaut, les enums sont sérialisés en tant que nombres. Pour sérialiser les noms d’enum sous forme de chaînes, utilisez l' <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.

Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

Si le résumé est `Hot`, par défaut, le JSON sérialisé a la valeur numérique 3 :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

L’exemple de code suivant sérialise les noms d’énumération à la place et les convertit en casse mixte :

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

Le JSON obtenu ressemble à l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

La prise en charge des enums en tant que chaînes s’applique également à la désérialisation, comme illustré dans l’exemple suivant :

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a>Exclure des propriétés de la sérialisation

Par défaut, toutes les propriétés publiques sont sérialisées. Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options. Cette section explique comment exclure les éléments suivants :

* Propriétés individuelles
* Toutes les propriétés en lecture seule
* Toutes les propriétés de valeur null 

### <a name="exclude-individual-properties"></a>Exclure des propriétés individuelles

Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Voici un exemple de type pour sérialiser et la sortie JSON :

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

### <a name="exclude-all-read-only-properties"></a>Exclure toutes les propriétés en lecture seule

Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public. Pour exclure toutes les propriétés en lecture seule, affectez la valeur `true`à la <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple de type pour sérialiser et la sortie JSON :

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

Cette option s’applique uniquement à la sérialisation. Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.

### <a name="exclude-all-null-value-properties"></a>Exclure toutes les propriétés de valeur null

Pour exclure toutes les propriétés de valeur null, affectez la valeur `true`à la propriété <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues>, comme indiqué dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple d’objet pour sérialiser et la sortie JSON :

|Property |valeur  |
|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00|
| TemperatureC| 25 |
| Récapitulatif| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Ce paramètre s’applique à la sérialisation et à la désérialisation. Pour plus d’informations sur son effet sur la désérialisation, consultez [ignorer la valeur null lors de la désérialisation](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Personnaliser l’encodage de caractères

Par défaut, le sérialiseur échappe tous les caractères non-ASCII.  Autrement dit, il les remplace par `\uxxxx` où `xxxxx` est le code Unicode du caractère.  Par exemple, si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Sérialiser les jeux de caractères de la langue

Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues, spécifiez une ou plusieurs [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, comme indiqué dans l’exemple suivant :

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Ce code sérialise les caractères cyrilliques et grecs. Les caractères cyrilliques sont indiqués dans l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

Pour spécifier toutes les langues, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Sérialiser des caractères spécifiques

Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés. L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple de JSON généré par le code précédent :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Sérialiser tous les caractères

Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, comme illustré dans l’exemple suivant :

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> Contrairement à l’encodeur par défaut, l’encodeur `UnsafeRelaxedJsonEscaping` :
>
> * N’échappe pas les caractères HTML tels que `<`, `>`, `&`et `'`.
> * N’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu*de caractères.
> * Est plus permissif que l’encodeur par défaut sur lequel les caractères sont autorisés à passer sans séquence d’échappement.
>
> Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8. Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8`. N’autorisez jamais l’émission de la sortie `UnsafeRelaxedJsonEscaping` brute dans une page HTML ou un élément `<script>`.

## <a name="serialize-properties-of-derived-classes"></a>Sérialiser les propriétés des classes dérivées

La sérialisation polymorphe n’est pas prise en charge lorsque vous spécifiez au moment de la compilation le type à sérialiser. Par exemple, supposons que vous ayez une classe `WeatherForecast` et une classe dérivée `WeatherForecastWithWind`:

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

Et supposons que l’argument de type de la méthode `Serialize` au moment de la compilation est `WeatherForecast`:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

Dans ce scénario, la propriété `WindSpeed` n’est pas sérialisée, même si l’objet `weatherForecast` est en fait un objet `WeatherForecastWithWind`. Seules les propriétés de la classe de base sont sérialisées :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.

Pour sérialiser les propriétés du type dérivé, utilisez l’une des approches suivantes :

* Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Déclarez l’objet à sérialiser en tant que `object`.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la propriété `WindSpeed` dans la sortie JSON :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Pour plus d’informations sur la désérialisation polymorphe, consultez [prise en charge de la désérialisation polymorphe](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Autoriser les commentaires et les virgules de fin

Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON. Pour autoriser les commentaires dans le JSON, affectez à la propriété <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> la valeur `JsonCommentHandling.Skip`. Et pour autoriser les virgules de fin, définissez la propriété <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> sur `true`. L’exemple suivant montre comment autoriser les deux :

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Voici un exemple de code JSON avec des commentaires et une virgule de fin :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Correspondance de propriété ne respectant pas la casse

Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible. Pour modifier ce comportement, définissez le <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> sur `true`:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

Voici un exemple de JSON avec les noms de propriété de casse mixte. Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.

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

## <a name="handle-overflow-json"></a>Handle de dépassement JSON

Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible. Par exemple, supposons que votre type de cible est le suivant :

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Et le JSON à désérialiser est le suivant :

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

Si vous désérialisez le JSON indiqué dans le type indiqué, les propriétés `DatesAvailable` et `SummaryWords` ne peuvent pas être placées et sont perdues. Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de type `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:

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

Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la propriété `ExtensionData` :

|Property |valeur  |Notes  |
|---------|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00||
| TemperatureC| 0 | Incompatibilité sensible à la casse (`temperatureC` dans le JSON), la propriété n’est donc pas définie. |
| Récapitulatif | Images ||
| ExtensionData | temperatureC : 25 |Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.|
|| DatesAvailable:<br>  DE 8/1/2019 12:00:00 À 07:00<br>DE 8/2/2019 12:00:00 À 07:00 |Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.|
| |SummaryWords:<br>Cool<br>Venteux<br>Humide |Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.|

Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :

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

Notez que le nom de la propriété `ExtensionData` n’apparaît pas dans le JSON. Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.

## <a name="ignore-null-when-deserializing"></a>Ignorer la valeur null lors de la désérialisation

Par défaut, si une propriété dans JSON a la valeur null, la propriété correspondante dans l’objet cible a la valeur null. Dans certains scénarios, la propriété cible peut avoir une valeur par défaut et vous ne souhaitez pas qu’une valeur null remplace la valeur par défaut.

Par exemple, supposons que le code suivant représente votre objet cible :

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Et supposons que le code JSON suivant est désérialisé :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

Après la désérialisation, la propriété `Summary` de l’objet `WeatherForecastWithDefault` a la valeur null.

Pour modifier ce comportement, affectez la valeur `true`à <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

Avec cette option, la propriété `Summary` de l’objet `WeatherForecastWithDefault` est la valeur par défaut « no Summary » après la désérialisation.

Les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides. Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions. Pour plus d’informations, consultez le [problème sur les types valeur non Nullable](https://github.com/dotnet/corefx/issues/40922) dans le référentiel dotnet/Corefx sur GitHub.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter et JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur hautes performances et à faible allocation de type forward-only pour le texte JSON codé au format UTF-8 et lu à partir de `ReadOnlySpan<byte>`. Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés. La méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> utilise `Utf8JsonReader` en coulisses.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants comme `String`, `Int32`et `DateTime`. Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés. La méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> utilise `Utf8JsonWriter` en coulisses.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> permet de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader`. Le DOM fournit un accès aléatoire aux données dans une charge utile JSON. Les éléments JSON qui composent la charge utile sont accessibles via le type de <xref:System.Text.Json.JsonElement>. Le `JsonElement` fournit des énumérateurs de tableaux et d’objets, ainsi que des API pour convertir du texte JSON en types .NET courants. `JsonDocument` expose une propriété <xref:System.Text.Json.JsonDocument.RootElement>.

Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Utiliser JsonDocument pour l’accès aux données

L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.JsonDocument> pour l’accès aléatoire aux données :

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

Le code précédent :

* Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString`.
* Calcule une qualité moyenne pour les objets d’un tableau de `Students` qui ont une propriété `Grade`. 
* Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.
* Compte les étudiants en incrémentant une variable de `count` à chaque itération. Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

Voici un exemple du JSON traité par ce code :

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a>Utiliser JsonDocument pour écrire du code JSON

L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument>:

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

Le code précédent :

* Lit un fichier JSON, charge les données dans un `JsonDocument`et écrit le format JSON (Pretty-imprimed) dans un fichier.
* Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.
* Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer. Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé. 

Voici un exemple d’entrée JSON à traiter par l’exemple de code :

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

Le résultat est la sortie JSON imprimée suivante :

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a>Utiliser Utf8JsonWriter

L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonWriter> :

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

## <a name="use-utf8jsonreader"></a>Utiliser Utf8JsonReader

L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonReader> :

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

Le code précédent suppose que la variable `jsonUtf8` est un tableau d’octets contenant un JSON valide, encodé au format UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrer les données à l’aide de Utf8JsonReader

L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur :

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

Le code précédent :

* Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8. Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>`, à l’aide du code suivant :

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.
* Compte les objets et les valeurs de propriété `name` qui se terminent par « University ».

Voici un exemple JSON que le code précédent peut lire. Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a>Ressources supplémentaires

* [Vue d’ensemble de System. Text. JSON](system-text-json-overview.md)
* [Informations de référence sur l’API System. Text. JSON](xref:System.Text.Json)
* [Écrire des convertisseurs personnalisés pour System. Text. JSON](system-text-json-converters-how-to.md)
* [Prise en charge des valeurs DateTime et DateTimeOffset dans System. Text. JSON](../datetime/system-text-json-support.md)
