---
title: Comment conserver des références avec System.Text.Json
description: Apprenez à préserver les références et à gérer les références circulaires lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d358c953c0979ca097c080fcd750d5ef95b07de0
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008732"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="3c910-103">Comment conserver des références et gérer des références circulaires avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3c910-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="3c910-104">Pour conserver les références et gérer les références circulaires, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="3c910-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="3c910-105">Ce paramètre entraîne le comportement suivant :</span><span class="sxs-lookup"><span data-stu-id="3c910-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="3c910-106">Lors de la sérialisation :</span><span class="sxs-lookup"><span data-stu-id="3c910-106">On serialize:</span></span>

  <span data-ttu-id="3c910-107">Lors de l’écriture de types complexes, le sérialiseur écrit également des propriétés de métadonnées ( `$id` , `$values` et `$ref` ).</span><span class="sxs-lookup"><span data-stu-id="3c910-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="3c910-108">Lors de la désérialisation :</span><span class="sxs-lookup"><span data-stu-id="3c910-108">On deserialize:</span></span>

  <span data-ttu-id="3c910-109">Les métadonnées sont attendues (même si elles ne sont pas obligatoires) et le désérialiseur essaie de le comprendre.</span><span class="sxs-lookup"><span data-stu-id="3c910-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="3c910-110">Le code suivant illustre l’utilisation du `Preserve` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3c910-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="3c910-111">Cette fonctionnalité ne peut pas être utilisée pour conserver des types valeur ou des types immuables.</span><span class="sxs-lookup"><span data-stu-id="3c910-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="3c910-112">Lors de la désérialisation, l’instance d’un type immuable est créée après la lecture de la charge utile entière.</span><span class="sxs-lookup"><span data-stu-id="3c910-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="3c910-113">Il serait donc impossible de désérialiser la même instance si une référence à celle-ci apparaît dans la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="3c910-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="3c910-114">Pour les types valeur, les types immuables et les tableaux, aucune métadonnée de référence n’est sérialisée.</span><span class="sxs-lookup"><span data-stu-id="3c910-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="3c910-115">Lors de la désérialisation, une exception est levée si `$ref` ou `$id` est trouvé.</span><span class="sxs-lookup"><span data-stu-id="3c910-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="3c910-116">Toutefois, les types valeur ignorent `$id` (et, `$values` dans le cas des collections) qu’il est possible de désérialiser les charges utiles qui ont été sérialisées à l’aide de Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="3c910-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="3c910-117">Newtonsoft.Json sérialise les métadonnées de ces types.</span><span class="sxs-lookup"><span data-stu-id="3c910-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="3c910-118">Pour déterminer si les objets sont égaux, System.Text.Json utilise <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , qui utilise l’égalité <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> de référence () au lieu de l’égalité des valeurs (lors de la comparaison de <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> deux instances d’objet.</span><span class="sxs-lookup"><span data-stu-id="3c910-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="3c910-119">Pour plus d’informations sur la façon dont les références sont sérialisées et désérialisées, consultez <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3c910-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3c910-120">La <xref:System.Text.Json.Serialization.ReferenceResolver> classe définit le comportement de préservation des références sur la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="3c910-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="3c910-121">Créez une classe dérivée pour spécifier un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3c910-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="3c910-122">Pour obtenir un exemple, consultez [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="3c910-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="3c910-123">System.Text.Json dans .NET Core 3,1 prend uniquement en charge la sérialisation par valeur et lève une exception pour les références circulaires.</span><span class="sxs-lookup"><span data-stu-id="3c910-123">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="3c910-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c910-124">See also</span></span>

* [<span data-ttu-id="3c910-125">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="3c910-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="3c910-126">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="3c910-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="3c910-127">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="3c910-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="3c910-128">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="3c910-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="3c910-129">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="3c910-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="3c910-130">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="3c910-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="3c910-131">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="3c910-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="3c910-132">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="3c910-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="3c910-133">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="3c910-133">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="3c910-134">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="3c910-134">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="3c910-135">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3c910-135">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="3c910-136">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="3c910-136">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="3c910-137">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="3c910-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="3c910-138">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="3c910-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="3c910-139">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="3c910-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="3c910-140">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3c910-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="3c910-141">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="3c910-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
