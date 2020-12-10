---
title: Comment ignorer les propriétés avec System.Text.Json
description: Découvrez comment ignorer les propriétés lors de la sérialisation avec System.Text.Json dans .net.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6d703156d50a3e00a33cea5e15be2df911ed7c1b
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008810"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a>Comment ignorer les propriétés avec System.Text.Json

Lors de la sérialisation d’objets C# vers JavaScript Object Notation (JSON), par défaut, toutes les propriétés publiques sont sérialisées. Si vous ne souhaitez pas que certains d’entre eux apparaissent dans le JSON obtenu, vous avez plusieurs options. Dans cet article, vous allez apprendre à ignorer les propriétés en fonction de différents critères :

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

## <a name="ignore-individual-properties"></a>Ignorer les propriétés individuelles

Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Voici un exemple de type pour sérialiser et la sortie JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

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
* `WhenWritingDefault` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` , d’un type valeur Nullable `null` ou d’un type valeur `default` .
* `WhenWritingNull` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` ou d’un type valeur Nullable `null` .

L’exemple suivant illustre l’utilisation de la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a>Ignorer toutes les propriétés en lecture seule

Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public. Pour ignorer toutes les propriétés en lecture seule lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> à `true` , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

Voici un exemple de type pour sérialiser et la sortie JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Cette option s’applique uniquement à la sérialisation. Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.

::: zone pivot="dotnet-5-0"
Cette option s’applique uniquement aux propriétés. Pour ignorer les champs en lecture seule lors de la [sérialisation des champs](system-text-json-how-to.md#include-fields), utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.
::: zone-end

## <a name="ignore-all-null-value-properties"></a>Ignorer toutes les propriétés de valeur null

::: zone pivot="dotnet-5-0"
Pour ignorer toutes les propriétés de valeur null, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> , comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
Pour ignorer toutes les propriétés de valeur null lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> à la propriété `true` , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

Voici un exemple d’objet pour sérialiser et la sortie JSON :

| Propriété             | Valeur                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a>Ignorer toutes les propriétés de valeur par défaut

::: zone pivot="dotnet-5-0"
Pour empêcher la sérialisation des valeurs par défaut dans les propriétés de type valeur, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

Le <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> paramètre empêche également la sérialisation des propriétés de type référence null-valeur et de type valeur Nullable.

::: zone pivot="dotnet-core-3-1"
Il n’existe aucune méthode intégrée pour empêcher la sérialisation des propriétés avec des valeurs par défaut de type valeur dans `System.Text.Json` dans .net Core 3,1.
::: zone-end

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Guide pratique pour sérialiser et désérialiser JSON](system-text-json-how-to.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
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
