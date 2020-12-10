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
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a><span data-ttu-id="115f2-103">Comment personnaliser les noms et les valeurs des propriétés avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="115f2-103">How to customize property names and values with System.Text.Json</span></span>

<span data-ttu-id="115f2-104">Par défaut, les noms de propriété et les clés de dictionnaire sont inchangés dans la sortie JSON, y compris la casse.</span><span class="sxs-lookup"><span data-stu-id="115f2-104">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="115f2-105">Les valeurs enum sont représentées sous forme de nombres.</span><span class="sxs-lookup"><span data-stu-id="115f2-105">Enum values are represented as numbers.</span></span> <span data-ttu-id="115f2-106">Dans cet article, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="115f2-106">In this article, you'll learn how to:</span></span>

> [!NOTE]
> <span data-ttu-id="115f2-107">La [valeur par défaut du Web](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) est casse mixte.</span><span class="sxs-lookup"><span data-stu-id="115f2-107">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is camel case.</span></span>

* [<span data-ttu-id="115f2-108">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="115f2-108">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="115f2-109">Convertir tous les noms de propriété en casse mixte</span><span class="sxs-lookup"><span data-stu-id="115f2-109">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="115f2-110">Implémenter une stratégie d’attribution de noms de propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="115f2-110">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="115f2-111">Convertir les clés du dictionnaire en casse mixte</span><span class="sxs-lookup"><span data-stu-id="115f2-111">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="115f2-112">Convertir des enums en chaînes et casse mixte</span><span class="sxs-lookup"><span data-stu-id="115f2-112">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="115f2-113">Pour les autres scénarios qui nécessitent un traitement spécial des noms et des valeurs de propriété JSON, vous pouvez [implémenter des convertisseurs personnalisés](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="115f2-113">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

## <a name="customize-individual-property-names"></a><span data-ttu-id="115f2-114">Personnaliser les noms de propriété individuels</span><span class="sxs-lookup"><span data-stu-id="115f2-114">Customize individual property names</span></span>

<span data-ttu-id="115f2-115">Pour définir le nom de chaque propriété, utilisez l’attribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="115f2-115">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="115f2-116">Voici un exemple de type pour sérialiser et JSON obtenu :</span><span class="sxs-lookup"><span data-stu-id="115f2-116">Here's an example type to serialize and resulting JSON:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="115f2-117">Nom de propriété défini par cet attribut :</span><span class="sxs-lookup"><span data-stu-id="115f2-117">The property name set by this attribute:</span></span>

* <span data-ttu-id="115f2-118">S’applique dans les deux directions, pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="115f2-118">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="115f2-119">Est prioritaire sur les stratégies d’attribution de noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="115f2-119">Takes precedence over property naming policies.</span></span>

## <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="115f2-120">Utiliser la casse mixte pour tous les noms de propriété JSON</span><span class="sxs-lookup"><span data-stu-id="115f2-120">Use camel case for all JSON property names</span></span>

<span data-ttu-id="115f2-121">Pour utiliser la casse mixte pour tous les noms de propriétés JSON, affectez <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> la valeur à `JsonNamingPolicy.CamelCase` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="115f2-121">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

<span data-ttu-id="115f2-122">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="115f2-122">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="115f2-123">La stratégie de nommage de propriété casse mixte :</span><span class="sxs-lookup"><span data-stu-id="115f2-123">The camel case property naming policy:</span></span>

* <span data-ttu-id="115f2-124">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="115f2-124">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="115f2-125">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="115f2-125">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="115f2-126">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas une casse mixte.</span><span class="sxs-lookup"><span data-stu-id="115f2-126">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

## <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="115f2-127">Utiliser une stratégie d’attribution de noms de propriété JSON personnalisée</span><span class="sxs-lookup"><span data-stu-id="115f2-127">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="115f2-128">Pour utiliser une stratégie d’attribution de noms de propriété JSON personnalisée, créez une classe qui dérive de <xref:System.Text.Json.JsonNamingPolicy> et substituez la <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> méthode, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="115f2-128">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

<span data-ttu-id="115f2-129">Définissez ensuite la <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriété sur une instance de votre classe de stratégie d’attribution de noms :</span><span class="sxs-lookup"><span data-stu-id="115f2-129">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

<span data-ttu-id="115f2-130">Voici un exemple de classe pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="115f2-130">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="115f2-131">La stratégie d’attribution de noms de propriété JSON :</span><span class="sxs-lookup"><span data-stu-id="115f2-131">The JSON property naming policy:</span></span>

* <span data-ttu-id="115f2-132">S’applique à la sérialisation et à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="115f2-132">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="115f2-133">Est substitué par des `[JsonPropertyName]` attributs.</span><span class="sxs-lookup"><span data-stu-id="115f2-133">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="115f2-134">C’est pourquoi le nom de la propriété JSON `Wind` dans l’exemple n’est pas en majuscules.</span><span class="sxs-lookup"><span data-stu-id="115f2-134">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

## <a name="camel-case-dictionary-keys"></a><span data-ttu-id="115f2-135">Clés de dictionnaire de casse mixte</span><span class="sxs-lookup"><span data-stu-id="115f2-135">Camel case dictionary keys</span></span>

<span data-ttu-id="115f2-136">Si une propriété d’un objet à sérialiser est de type `Dictionary<string,TValue>` , les `string` clés peuvent être converties en casse mixte.</span><span class="sxs-lookup"><span data-stu-id="115f2-136">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="115f2-137">Pour ce faire, affectez <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> à `JsonNamingPolicy.CamelCase` la valeur, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="115f2-137">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

<span data-ttu-id="115f2-138">La sérialisation d’un objet avec un dictionnaire nommé `TemperatureRanges` qui a des paires clé-valeur `"ColdMinTemp", 20` et `"HotMinTemp", 40` provoquerait une sortie JSON similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="115f2-138">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="115f2-139">La stratégie d’attribution de noms de casse mixte pour les clés de dictionnaire s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="115f2-139">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="115f2-140">Si vous désérialisez un dictionnaire, les clés correspondent au fichier JSON même si vous spécifiez `JsonNamingPolicy.CamelCase` pour le `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="115f2-140">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

## <a name="enums-as-strings"></a><span data-ttu-id="115f2-141">Enums en tant que chaînes</span><span class="sxs-lookup"><span data-stu-id="115f2-141">Enums as strings</span></span>

<span data-ttu-id="115f2-142">Par défaut, les enums sont sérialisés en tant que nombres.</span><span class="sxs-lookup"><span data-stu-id="115f2-142">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="115f2-143">Pour sérialiser les noms d’enum sous forme de chaînes, utilisez <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="115f2-143">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="115f2-144">Par exemple, supposons que vous deviez sérialiser la classe suivante qui a une énumération :</span><span class="sxs-lookup"><span data-stu-id="115f2-144">For example, suppose you need to serialize the following class that has an enum:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

<span data-ttu-id="115f2-145">Si le résumé est `Hot` , par défaut, le JSON sérialisé a la valeur numérique 3 :</span><span class="sxs-lookup"><span data-stu-id="115f2-145">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="115f2-146">L’exemple de code suivant sérialise les noms d’enum à la place des valeurs numériques, et convertit les noms en casse mixte :</span><span class="sxs-lookup"><span data-stu-id="115f2-146">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

<span data-ttu-id="115f2-147">Le JSON obtenu ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="115f2-147">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="115f2-148">Les noms de chaîne enum peuvent également être désérialisés, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="115f2-148">Enum string names can be deserialized as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a><span data-ttu-id="115f2-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="115f2-149">See also</span></span>

* [<span data-ttu-id="115f2-150">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="115f2-150">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="115f2-151">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="115f2-151">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="115f2-152">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="115f2-152">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="115f2-153">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="115f2-153">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="115f2-154">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="115f2-154">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="115f2-155">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="115f2-155">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="115f2-156">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="115f2-156">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="115f2-157">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="115f2-157">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="115f2-158">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="115f2-158">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="115f2-159">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="115f2-159">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="115f2-160">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="115f2-160">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="115f2-161">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="115f2-161">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="115f2-162">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="115f2-162">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="115f2-163">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="115f2-163">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="115f2-164">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="115f2-164">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="115f2-165">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="115f2-165">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="115f2-166">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="115f2-166">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
