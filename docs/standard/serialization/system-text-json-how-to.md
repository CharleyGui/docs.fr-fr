---
title: Comment sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Découvrez comment utiliser l' System.Text.Json espace de noms pour sérialiser et désérialiser à partir de JSON dans .net. Comprend un exemple de code.
ms.date: 01/04/2021
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
ms.openlocfilehash: fd92c067fc76bea6bede1e5370e7ac168856fa9b
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058100"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Comment sérialiser et désérialiser (marshaler et démarshaler) JSON dans .NET

Cet article explique comment utiliser l' <xref:System.Text.Json?displayProperty=fullName> espace de noms pour sérialiser et désérialiser à partir de JavaScript Object Notation (JSON). Si vous transférez du code existant à partir de `Newtonsoft.Json` , consultez [Comment migrer vers `System.Text.Json` ](system-text-json-migrate-from-newtonsoft-how-to.md).

Les instructions et l’exemple de code utilisent directement la bibliothèque, et non un Framework comme [ASP.net Core](/aspnet/core/).

La majeure partie de l’exemple de code de sérialisation affecte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` la valeur « joli Printing » au format JSON (avec mise en retrait et espace blanc pour la lisibilité humaine). Pour une utilisation en production, vous acceptez généralement la valeur par défaut de `false` pour ce paramètre, car l’ajout d’espaces blancs inutiles peut entraîner un impact négatif et sensible sur les performances et l’utilisation de la bande passante.

Les exemples de code font référence à la classe et aux variantes suivantes :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

> [!NOTE]
> System.Text.Json utilise des [structs de référence](../../csharp/language-reference/builtin-types/struct.md#ref-struct), qui ne sont pas pris en charge par Visual Basic. Si vous essayez d’utiliser System.Text.Json des API avec Visual Basic, vous recevez des erreurs de compilation BC40000. Le message d’erreur indique que le problème est une API obsolète, mais le problème réel est l’absence de `ref struct` prise en charge dans le compilateur.

## <a name="namespaces"></a>Espaces de noms

L' <xref:System.Text.Json> espace de noms contient tous les points d’entrée et les principaux types. L' <xref:System.Text.Json.Serialization> espace de noms contient des attributs et des API pour les scénarios avancés et la personnalisation propres à la sérialisation et à la désérialisation. Les exemples de code présentés dans cet article requièrent des `using` directives pour l’un de ces espaces de noms ou les deux :

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> Les attributs de l' <xref:System.Runtime.Serialization> espace de noms ne sont pas pris en charge dans `System.Text.Json` .

## <a name="how-to-write-net-objects-as-json-serialize"></a>Comment écrire des objets .NET au format JSON (sérialiser)

Pour écrire du code JSON dans une chaîne ou dans un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode.

L’exemple suivant crée JSON sous forme de chaîne :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

L’exemple suivant utilise du code synchrone pour créer un fichier JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

L’exemple suivant utilise du code asynchrone pour créer un fichier JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

Les exemples précédents utilisent l’inférence de type pour le type en cours de sérialisation. Une surcharge de `Serialize()` prend un paramètre de type générique :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a>Exemple de sérialisation

Voici un exemple de classe qui contient des propriétés de type collection et un type défini par l’utilisateur :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> « POCO » signifie « [Plain Old CLR Object](https://en.wikipedia.org/wiki/Plain_old_CLR_object)». Un POCO est un type .NET qui ne dépend d’aucun type spécifique à l’infrastructure, par exemple par le biais de l’héritage ou des attributs.

La sortie JSON de la sérialisation d’une instance du type précédent ressemble à l’exemple suivant. La sortie JSON est minimisés (les espaces blancs, les mises en retrait et les caractères de nouvelle ligne sont supprimés) par défaut :

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

## <a name="serialize-to-utf-8"></a>Sérialiser vers UTF-8

Pour sérialiser vers UTF-8, appelez la <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> méthode :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

Une <xref:System.Text.Json.JsonSerializer.Serialize%2A> surcharge qui prend un <xref:System.Text.Json.Utf8JsonWriter> est également disponible.

La sérialisation en UTF-8 est environ 5-10% plus rapide que l’utilisation des méthodes basées sur une chaîne. La différence est que les octets (au format UTF-8) n’ont pas besoin d’être convertis en chaînes (UTF-16).

## <a name="serialization-behavior"></a>Comportements de sérialisation

::: zone pivot="dotnet-5-0"

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier des propriétés à ignorer](system-text-json-ignore-properties.md).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](system-text-json-customize-properties.md).
* Par défaut, les références circulaires sont détectées et les exceptions levées. Vous pouvez [conserver les références et gérer les références circulaires](system-text-json-preserve-references.md).
* Par défaut, les [champs](../../csharp/programming-guide/classes-and-structs/fields.md) sont ignorés. Vous pouvez [inclure des champs](#include-fields).

Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents. Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Par défaut, toutes les propriétés publiques sont sérialisées. Vous pouvez [spécifier des propriétés à ignorer](system-text-json-ignore-properties.md).
* L' [encodeur par défaut](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) échappe les caractères non-ASCII, les caractères respectant le format HTML dans la plage ASCII, et les caractères qui doivent être échappés conformément à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Par défaut, JSON est minimisés. Vous pouvez [très bien imprimer le JSON](#serialize-to-formatted-json).
* Par défaut, la casse des noms JSON correspond aux noms .NET. Vous pouvez [personnaliser la casse du nom JSON](system-text-json-customize-properties.md).
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

## <a name="how-to-read-json-as-net-objects-deserialize"></a>Comment lire JSON en tant qu’objets .NET (désérialisation)

Pour désérialiser à partir d’une chaîne ou d’un fichier, appelez la <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode.

L’exemple suivant lit JSON à partir d’une chaîne et crée une instance de la `WeatherForecastWithPOCOs` classe indiquée précédemment pour l' [exemple de sérialisation](#serialization-example):

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

Pour désérialiser à partir d’un fichier à l’aide d’un code synchrone, lisez le fichier dans une chaîne, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

Pour désérialiser à partir d’un fichier à l’aide de code asynchrone, appelez la <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> méthode :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

> [!TIP]
> Si vous souhaitez désérialiser JSON et que vous n’avez pas la classe dans laquelle la désérialiser, Visual Studio 2019 peut générer automatiquement la classe dont vous avez besoin :
>
> 1. Copiez le JSON que vous devez désérialiser.
> 1. Créez un fichier de classe et supprimez le code du modèle.
> 1. Choisissez **Edition**  >  **coller spécial**  >  **coller JSON comme classes**.
>
> Le résultat est une classe que vous pouvez utiliser pour votre cible de désérialisation.

## <a name="deserialize-from-utf-8"></a>Désérialiser à partir d’UTF-8

Pour désérialiser à partir d’UTF-8, appelez une <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> surcharge qui accepte un `ReadOnlySpan<byte>` ou un `Utf8JsonReader` , comme indiqué dans les exemples suivants. Les exemples supposent que le JSON se trouve dans un tableau d’octets nommé jsonUtf8Bytes.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a>Comportement de la désérialisation

Les comportements suivants s’appliquent lors de la désérialisation de JSON :

::: zone pivot="dotnet-5-0"

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](system-text-json-character-casing.md).
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* Les constructeurs non publics sont ignorés par le sérialiseur.
* La désérialisation des objets immuables ou des propriétés en lecture seule est prise en charge. Consultez [les types immuables et les enregistrements](system-text-json-immutability.md).
* Par défaut, les enums sont pris en charge en tant que nombres. Vous pouvez [sérialiser les noms d’enum en tant que chaînes](system-text-json-customize-properties.md#enums-as-strings).
* Par défaut, les champs sont ignorés. Vous pouvez [inclure des champs](#include-fields).
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](system-text-json-invalid-json.md).
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents. Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Par défaut, la correspondance de nom de propriété respecte la casse. Vous pouvez [spécifier le non-respect de la casse](system-text-json-character-casing.md). Par défaut, les applications ASP.NET Core [spécifient le non-respect](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)de la casse.
* Si le JSON contient une valeur pour une propriété en lecture seule, la valeur est ignorée et aucune exception n’est levée.
* Un constructeur sans paramètre, qui peut être public, Internal ou Private, est utilisé pour la désérialisation.
* La désérialisation des objets immuables ou des propriétés en lecture seule n’est pas prise en charge.
* Par défaut, les enums sont pris en charge en tant que nombres. Vous pouvez [sérialiser les noms d’enum en tant que chaînes](system-text-json-customize-properties.md#enums-as-strings).
* Les champs ne sont pas pris en charge.
* Par défaut, les commentaires ou les virgules de fin dans le JSON lèvent des exceptions. Vous pouvez [autoriser les commentaires et les virgules de fin](system-text-json-invalid-json.md).
* La [profondeur maximale par défaut](xref:System.Text.Json.JsonReaderOptions.MaxDepth) est 64.

Lorsque vous utilisez System.Text.Json indirectement dans une application ASP.net Core, certains comportements par défaut sont différents. Pour plus d’informations, consultez [paramètres par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
::: zone-end

Vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md) pour fournir des fonctionnalités qui ne sont pas prises en charge par les convertisseurs intégrés.

## <a name="serialize-to-formatted-json"></a>Sérialiser au format JSON

Pour imprimer la sortie JSON, définissez <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> sur `true` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

Voici un exemple de type à sérialiser et à imprimer une sortie JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Si vous utilisez `JsonSerializerOptions` à plusieurs reprises avec les mêmes options, ne créez pas une nouvelle `JsonSerializerOptions` instance à chaque fois que vous l’utilisez. Réutilisez la même instance pour chaque appel. Pour plus d’informations, consultez [réutiliser des instances JsonSerializerOptions](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).

## <a name="include-fields"></a>Inclure les champs

::: zone pivot="dotnet-5-0"
Utilisez le <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> paramètre global ou l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) pour inclure les champs lors de la sérialisation ou de la désérialisation, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

Pour ignorer les champs en lecture seule, utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.
::: zone-end

::: zone pivot="dotnet-core-3-1"
Les champs ne sont pas pris en charge dans System.Text.Json dans .net Core 3,1. Les [convertisseurs personnalisés](system-text-json-converters-how-to.md) peuvent fournir cette fonctionnalité.
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>Méthodes d’extension HttpClient et HttpContent

::: zone pivot="dotnet-5-0"

La sérialisation et la désérialisation des charges utiles JSON à partir du réseau sont des opérations courantes. Les méthodes d’extension sur [httpclient](xref:System.Net.Http.Json.HttpClientJsonExtensions) et [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) vous permettent d’effectuer ces opérations sur une seule ligne de code. Ces méthodes d’extension utilisent [des valeurs par défaut Web pour JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).

L’exemple suivant illustre l’utilisation de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> et <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

Il existe également des méthodes d’extension pour System.Text.Json sur [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).
::: zone-end

::: zone pivot="dotnet-core-3-1"
Les méthodes d’extension sur `HttpClient` et ne `HttpContent` sont pas disponibles dans System.Text.Json dans .net Core 3,1.
::: zone-end

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Préserver les références](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [Types de collections pris en charge dans System.Text.Json](system-text-json-supported-collection-types.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
