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
ms.openlocfilehash: 2d663ac8c1c15d61959a62c40d9a3b0993484032
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599074"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="9fefb-103">Comment activer la correspondance des noms de propriétés ne respectant pas la casse avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="9fefb-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="9fefb-104">Dans cet article, vous allez apprendre à activer la correspondance des noms de propriété qui ne respectent pas la casse avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9fefb-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="9fefb-105">Correspondance de propriété ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="9fefb-105">Case-insensitive property matching</span></span>

<span data-ttu-id="9fefb-106">Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="9fefb-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="9fefb-107">Pour modifier ce comportement, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="9fefb-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="9fefb-108">La [valeur par défaut du Web](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="9fefb-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="9fefb-109">Voici un exemple de JSON avec les noms de propriété de casse mixte.</span><span class="sxs-lookup"><span data-stu-id="9fefb-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="9fefb-110">Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="9fefb-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="9fefb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fefb-111">See also</span></span>

* [<span data-ttu-id="9fefb-112">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="9fefb-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9fefb-113">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="9fefb-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="9fefb-114">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="9fefb-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="9fefb-115">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="9fefb-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="9fefb-116">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="9fefb-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="9fefb-117">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="9fefb-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="9fefb-118">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="9fefb-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="9fefb-119">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="9fefb-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="9fefb-120">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="9fefb-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="9fefb-121">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="9fefb-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
