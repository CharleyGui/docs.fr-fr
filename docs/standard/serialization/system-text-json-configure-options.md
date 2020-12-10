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
ms.openlocfilehash: 5f32e1369e58dd9550f28abc822f187dee46c022
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009831"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="c0b0a-103">Comment instancier des instances JsonSerializerOptions avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c0b0a-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="c0b0a-104">Cet article explique comment éviter les problèmes de performances lorsque vous utilisez <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="c0b0a-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="c0b0a-105">Il montre également comment utiliser les constructeurs paramétrables qui sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="c0b0a-106">Réutiliser les instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="c0b0a-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="c0b0a-107">Si vous utilisez `JsonSerializerOptions` à plusieurs reprises avec les mêmes options, ne créez pas une nouvelle `JsonSerializerOptions` instance à chaque fois que vous l’utilisez.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="c0b0a-108">Réutilisez la même instance pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="c0b0a-109">Ce guide s’applique au code que vous écrivez pour les convertisseurs personnalisés et lorsque vous appelez <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> ou <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c0b0a-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c0b0a-110">Le code suivant illustre la baisse des performances pour l’utilisation de nouvelles instances d’options.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="c0b0a-111">Le code précédent sérialise un petit objet 100 000 fois à l’aide de la même instance d’options.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="c0b0a-112">Ensuite, il sérialise le même objet le même nombre de fois et crée à chaque fois une nouvelle instance d’options.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="c0b0a-113">Une différence de temps d’exécution classique est de 190 par rapport à 40 140 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="c0b0a-114">La différence est encore plus importante si vous augmentez le nombre d’itérations.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="c0b0a-115">Le sérialiseur subit une phase de préchauffage pendant la première sérialisation de chaque type dans le graphique d’objets quand une nouvelle instance d’options lui est passée.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="c0b0a-116">Cela implique la création d’un cache de métadonnées qui est nécessaire pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="c0b0a-117">Les métadonnées incluent des délégués aux accesseurs get de propriété, aux Setters, aux arguments de constructeur, aux attributs spécifiés, etc.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="c0b0a-118">Ce cache de métadonnées est stocké dans l’instance options.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="c0b0a-119">Le même processus de préchauffage et le même cache s’appliquent à la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="c0b0a-120">La taille du cache de métadonnées dans une `JsonSerializerOptions` instance dépend du nombre de types à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="c0b0a-121">Si vous passez de nombreux types (par exemple, des types générés dynamiquement) au sérialiseur, la taille du cache continue de croître et peut finir par provoquer un `OutOfMemoryException` .</span><span class="sxs-lookup"><span data-stu-id="c0b0a-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="c0b0a-122">Copier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="c0b0a-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="c0b0a-123">Il existe un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) qui vous permet de créer une nouvelle instance avec les mêmes options qu’une instance existante, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c0b0a-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="c0b0a-124">Un `JsonSerializerOptions` constructeur qui prend une instance existante n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="c0b0a-125">Valeurs par défaut Web pour JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="c0b0a-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="c0b0a-126">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="c0b0a-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="c0b0a-127">Il y a un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults) ? View = net-5,0&Preserve-View = true) qui vous permet de créer une nouvelle instance avec les options par défaut que ASP.NET Core utilise pour Web Apps, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c0b0a-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="c0b0a-128">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="c0b0a-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="c0b0a-129">Un `JsonSerializerOptions` constructeur qui spécifie un jeu de valeurs par défaut n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c0b0a-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="c0b0a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0b0a-130">See also</span></span>

* [<span data-ttu-id="c0b0a-131">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="c0b0a-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="c0b0a-132">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="c0b0a-132">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="c0b0a-133">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="c0b0a-133">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="c0b0a-134">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="c0b0a-134">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="c0b0a-135">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="c0b0a-135">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="c0b0a-136">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="c0b0a-136">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="c0b0a-137">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="c0b0a-137">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="c0b0a-138">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="c0b0a-138">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="c0b0a-139">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="c0b0a-139">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="c0b0a-140">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="c0b0a-140">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="c0b0a-141">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c0b0a-141">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="c0b0a-142">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="c0b0a-142">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="c0b0a-143">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="c0b0a-143">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="c0b0a-144">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="c0b0a-144">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="c0b0a-145">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b0a-145">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="c0b0a-146">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="c0b0a-146">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="c0b0a-147">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="c0b0a-147">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
