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
# <a name="how-to-serialize-json-in-net"></a>Comment sérialiser JSON dans .NET

> [!IMPORTANT]
> La documentation de sérialisation JSON est en cours de construction. Cet article ne traite pas de tous les scénarios. Pour plus d’informations, examinez les [problèmes liés à System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) dans le référentiel dotnet/Corefx sur GitHub, en particulier ceux étiquetés [JSON-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

Cet article explique comment utiliser l' <xref:System.Text.Json> espace de noms pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON). Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).

## <a name="namespaces"></a>Espaces de noms

L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types. L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation. Par conséquent, les exemples de code présentés dans cet article requièrent l’une des `using` directives suivantes, ou les deux :

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Les attributs de <xref:System.Runtime.Serialization> l’espace de noms ne `System.Text.Json`sont actuellement pas pris en charge dans.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Comment écrire des objets .NET dans JSON (sérialiser)

Pour écrire du code JSON dans une chaîne, <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> appelez la méthode. L’exemple suivant utilise une surcharge avec un paramètre de type générique :

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

Vous pouvez omettre le paramètre de type générique et utiliser l’inférence de type générique à la place :

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

Voici un exemple de type à sérialiser, qui contient des collections et des classes imbriquées :

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

La sortie JSON est minimisés par défaut : 

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

Les surcharges <xref:System.Text.Json.JsonSerializer.Serialize%2A> de vous permettent de sérialiser <xref:System.IO.Stream>vers un. Les `Stream` versions Async des surcharges sont disponibles.

### <a name="serialize-to-utf-8"></a>Sérialiser vers UTF-8

Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

En guise d’alternative <xref:System.Text.Json.JsonSerializer.Serialize%2A> , une surcharge qui <xref:System.Text.Json.Utf8JsonWriter> prend un est disponible.

La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne. La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).

