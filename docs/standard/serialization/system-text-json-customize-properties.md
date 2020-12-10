---
title: Comment personnaliser les noms et les valeurs des propriétés avec System.Text.Json
description: Découvrez comment personnaliser les noms et les valeurs des propriétés lors de la sérialisation avec System.Text.Json dans .net.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b88509313e719ea993e00d889bc6145f4976a2d
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008901"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a>Comment personnaliser les noms et les valeurs des propriétés avec System.Text.Json

Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse. Les valeurs enum sont représentées sous forme de nombres. Dans cet article, vous allez apprendre à :

> [!NOTE]
> La [valeur par défaut du Web](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) est casse mixte.

* [Personnaliser les noms de propriété individuels](#customize-individual-property-names)
* [Convertir tous les noms de propriété en casse mixte](#use-camel-case-for-all-json-property-names)
* [Implémenter une stratégie d’attribution de noms de propriété personnalisée](#use-a-custom-json-property-naming-policy)
* [Convertir les clés du dictionnaire en casse mixte](#camel-case-dictionary-keys)
* [Convertir des enums en chaînes et casse mixte](#enums-as-strings)

Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).

## <a name="customize-individual-property-names"></a>Personnaliser les noms de propriété individuels

Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Voici un exemple de type pour sérialiser et JSON obtenu :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

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

## <a name="use-camel-case-for-all-json-property-names"></a>Utiliser la casse mixte pour tous les noms de propriété JSON

Pour utiliser la casse mixte pour tous les noms de propriétés JSON, affectez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> la valeur à `JsonNamingPolicy.CamelCase` , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

Voici un exemple de classe pour sérialiser et la sortie JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

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

## <a name="use-a-custom-json-property-naming-policy"></a>Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée

Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> méthode, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

Définissez ensuite la <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

Voici un exemple de classe pour sérialiser et la sortie JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

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

## <a name="camel-case-dictionary-keys"></a>Clés de dictionnaire de casse mixte

Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>` , les `string` clés peuvent être converties en casse mixte. Pour ce faire, affectez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> à `JsonNamingPolicy.CamelCase` la valeur, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

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

## <a name="enums-as-strings"></a>Enums en tant que chaînes

Par défaut, les enums sont sérialisés en tant que nombres. Pour sérialiser les noms d’enum sous forme de chaînes, utilisez <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .

Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

Si le résumé est `Hot` , par défaut, le JSON sérialisé a la valeur numérique 3 :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

Le JSON obtenu ressemble à l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Guide pratique pour sérialiser et désérialiser JSON](system-text-json-how-to.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
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
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
