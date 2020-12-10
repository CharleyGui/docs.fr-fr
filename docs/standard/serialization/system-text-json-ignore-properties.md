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
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="8c4c0-103">Comment ignorer les propriétés avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8c4c0-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="8c4c0-104">Lors de la sérialisation d’objets C# vers JavaScript Object Notation (JSON), par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="8c4c0-105">Si vous ne souhaitez pas que certains d’entre eux apparaissent dans le JSON obtenu, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="8c4c0-106">Dans cet article, vous allez apprendre à ignorer les propriétés en fonction de différents critères :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="8c4c0-107">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="8c4c0-107">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="8c4c0-108">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8c4c0-108">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="8c4c0-109">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="8c4c0-109">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="8c4c0-110">Toutes les propriétés de valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8c4c0-110">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="8c4c0-111">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="8c4c0-111">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="8c4c0-112">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8c4c0-112">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="8c4c0-113">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="8c4c0-113">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="8c4c0-114">Ignorer les propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="8c4c0-114">Ignore individual properties</span></span>

<span data-ttu-id="8c4c0-115">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8c4c0-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="8c4c0-116">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8c4c0-117">Vous pouvez spécifier une exclusion conditionnelle en définissant la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` .</span><span class="sxs-lookup"><span data-stu-id="8c4c0-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="8c4c0-118">L' <xref:System.Text.Json.Serialization.JsonIgnoreCondition> énumération fournit les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="8c4c0-119">`Always` -La propriété est toujours ignorée.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="8c4c0-120">Si aucun `Condition` n’est spécifié, cette option est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="8c4c0-121">`Never` -La propriété est toujours sérialisée et désérialisée, quels que soient `DefaultIgnoreCondition` les `IgnoreReadOnlyProperties` `IgnoreReadOnlyFields` paramètres globaux, et.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="8c4c0-122">`WhenWritingDefault` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` , d’un type valeur Nullable `null` ou d’un type valeur `default` .</span><span class="sxs-lookup"><span data-stu-id="8c4c0-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="8c4c0-123">`WhenWritingNull` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` ou d’un type valeur Nullable `null` .</span><span class="sxs-lookup"><span data-stu-id="8c4c0-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="8c4c0-124">L’exemple suivant illustre l’utilisation de la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="8c4c0-125">Ignorer toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8c4c0-125">Ignore all read-only properties</span></span>

<span data-ttu-id="8c4c0-126">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="8c4c0-127">Pour ignorer toutes les propriétés en lecture seule lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> à `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="8c4c0-128">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="8c4c0-129">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-129">This option applies only to serialization.</span></span> <span data-ttu-id="8c4c0-130">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8c4c0-131">Cette option s’applique uniquement aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-131">This option applies only to properties.</span></span> <span data-ttu-id="8c4c0-132">Pour ignorer les champs en lecture seule lors de la [sérialisation des champs](system-text-json-how-to.md#include-fields), utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="8c4c0-133">Ignorer toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="8c4c0-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8c4c0-134">Pour ignorer toutes les propriétés de valeur null, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="8c4c0-135">Pour ignorer toutes les propriétés de valeur null lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> à la propriété `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="8c4c0-136">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="8c4c0-137">Propriété</span><span class="sxs-lookup"><span data-stu-id="8c4c0-137">Property</span></span>             | <span data-ttu-id="8c4c0-138">Valeur</span><span class="sxs-lookup"><span data-stu-id="8c4c0-138">Value</span></span>                         |
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

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="8c4c0-139">Ignorer toutes les propriétés de valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8c4c0-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8c4c0-140">Pour empêcher la sérialisation des valeurs par défaut dans les propriétés de type valeur, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8c4c0-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="8c4c0-141">Le <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> paramètre empêche également la sérialisation des propriétés de type référence null-valeur et de type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="8c4c0-142">Il n’existe aucune méthode intégrée pour empêcher la sérialisation des propriétés avec des valeurs par défaut de type valeur dans `System.Text.Json` dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="8c4c0-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c4c0-143">See also</span></span>

* [<span data-ttu-id="8c4c0-144">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="8c4c0-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="8c4c0-145">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="8c4c0-145">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="8c4c0-146">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="8c4c0-146">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="8c4c0-147">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="8c4c0-147">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="8c4c0-148">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="8c4c0-148">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="8c4c0-149">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="8c4c0-149">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="8c4c0-150">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="8c4c0-150">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="8c4c0-151">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="8c4c0-151">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="8c4c0-152">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="8c4c0-152">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="8c4c0-153">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="8c4c0-153">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="8c4c0-154">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8c4c0-154">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="8c4c0-155">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="8c4c0-155">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="8c4c0-156">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="8c4c0-156">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="8c4c0-157">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="8c4c0-157">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="8c4c0-158">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8c4c0-158">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="8c4c0-159">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="8c4c0-159">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="8c4c0-160">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="8c4c0-160">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
