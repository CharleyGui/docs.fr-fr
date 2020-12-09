---
title: Comment instancier JsonSerializerOptions avec System.Text.Json
description: Apprenez à éviter les problèmes de performances et à utiliser les constructeurs disponibles pour les instances JsonSerializerOptions.
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 257c99e117dea9a9b3ab2352c9a442d71a2cdabd
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918552"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="4e221-103">Comment instancier des instances JsonSerializerOptions avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4e221-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="4e221-104">Cet article explique comment éviter les problèmes de performances lorsque vous utilisez <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="4e221-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="4e221-105">Il montre également comment utiliser les constructeurs paramétrables qui sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="4e221-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="4e221-106">Réutiliser les instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="4e221-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="4e221-107">Si vous utilisez `JsonSerializerOptions` à plusieurs reprises avec les mêmes options, ne créez pas une nouvelle `JsonSerializerOptions` instance à chaque fois que vous l’utilisez.</span><span class="sxs-lookup"><span data-stu-id="4e221-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="4e221-108">Réutilisez la même instance pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="4e221-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="4e221-109">Ce guide s’applique au code que vous écrivez pour les convertisseurs personnalisés et lorsque vous appelez <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> ou <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4e221-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4e221-110">Le code suivant illustre la baisse des performances pour l’utilisation de nouvelles instances d’options.</span><span class="sxs-lookup"><span data-stu-id="4e221-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="4e221-111">Le code précédent sérialise un petit objet 100 000 fois à l’aide de la même instance d’options.</span><span class="sxs-lookup"><span data-stu-id="4e221-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="4e221-112">Ensuite, il sérialise le même objet le même nombre de fois et crée à chaque fois une nouvelle instance d’options.</span><span class="sxs-lookup"><span data-stu-id="4e221-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="4e221-113">Une différence de temps d’exécution classique est de 190 par rapport à 40 140 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="4e221-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="4e221-114">La différence est encore plus importante si vous augmentez le nombre d’itérations.</span><span class="sxs-lookup"><span data-stu-id="4e221-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="4e221-115">Le sérialiseur subit une phase de préchauffage pendant la première sérialisation de chaque type dans le graphique d’objets quand une nouvelle instance d’options lui est passée.</span><span class="sxs-lookup"><span data-stu-id="4e221-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="4e221-116">Cela implique la création d’un cache de métadonnées qui est nécessaire pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="4e221-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="4e221-117">Les métadonnées incluent des délégués aux accesseurs get de propriété, aux Setters, aux arguments de constructeur, aux attributs spécifiés, etc.</span><span class="sxs-lookup"><span data-stu-id="4e221-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="4e221-118">Ce cache de métadonnées est stocké dans l’instance options.</span><span class="sxs-lookup"><span data-stu-id="4e221-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="4e221-119">Le même processus de préchauffage et le même cache s’appliquent à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="4e221-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="4e221-120">La taille du cache de métadonnées dans une `JsonSerializerOptions` instance dépend du nombre de types à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="4e221-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="4e221-121">Si vous passez de nombreux types (par exemple, des types générés dynamiquement) au sérialiseur, la taille du cache continue de croître et peut finir par provoquer un `OutOfMemoryException` .</span><span class="sxs-lookup"><span data-stu-id="4e221-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="4e221-122">Copier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="4e221-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="4e221-123">Il existe un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) qui vous permet de créer une nouvelle instance avec les mêmes options qu’une instance existante, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4e221-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="4e221-124">Un `JsonSerializerOptions` constructeur qui prend une instance existante n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4e221-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="4e221-125">Valeurs par défaut Web pour JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="4e221-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="4e221-126">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="4e221-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="4e221-127">Il y a un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults) ? View = net-5,0&Preserve-View = true) qui vous permet de créer une nouvelle instance avec les options par défaut que ASP.NET Core utilise pour Web Apps, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4e221-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="4e221-128">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="4e221-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="4e221-129">Un `JsonSerializerOptions` constructeur qui spécifie un jeu de valeurs par défaut n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4e221-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="4e221-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e221-130">See also</span></span>

* [<span data-ttu-id="4e221-131">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="4e221-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="4e221-132">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="4e221-132">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="4e221-133">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="4e221-133">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="4e221-134">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="4e221-134">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="4e221-135">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="4e221-135">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="4e221-136">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="4e221-136">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="4e221-137">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="4e221-137">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="4e221-138">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="4e221-138">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="4e221-139">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="4e221-139">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="4e221-140">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="4e221-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
