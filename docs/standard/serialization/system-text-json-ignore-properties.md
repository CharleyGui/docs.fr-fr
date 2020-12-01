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
ms.openlocfilehash: ed7ef8509d6660bbbbaf194a87aa9d4815143507
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439955"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="8da24-103">Comment ignorer les propriétés avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8da24-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="8da24-104">Lors de la sérialisation d’objets C# vers JavaScript Object Notation (JSON), par défaut, toutes les propriétés publiques sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="8da24-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="8da24-105">Si vous ne souhaitez pas que certains d’entre eux apparaissent dans le JSON obtenu, vous avez plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="8da24-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="8da24-106">Dans cet article, vous allez apprendre à ignorer les propriétés en fonction de différents critères :</span><span class="sxs-lookup"><span data-stu-id="8da24-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="8da24-107">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="8da24-107">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="8da24-108">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8da24-108">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="8da24-109">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="8da24-109">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="8da24-110">Toutes les propriétés de valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8da24-110">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="8da24-111">Propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="8da24-111">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="8da24-112">Toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8da24-112">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="8da24-113">Toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="8da24-113">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="8da24-114">Ignorer les propriétés individuelles</span><span class="sxs-lookup"><span data-stu-id="8da24-114">Ignore individual properties</span></span>

<span data-ttu-id="8da24-115">Pour ignorer des propriétés individuelles, utilisez l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8da24-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="8da24-116">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="8da24-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8da24-117">Vous pouvez spécifier une exclusion conditionnelle en définissant la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` .</span><span class="sxs-lookup"><span data-stu-id="8da24-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="8da24-118">L' <xref:System.Text.Json.Serialization.JsonIgnoreCondition> énumération fournit les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="8da24-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="8da24-119">`Always` -La propriété est toujours ignorée.</span><span class="sxs-lookup"><span data-stu-id="8da24-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="8da24-120">Si aucun `Condition` n’est spécifié, cette option est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8da24-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="8da24-121">`Never` -La propriété est toujours sérialisée et désérialisée, quels que soient `DefaultIgnoreCondition` les `IgnoreReadOnlyProperties` `IgnoreReadOnlyFields` paramètres globaux, et.</span><span class="sxs-lookup"><span data-stu-id="8da24-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="8da24-122">`WhenWritingDefault` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` , d’un type valeur Nullable `null` ou d’un type valeur `default` .</span><span class="sxs-lookup"><span data-stu-id="8da24-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="8da24-123">`WhenWritingNull` -La propriété est ignorée lors de la sérialisation s’il s’agit d’un type référence `null` ou d’un type valeur Nullable `null` .</span><span class="sxs-lookup"><span data-stu-id="8da24-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="8da24-124">L’exemple suivant illustre l’utilisation de la propriété de l’attribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` :</span><span class="sxs-lookup"><span data-stu-id="8da24-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="8da24-125">Ignorer toutes les propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8da24-125">Ignore all read-only properties</span></span>

<span data-ttu-id="8da24-126">Une propriété est en lecture seule si elle contient un accesseur get public, mais pas un accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="8da24-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="8da24-127">Pour ignorer toutes les propriétés en lecture seule lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> à `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8da24-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="8da24-128">Voici un exemple de type pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="8da24-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="8da24-129">Cette option s’applique uniquement à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="8da24-129">This option applies only to serialization.</span></span> <span data-ttu-id="8da24-130">Pendant la désérialisation, les propriétés en lecture seule sont ignorées par défaut.</span><span class="sxs-lookup"><span data-stu-id="8da24-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8da24-131">Cette option s’applique uniquement aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="8da24-131">This option applies only to properties.</span></span> <span data-ttu-id="8da24-132">Pour ignorer les champs en lecture seule lors de la [sérialisation des champs](system-text-json-how-to.md#include-fields), utilisez le <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> paramètre global.</span><span class="sxs-lookup"><span data-stu-id="8da24-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="8da24-133">Ignorer toutes les propriétés de valeur null</span><span class="sxs-lookup"><span data-stu-id="8da24-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8da24-134">Pour ignorer toutes les propriétés de valeur null, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8da24-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="8da24-135">Pour ignorer toutes les propriétés de valeur null lors de la sérialisation, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> à la propriété `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8da24-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="8da24-136">Voici un exemple d’objet pour sérialiser et la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="8da24-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="8da24-137">Propriété</span><span class="sxs-lookup"><span data-stu-id="8da24-137">Property</span></span>             | <span data-ttu-id="8da24-138">Valeur</span><span class="sxs-lookup"><span data-stu-id="8da24-138">Value</span></span>                         |
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

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="8da24-139">Ignorer toutes les propriétés de valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8da24-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="8da24-140">Pour empêcher la sérialisation des valeurs par défaut dans les propriétés de type valeur, affectez la valeur <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> à la propriété <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8da24-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="8da24-141">Le <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> paramètre empêche également la sérialisation des propriétés de type référence null-valeur et de type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="8da24-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="8da24-142">Il n’existe aucune méthode intégrée pour empêcher la sérialisation des propriétés avec des valeurs par défaut de type valeur dans `System.Text.Json` dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="8da24-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="8da24-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8da24-143">See also</span></span>

* [<span data-ttu-id="8da24-144">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="8da24-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="8da24-145">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="8da24-145">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="8da24-146">Activer la correspondance qui ne respecte pas la casse</span><span class="sxs-lookup"><span data-stu-id="8da24-146">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="8da24-147">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="8da24-147">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="8da24-148">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="8da24-148">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="8da24-149">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="8da24-149">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="8da24-150">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="8da24-150">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="8da24-151">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="8da24-151">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="8da24-152">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="8da24-152">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="8da24-153">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="8da24-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
