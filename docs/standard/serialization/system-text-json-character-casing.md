---
title: Comment activer la correspondance des noms de propriétés ne respectant pas la casse avec System.Text.Json
description: Découvrez comment activer la correspondance des noms de propriété ne respectant pas la casse lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3e2fb8cbdd35e772b5e97c731199f69aa834bd0a
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009740"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="d7d86-103">Comment activer la correspondance des noms de propriétés ne respectant pas la casse avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d7d86-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="d7d86-104">Dans cet article, vous allez apprendre à activer la correspondance des noms de propriété qui ne respectent pas la casse avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d7d86-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="d7d86-105">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="d7d86-105">Case-insensitive property matching</span></span>

<span data-ttu-id="d7d86-106">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="d7d86-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="d7d86-107">Pour modifier ce comportement, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="d7d86-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="d7d86-108">La [valeur par défaut du Web](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="d7d86-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="d7d86-109">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="d7d86-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="d7d86-110">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="d7d86-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="d7d86-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7d86-111">See also</span></span>

* [<span data-ttu-id="d7d86-112">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="d7d86-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d7d86-113">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="d7d86-113">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="d7d86-114">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="d7d86-114">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="d7d86-115">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="d7d86-115">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="d7d86-116">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="d7d86-116">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="d7d86-117">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="d7d86-117">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="d7d86-118">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="d7d86-118">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="d7d86-119">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="d7d86-119">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="d7d86-120">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="d7d86-120">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="d7d86-121">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="d7d86-121">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="d7d86-122">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d7d86-122">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="d7d86-123">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="d7d86-123">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="d7d86-124">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="d7d86-124">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="d7d86-125">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="d7d86-125">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="d7d86-126">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="d7d86-126">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="d7d86-127">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d7d86-127">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="d7d86-128">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="d7d86-128">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
