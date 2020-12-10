---
title: Comment gérer le JSON de dépassement de capacité avec System.Text.Json
description: Découvrez comment gérer le JSON de dépassement de capacité lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 265ce4f77d353720419122d17c36e508a377b68f
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008914"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="7badb-103">Comment gérer le JSON de dépassement de capacité avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="7badb-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="7badb-104">Dans cet article, vous allez apprendre à gérer le code JSON de dépassement de capacité avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7badb-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="7badb-105">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="7badb-105">Handle overflow JSON</span></span>

<span data-ttu-id="7badb-106">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="7badb-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="7badb-107">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="7badb-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="7badb-108">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="7badb-108">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="7badb-109">Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` `SummaryWords` Propriétés et ne sont pas visibles et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="7badb-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="7badb-110">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de `Dictionary<string,object>` type `Dictionary<string,JsonElement>` ou :</span><span class="sxs-lookup"><span data-stu-id="7badb-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="7badb-111">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la `ExtensionData` propriété :</span><span class="sxs-lookup"><span data-stu-id="7badb-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="7badb-112">Propriété</span><span class="sxs-lookup"><span data-stu-id="7badb-112">Property</span></span> | <span data-ttu-id="7badb-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="7badb-113">Value</span></span> | <span data-ttu-id="7badb-114">Notes</span><span class="sxs-lookup"><span data-stu-id="7badb-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="7badb-115">Incompatibilité sensible à la casse ( `temperatureCelsius` dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="7badb-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="7badb-116">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="7badb-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="7badb-117">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="7badb-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="7badb-118">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="7badb-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="7badb-119">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="7badb-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="7badb-120">Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="7badb-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="7badb-121">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="7badb-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="7badb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7badb-122">See also</span></span>

* [<span data-ttu-id="7badb-123">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="7badb-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="7badb-124">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="7badb-124">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="7badb-125">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="7badb-125">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="7badb-126">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="7badb-126">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="7badb-127">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="7badb-127">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="7badb-128">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="7badb-128">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="7badb-129">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="7badb-129">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="7badb-130">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="7badb-130">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="7badb-131">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="7badb-131">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="7badb-132">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="7badb-132">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="7badb-133">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="7badb-133">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="7badb-134">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="7badb-134">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="7badb-135">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="7badb-135">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="7badb-136">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="7badb-136">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="7badb-137">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="7badb-137">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="7badb-138">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="7badb-138">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="7badb-139">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="7badb-139">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