## <a name="serialization-behavior"></a>Comportements de sérialisation

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier les propriétés à exclure](#exclude-properties).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères HTML dans la plage ASCII et les caractères qui doivent être placés dans une séquence d’échappement conformément à [la spécification JSON](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names).
* Les références circulaires sont détectées et les exceptions levées. Pour plus d’informations, consultez le [problème sur les références circulaires](https://github.com/dotnet/corefx/issues/38579) dans le référentiel dotnet/Corefx sur GitHub.
* Actuellement, les champs sont exclus.

Les types pris en charge sont les suivants :

* Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.
* [Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).
* Tableaux unidimensionnels et en escalier (`ArrayName[][]`).
* `Dictionary<string,TValue>`où `TValue` est `object` ,`JsonElement`ou un poco.
* Collections des espaces de noms suivants. Pour plus d’informations, consultez le [problème sur la prise en charge de collection](https://github.com/dotnet/corefx/issues/36643) dans le référentiel dotnet/Corefx sur GitHub.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Comment lire JSON dans des objets .NET (désérialisation)

Pour désérialiser à partir d’une chaîne, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> appelez la méthode, comme indiqué dans l’exemple suivant :

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Pour obtenir un exemple, consultez la section [Serialize](#how-to-write-net-objects-to-json-serialize) . Les objets JSON et .NET sont identiques, mais le sens est inversé.

Les surcharges <xref:System.Text.Json.JsonSerializer.Deserialize*> de vous permettent de désérialiser `Stream`à partir d’un.  Les `Stream` versions Async des surcharges sont disponibles.

### <a name="deserialize-from-utf-8"></a>Désérialiser à partir d’UTF-8

Pour désérialiser à partir d’UTF-8, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> appelez une surcharge qui `Utf8JsonReader` accepte un `ReadOnlySpan<byte>`ou un, comme indiqué dans les exemples suivants :

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

## <a name="deserialization-behavior"></a>Comportement de la désérialisation

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.
* La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge. Pour plus d’informations, consultez le [problème GitHub sur la prise en charge des objets immuables](https://github.com/dotnet/corefx/issues/38569) et le [problème sur la prise en charge des propriétés en lecture seule](https://github.com/dotnet/corefx/issues/38163) dans le référentiel dotnet/corefx sur GitHub.
* Par défaut, les enums sont pris en charge en tant que nombres.
* Les champs ne sont pas pris en charge.
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas) si nécessaire.
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

## <a name="serialize-to-formatted-json"></a>Sérialiser au format JSON

Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur : `true`

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple de type à sérialiser et une sortie JSON :

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

## <a name="allow-comments-and-trailing-commas"></a>Autoriser les commentaires et les virgules de fin

Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON. Pour autoriser les commentaires dans le JSON, affectez <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> à `JsonCommentHandling.Skip`la propriété la valeur. Et pour autoriser les virgules de fin, affectez <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> à `true`la propriété la valeur. L’exemple suivant montre comment autoriser les deux :

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

## <a name="customize-json-names"></a>Personnaliser les noms JSON

Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse. Cette section explique comment effectuer les opérations suivantes :

* Personnaliser les noms de propriété individuels
* Convertir tous les noms de propriété en casse mixte
* Implémenter une stratégie d’attribution de noms de propriété personnalisée
* Convertir les clés du dictionnaire en casse mixte

Actuellement, il n’existe pas de prise en charge pour la conversion automatique des enum en casse mixte. Pour plus d’informations, consultez le [problème sur la prise en charge de la casse mixte enum](https://github.com/dotnet/corefx/issues/37725) dans le référentiel dotnet/Corefx sur GitHub.

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

Pour utiliser la casse mixte pour tous les noms de propriétés <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> JSON `JsonNamingPolicy.CamelCase`, affectez la valeur à, comme indiqué dans l’exemple suivant :

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

La stratégie de nommage de propriété casse mixte :

* S’applique à la sérialisation et à la désérialisation.
* Est substitué par des `[JsonPropertyName]` attributs.

### <a name="use-a-custom-json-property-naming-policy"></a>Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée

Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe <xref:System.Text.Json.JsonNamingPolicy> qui dérive de <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> et substituez la méthode, comme illustré dans l’exemple suivant :

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Définissez ensuite la <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :

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
* Est substitué par des `[JsonPropertyName]` attributs.

### <a name="camel-case-dictionary-keys"></a>Clés de dictionnaire de casse mixte

Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>`, les `string` clés peuvent être converties en casse mixte. Pour ce faire, affectez `JsonNamingPolicy.CamelCase`à la valeur <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> , comme illustré dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple d’objet pour sérialiser et la sortie JSON :

|Propriété |Valeur  |
|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00|
| TemperatureC| 25 |
| Récapitulatif| Images|
| TemperatureRanges | Froid, 20<br>Chaud, 40|

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

La stratégie d’attribution de noms de casse mixte s’applique uniquement à la sérialisation.

## <a name="exclude-properties"></a>Exclure des propriétés

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

Pour exclure toutes les propriétés en lecture seule, affectez `true`la <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> valeur à, comme illustré dans l’exemple suivant :

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

Cette option s’applique uniquement à la sérialisation. Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut. Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.

### <a name="exclude-all-null-value-properties"></a>Exclure toutes les propriétés de valeur null

Pour exclure toutes les propriétés de valeur null, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> affectez `true`à la propriété la valeur, comme illustré dans l’exemple suivant :

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Voici un exemple d’objet pour sérialiser et la sortie JSON :

|Propriété |Valeur  |
|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00|
| TemperatureC| 25 |
| Récapitulatif| Null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Ce paramètre s’applique à la sérialisation et à la désérialisation. Pendant la désérialisation, les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides. Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions. Pour plus d’informations, consultez le [problème sur les types valeur non Nullable](https://github.com/dotnet/corefx/issues/40922) dans le référentiel dotnet/Corefx sur GitHub.

## <a name="case-insensitive-property-matching"></a>Correspondance de propriété ne respectant pas la casse

Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible. Pour modifier ce comportement, affectez <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> à `true`la valeur :

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

## <a name="include-properties-of-derived-classes"></a>Inclure les propriétés des classes dérivées

La sérialisation polymorphe n’est pas prise en charge lorsque vous spécifiez au moment de la compilation le type à sérialiser. Par exemple, supposons que vous `WeatherForecast` avez une classe et une `WeatherForecastWithWind`classe dérivée :

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

Et supposons que le type passé à la méthode au `Serialize` `WeatherForecast`moment de la compilation, ou inféré par celle-ci :

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

Dans ce scénario, la `WindSpeed` propriété n’est pas sérialisée, même `weatherForecast` si l’objet est `WeatherForecastWithWind` en fait un objet. Seules les propriétés de la classe de base sont sérialisées :

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

* Déclarez l’objet à sérialiser en `object`tant que.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

Dans l’exemple de scénario précédent, les deux approches `WindSpeed` entraînent l’inclusion de la propriété dans la sortie JSON :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
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

Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` propriétés `SummaryWords` et ne sont pas visibles et sont perdues. Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de `Dictionary<string,object>` type `Dictionary<string,JsonElement>`ou :

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

Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé- `ExtensionData` valeur de la propriété :

|Propriété |Valeur  |Notes  |
|---------|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00||
| TemperatureC| 0 | Incompatibilité sensible à la`temperatureC` casse (dans le JSON), la propriété n’est donc pas définie. |
| Récapitulatif | Images ||
| ExtensionData | temperatureC: 25 |Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.|
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

Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON. Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.

## <a name="use-utf8jsonwriter-directly"></a>Utiliser Utf8JsonWriter directement

L’exemple suivant montre comment utiliser directement la <xref:System.Text.Json.Utf8JsonWriter> classe.

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

## <a name="use-utf8jsonreader-directly"></a>Utiliser Utf8JsonReader directement

L’exemple suivant montre comment utiliser directement la <xref:System.Text.Json.Utf8JsonReader> classe. Le code suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.

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

## <a name="additional-resources"></a>Ressources supplémentaires

* [Vue d’ensemble de System. Text. JSON](system-text-json-overview.md)
* [Informations de référence sur l’API System. Text. JSON](xref:System.Text.Json)
* [Prise en charge des valeurs DateTime et DateTimeOffset dans System. Text. JSON](../datetime/system-text-json-support.md)
