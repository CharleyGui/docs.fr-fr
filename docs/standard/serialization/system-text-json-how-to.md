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
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET

Cet article explique comment utiliser l’espace de noms <xref:System.Text.Json> pour sérialiser et désérialiser vers et à partir de JavaScript Object Notation (JSON).

Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).

La majeure partie de l’exemple de code de sérialisation définit <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> de façon à ce qu’il `true` « plutôt imprimer » le JSON (avec mise en retrait et espace blanc pour la lisibilité humaine). Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre.

## <a name="namespaces"></a>Espaces de noms des

L’espace de noms <xref:System.Text.Json> contient tous les points d’entrée et les principaux types. L’espace de noms <xref:System.Text.Json.Serialization> contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation. Les exemples de code présentés dans cet article requièrent des directives `using` pour l’un de ces espaces de noms ou les deux :

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Les attributs de l’espace de noms <xref:System.Runtime.Serialization> ne sont actuellement pas pris en charge dans `System.Text.Json`.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Comment écrire des objets .NET dans JSON (sérialiser)

Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.

L’exemple suivant crée JSON sous forme de chaîne :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

L’exemple suivant utilise du code synchrone pour créer un fichier JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation. Une surcharge de `Serialize()` prend un paramètre de type générique :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Exemple de sérialisation

Voici un exemple de classe qui contient des collections et une classe imbriquée :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant. La sortie JSON est minimisés par défaut : 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

L’exemple suivant montre le même JSON, mis en forme (autrement dit, avec un espace blanc et une mise en retrait) :

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

Pour sérialiser vers UTF-8, appelez la méthode <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

Une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.

La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne. La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).

