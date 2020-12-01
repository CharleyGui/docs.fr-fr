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
ms.openlocfilehash: 4bd57d32120f51ffd1ff09c9817edbafa28a3f19
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439944"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="55a1d-103">Comment activer la correspondance des noms de propriétés ne respectant pas la casse avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="55a1d-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="55a1d-104">Dans cet article, vous allez apprendre à activer la correspondance des noms de propriété qui ne respectent pas la casse avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="55a1d-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="55a1d-105">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="55a1d-105">Case-insensitive property matching</span></span>

<span data-ttu-id="55a1d-106">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="55a1d-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="55a1d-107">Pour modifier ce comportement, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="55a1d-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="55a1d-108">Les [paramètres par défaut du Web](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="55a1d-108">The [web defaults](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="55a1d-109">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="55a1d-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="55a1d-110">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="55a1d-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="55a1d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55a1d-111">See also</span></span>

* [<span data-ttu-id="55a1d-112">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="55a1d-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="55a1d-113">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="55a1d-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="55a1d-114">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="55a1d-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="55a1d-115">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="55a1d-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="55a1d-116">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="55a1d-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="55a1d-117">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="55a1d-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="55a1d-118">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="55a1d-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="55a1d-119">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="55a1d-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="55a1d-120">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="55a1d-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="55a1d-121">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="55a1d-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
