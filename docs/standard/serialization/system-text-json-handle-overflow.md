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
ms.openlocfilehash: 2c40d42b26bc5bd05f592cc51c6b5b9b4c6bbd9e
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439980"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="0602a-103">Comment gérer le JSON de dépassement de capacité avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="0602a-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="0602a-104">Dans cet article, vous allez apprendre à gérer le code JSON de dépassement de capacité avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0602a-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="0602a-105">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="0602a-105">Handle overflow JSON</span></span>

<span data-ttu-id="0602a-106">Lors de la désérialisation, vous pouvez recevoir des données dans le JSON qui ne sont pas représentées par les propriétés du type cible.</span><span class="sxs-lookup"><span data-stu-id="0602a-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="0602a-107">Par exemple, supposons que votre type de cible est le suivant :</span><span class="sxs-lookup"><span data-stu-id="0602a-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="0602a-108">Et le JSON à désérialiser est le suivant :</span><span class="sxs-lookup"><span data-stu-id="0602a-108">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="0602a-109">Si vous désérialisez le JSON affiché dans le type indiqué, les `DatesAvailable` `SummaryWords` Propriétés et ne sont pas visibles et sont perdues.</span><span class="sxs-lookup"><span data-stu-id="0602a-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="0602a-110">Pour capturer des données supplémentaires telles que ces propriétés, appliquez l’attribut [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) à une propriété de `Dictionary<string,object>` type `Dictionary<string,JsonElement>` ou :</span><span class="sxs-lookup"><span data-stu-id="0602a-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="0602a-111">Lorsque vous désérialisez le JSON indiqué plus haut dans ce type d’exemple, les données supplémentaires deviennent des paires clé-valeur de la `ExtensionData` propriété :</span><span class="sxs-lookup"><span data-stu-id="0602a-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="0602a-112">Propriété</span><span class="sxs-lookup"><span data-stu-id="0602a-112">Property</span></span> | <span data-ttu-id="0602a-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="0602a-113">Value</span></span> | <span data-ttu-id="0602a-114">Notes</span><span class="sxs-lookup"><span data-stu-id="0602a-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="0602a-115">Incompatibilité sensible à la casse ( `temperatureCelsius` dans le JSON), la propriété n’est donc pas définie.</span><span class="sxs-lookup"><span data-stu-id="0602a-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="0602a-116">Étant donné que le cas ne correspondait pas, cette propriété JSON est un extra et devient une paire clé-valeur dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="0602a-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="0602a-117">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="0602a-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="0602a-118">Une propriété supplémentaire du JSON devient une paire clé-valeur, avec un tableau comme objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="0602a-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="0602a-119">Lorsque l’objet cible est sérialisé, les paires de valeurs de clés de données d’extension deviennent des propriétés JSON comme elles étaient dans le JSON entrant :</span><span class="sxs-lookup"><span data-stu-id="0602a-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="0602a-120">Notez que le `ExtensionData` nom de la propriété n’apparaît pas dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="0602a-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="0602a-121">Ce comportement permet au JSON d’effectuer un aller-retour sans perdre aucune donnée supplémentaire qui, sinon, ne serait pas désérialisée.</span><span class="sxs-lookup"><span data-stu-id="0602a-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="0602a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0602a-122">See also</span></span>

* [<span data-ttu-id="0602a-123">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="0602a-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="0602a-124">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="0602a-124">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="0602a-125">Activer la correspondance qui ne respecte pas la casse</span><span class="sxs-lookup"><span data-stu-id="0602a-125">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="0602a-126">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="0602a-126">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="0602a-127">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="0602a-127">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="0602a-128">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="0602a-128">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="0602a-129">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="0602a-129">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="0602a-130">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="0602a-130">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="0602a-131">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="0602a-131">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="0602a-132">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="0602a-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