## <a name="serialization-behavior"></a>Comportements de sérialisation

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier les propriétés à exclure](#exclude-properties-from-serialization).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](#customize-json-names-and-values).
* Les références circulaires sont détectées et les exceptions levées.
* Actuellement, les champs sont exclus.

Les types pris en charge sont les suivants :

* Primitives .NET qui sont mappées à des primitives JavaScript, telles que des types numériques, des chaînes et des valeurs booléennes.
* [Objets CLR Plain Old](https://stackoverflow.com/questions/250001/poco-definition)définis par l’utilisateur (POCO).
* Tableaux unidimensionnels et en escalier (`ArrayName[][]`).
* `Dictionary<string,TValue>` où `TValue` est `object`, `JsonElement`ou POCO.
* Collections des espaces de noms suivants.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour gérer des types supplémentaires ou pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Comment lire JSON dans des objets .NET (désérialisation)

Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la classe `WeatherForecast` présentée précédemment pour l' [exemple de sérialisation](#serialization-example):

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la méthode <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Désérialiser à partir d’UTF-8

Pour désérialiser à partir d’UTF-8, appelez une surcharge <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> qui prend un `Utf8JsonReader` ou un `ReadOnlySpan<byte>`, comme indiqué dans les exemples suivants. Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Comportement de la désérialisation

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](#case-insensitive-property-matching).
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* La désérialisation en types référence sans constructeur sans paramètre n’est pas prise en charge.
* La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.
* Par défaut, les enums sont pris en charge en tant que nombres. Vous pouvez [sérialiser les noms d’enum en tant que chaînes](#enums-as-strings).
* Les champs ne sont pas pris en charge.
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](#allow-comments-and-trailing-commas).
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="serialize-to-formatted-json"></a>Sérialiser au format JSON

Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Voici un exemple de type à sérialiser et à imprimer une sortie JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

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

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

Pour utiliser la casse mixte pour tous les noms de propriété JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Voici un exemple de classe pour sérialiser et la sortie JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Définissez ensuite la propriété <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> sur une instance de votre classe de stratégie d’attribution de noms :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Voici un exemple de classe pour sérialiser et la sortie JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* Est substitué par `[JsonPropertyName]` attributs. C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.

### <a name="camel-case-dictionary-keys"></a>Clés de dictionnaire de casse mixte

Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>`, les clés `string` peuvent être converties en casse mixte. Pour ce faire, définissez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> sur `JsonNamingPolicy.CamelCase`, comme indiqué dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` entraînerait une sortie JSON comme dans l’exemple suivant :

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

La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation. Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy`.

### <a name="enums-as-strings"></a>Enums en tant que chaînes

Par défaut, les enums sont sérialisés en tant que nombres. Pour sérialiser les noms d’enum sous forme de chaînes, utilisez l' <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.

Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Si le résumé est `Hot`, par défaut, le JSON sérialisé a la valeur numérique 3 :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Le JSON obtenu ressemble à l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Exclure des propriétés de la sérialisation

Par défaut, toutes les propriétés publiques sont sérialisées. Si vous ne souhaitez pas que certains d’entre eux s’affichent dans la sortie JSON, vous avez plusieurs options. Cette section explique comment exclure les éléments suivants :

* [Propriétés individuelles](#exclude-individual-properties)
* [Toutes les propriétés en lecture seule](#exclude-all-read-only-properties)
* [Toutes les propriétés de valeur null](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Exclure des propriétés individuelles

Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Voici un exemple de type pour sérialiser et la sortie JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Exclure toutes les propriétés en lecture seule

Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public. Pour exclure toutes les propriétés en lecture seule, affectez la valeur `true`à la <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Voici un exemple de type pour sérialiser et la sortie JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Cette option s’applique uniquement à la sérialisation. Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.

### <a name="exclude-all-null-value-properties"></a>Exclure toutes les propriétés de valeur null

Pour exclure toutes les propriétés de valeur null, affectez la valeur `true`à la propriété <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues>, comme indiqué dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Voici un exemple d’objet pour sérialiser et la sortie JSON :

|Les |Value  |
|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00|
| TemperatureCelsius| 25 |
| Récapitulatif| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

Ce paramètre s’applique à la sérialisation et à la désérialisation. Pour plus d’informations sur son effet sur la désérialisation, consultez [ignorer la valeur null lors de la désérialisation](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Personnaliser l’encodage de caractères

Par défaut, le sérialiseur échappe tous les caractères non-ASCII.  Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.  Par exemple, si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Sérialiser les jeux de caractères de la langue

Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, comme illustré dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Ce code n’échappe pas aux caractères cyrilliques ou grecs. Si la propriété `Summary` est définie sur cyrillique Жарко, l’objet `WeatherForecast` est sérialisé comme indiqué dans cet exemple :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Sérialiser des caractères spécifiques

Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés. L’exemple suivant sérialise uniquement les deux premiers caractères de Жарко :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Voici un exemple de JSON généré par le code précédent :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Sérialiser tous les caractères

Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, comme illustré dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Par rapport à l’encodeur par défaut, l’encodeur `UnsafeRelaxedJsonEscaping` est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :
>
> * Elle n’échappe pas les caractères HTML tels que `<`, `>`, `&`et `'`.
> * Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu*de caractères.
>
> Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8. Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8`. N’autorisez jamais l’émission de la sortie `UnsafeRelaxedJsonEscaping` brute dans une page HTML ou un élément `<script>`.

## <a name="serialize-properties-of-derived-classes"></a>Sérialiser les propriétés des classes dérivées

La sérialisation d’une hiérarchie de type polymorphe n’est pas prise en charge. Par exemple, si une propriété est définie comme une interface ou une classe abstraite, seules les propriétés définies sur l’interface ou la classe abstraite sont sérialisées, même si le type de runtime a des propriétés supplémentaires. Les exceptions à ce comportement sont expliquées dans cette section.

Par exemple, supposons que vous ayez une classe `WeatherForecast` et une classe dérivée `WeatherForecastDerived`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

Et supposons que l’argument de type de la méthode `Serialize` au moment de la compilation est `WeatherForecast`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Dans ce scénario, la propriété `WindSpeed` n’est pas sérialisée, même si l’objet `weatherForecast` est en fait un objet `WeatherForecastDerived`. Seules les propriétés de la classe de base sont sérialisées :

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

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Déclarez l’objet à sérialiser en tant que `object`.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la propriété `WindSpeed` dans la sortie JSON :

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

Vous pouvez obtenir la sérialisation polymorphe pour les objets de niveau inférieur si vous les définissez en tant que type `object`. Par exemple, supposons que votre classe `WeatherForecast` possède une propriété nommée `PreviousForecast` qui peut être définie en tant que type `WeatherForecast` ou `object`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

Si la propriété `PreviousForecast` contient une instance de `WeatherForecastDerived`:

* La sortie JSON de la sérialisation `WeatherForecastWithPrevious` **n’inclut pas** `WindSpeed`.
* La sortie JSON de la sérialisation `WeatherForecastWithPreviousAsObject` **comprend** `WindSpeed`.

Pour sérialiser `WeatherForecastWithPreviousAsObject`, il n’est pas nécessaire d’appeler `Serialize<object>` ou `GetType`, car l’objet racine n’est pas celui d’un type dérivé. L’exemple de code suivant n’appelle pas `Serialize<object>` ou `GetType`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

Le code précédent sérialise correctement `WeatherForecastWithPreviousAsObject`:

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

La même approche de la définition des propriétés en tant que `object` fonctionne avec les interfaces. Supposons que vous disposez de l’interface et de l’implémentation suivantes, et que vous souhaitez sérialiser une classe avec des propriétés qui contiennent des instances d’implémentation :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

Lorsque vous sérialisez une instance de `Forecasts`, seul `Tuesday` affiche la propriété `WindSpeed`, car `Tuesday` est défini en tant que `object`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

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

Pour plus d’informations sur **la sérialisation**polymorphe et sur la **désérialisation**, consultez [How to Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Autoriser les commentaires et les virgules de fin

Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON. Pour autoriser les commentaires dans le JSON, affectez à la propriété <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> la valeur `JsonCommentHandling.Skip`.
Et pour autoriser les virgules de fin, définissez la propriété <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> sur `true`. L’exemple suivant montre comment autoriser les deux :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Voici un exemple de code JSON avec des commentaires et une virgule de fin :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Correspondance de propriété ne respectant pas la casse

Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible. Pour modifier ce comportement, définissez <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> sur `true`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Voici un exemple de JSON avec les noms de propriété de casse mixte. Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Handle de dépassement JSON

Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible. Par exemple, supposons que votre type de cible est le suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

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

Si vous désérialisez le JSON indiqué dans le type indiqué, les propriétés `DatesAvailable` et `SummaryWords` ne peuvent pas être placées et sont perdues. Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de type `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la propriété `ExtensionData` :

|Les |Value  |Remarques  |
|---------|---------|---------|
| Date    | DE 8/1/2019 12:00:00 À 07:00||
| TemperatureCelsius| 0 | Incompatibilité sensible à la casse (`temperatureCelsius` dans le JSON), la propriété n’est donc pas définie. |
| Récapitulatif | Très chargé ||
| ExtensionData | temperatureCelsius : 25 |Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.|
|| DatesAvailable:<br>  DE 8/1/2019 12:00:00 À 07:00<br>DE 8/2/2019 12:00:00 À 07:00 |Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.|
| |SummaryWords:<br>Cool<br>Venteux<br>Humide |Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.|

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

Notez que le nom de la propriété `ExtensionData` n’apparaît pas dans le JSON. Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.

## <a name="ignore-null-when-deserializing"></a>Ignorer la valeur null lors de la désérialisation

Par défaut, si une propriété dans JSON a la valeur null, la propriété correspondante dans l’objet cible a la valeur null. Dans certains scénarios, la propriété cible peut avoir une valeur par défaut et vous ne souhaitez pas qu’une valeur null remplace la valeur par défaut.

Par exemple, supposons que le code suivant représente votre objet cible :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Et supposons que le code JSON suivant est désérialisé :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Après la désérialisation, la propriété `Summary` de l’objet `WeatherForecastWithDefault` a la valeur null.

Pour modifier ce comportement, affectez la valeur `true`à <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

Avec cette option, la propriété `Summary` de l’objet `WeatherForecastWithDefault` est la valeur par défaut « no Summary » après la désérialisation.

Les valeurs NULL dans le JSON sont ignorées uniquement si elles sont valides. Les valeurs NULL pour les types valeur non Nullable provoquent des exceptions.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter et JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un `ReadOnlySpan<byte>` ou d’un `ReadOnlySequence<byte>`. Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés. La méthode <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> utilise `Utf8JsonReader` en coulisses.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants comme `String`, `Int32`et `DateTime`. Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés. La méthode <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> utilise `Utf8JsonWriter` en coulisses.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> permet de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader`. Le DOM fournit un accès aléatoire aux données dans une charge utile JSON. Les éléments JSON qui composent la charge utile sont accessibles via le type de <xref:System.Text.Json.JsonElement>. Le type de `JsonElement` fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .NET courants. `JsonDocument` expose une propriété <xref:System.Text.Json.JsonDocument.RootElement>.

Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Utiliser JsonDocument pour l’accès aux données

L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.JsonDocument> pour l’accès aléatoire aux données dans une chaîne JSON :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Le code précédent :

* Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString`.
* Calcule une qualité moyenne pour les objets d’un tableau de `Students` qui ont une propriété `Grade`. 
* Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.
* Compte les étudiants en incrémentant une variable de `count` à chaque itération. Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, comme indiqué dans l’exemple suivant :

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Voici un exemple du JSON traité par ce code :

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Utiliser JsonDocument pour écrire du code JSON

L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Le code précédent :

* Lit un fichier JSON, charge les données dans un `JsonDocument`et écrit le format JSON (Pretty-imprimed) dans un fichier.
* Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.
* Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer. Une alternative consiste à laisser l’enregistreur se vider lorsqu’il est supprimé. 

Voici un exemple d’entrée JSON à traiter par l’exemple de code :

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

Le résultat est la sortie JSON imprimée suivante :

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utiliser Utf8JsonWriter

L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonWriter> :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utiliser Utf8JsonReader

L’exemple suivant montre comment utiliser la classe <xref:System.Text.Json.Utf8JsonReader> :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Le code précédent suppose que la variable `jsonUtf8` est un tableau d’octets contenant un JSON valide, encodé au format UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrer les données à l’aide de Utf8JsonReader

L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

Le code précédent :

* Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.
* Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».
* Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8. Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>`, à l’aide du code suivant :

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

  Si le fichier contient une marque d’ordre d’octet UTF-8 (BOM), supprimez-le avant de passer les octets au `Utf8JsonReader`, puisque le lecteur attend du texte. Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.

Voici un exemple JSON que le code précédent peut lire. Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Ressources supplémentaires

* [présentation de System.Text.Json](system-text-json-overview.md)
* [Comment écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md)
* [Migration à partir de Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Prise en charge des valeurs DateTime et DateTimeOffset dans System.Text.Json](../datetime/system-text-json-support.md)
* [informations de référence sur l’API System.Text.Json](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
