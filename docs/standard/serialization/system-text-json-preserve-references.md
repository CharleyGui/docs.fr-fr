---
title: Comment conserver des références avec System.Text.Json
description: Apprenez à préserver les références et à gérer les références circulaires lors de la sérialisation et de la désérialisation de JSON dans .NET.
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
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439968"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="7e8e8-103">Comment gérer des références circulaires avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="7e8e8-103">How to handle circular references with System.Text.Json</span></span>

<span data-ttu-id="7e8e8-104">Dans cet article, vous allez apprendre à gérer des références circulaires avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-104">In this article, you will learn how to handle circular references with the `System.Text.Json` namespace.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="7e8e8-105">Conserver les références et gérer les références circulaires</span><span class="sxs-lookup"><span data-stu-id="7e8e8-105">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="7e8e8-106">Pour conserver les références et gérer les références circulaires, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="7e8e8-106">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="7e8e8-107">Ce paramètre entraîne le comportement suivant :</span><span class="sxs-lookup"><span data-stu-id="7e8e8-107">This setting causes the following behavior:</span></span>

* <span data-ttu-id="7e8e8-108">Lors de la sérialisation :</span><span class="sxs-lookup"><span data-stu-id="7e8e8-108">On serialize:</span></span>

  <span data-ttu-id="7e8e8-109">Lors de l’écriture de types complexes, le sérialiseur écrit également des propriétés de métadonnées ( `$id` , `$values` et `$ref` ).</span><span class="sxs-lookup"><span data-stu-id="7e8e8-109">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="7e8e8-110">Lors de la désérialisation :</span><span class="sxs-lookup"><span data-stu-id="7e8e8-110">On deserialize:</span></span>

  <span data-ttu-id="7e8e8-111">Les métadonnées sont attendues (même si elles ne sont pas obligatoires) et le désérialiseur essaie de le comprendre.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-111">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="7e8e8-112">Le code suivant illustre l’utilisation du `Preserve` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-112">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="7e8e8-113">Cette fonctionnalité ne peut pas être utilisée pour conserver des types valeur ou des types immuables.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-113">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="7e8e8-114">Lors de la désérialisation, l’instance d’un type immuable est créée après la lecture de la charge utile entière.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-114">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="7e8e8-115">Il serait donc impossible de désérialiser la même instance si une référence à celle-ci apparaît dans la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-115">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="7e8e8-116">Pour les types valeur, les types immuables et les tableaux, aucune métadonnée de référence n’est sérialisée.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-116">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="7e8e8-117">Lors de la désérialisation, une exception est levée si `$ref` ou `$id` est trouvé.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-117">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="7e8e8-118">Toutefois, les types valeur ignorent `$id` (et, `$values` dans le cas des collections) qu’il est possible de désérialiser les charges utiles qui ont été sérialisées à l’aide de Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="7e8e8-118">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="7e8e8-119">Newtonsoft.Json sérialise les métadonnées de ces types.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-119">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="7e8e8-120">Pour déterminer si les objets sont égaux, System.Text.Json utilise <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , qui utilise l’égalité <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> de référence () au lieu de l’égalité des valeurs (lors de la comparaison de <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> deux instances d’objet.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-120">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="7e8e8-121">Pour plus d’informations sur la façon dont les références sont sérialisées et désérialisées, consultez <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7e8e8-121">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="7e8e8-122">La <xref:System.Text.Json.Serialization.ReferenceResolver> classe définit le comportement de préservation des références sur la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-122">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="7e8e8-123">Créez une classe dérivée pour spécifier un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-123">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="7e8e8-124">Pour obtenir un exemple, consultez [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="7e8e8-124">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="7e8e8-125">System.Text.Json dans .NET Core 3,1 prend uniquement en charge la sérialisation par valeur et lève une exception pour les références circulaires.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-125">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="7e8e8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e8e8-126">See also</span></span>

* [<span data-ttu-id="7e8e8-127">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="7e8e8-127">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="7e8e8-128">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="7e8e8-128">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="7e8e8-129">Activer la correspondance qui ne respecte pas la casse</span><span class="sxs-lookup"><span data-stu-id="7e8e8-129">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="7e8e8-130">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="7e8e8-130">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="7e8e8-131">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="7e8e8-131">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="7e8e8-132">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="7e8e8-132">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="7e8e8-133">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="7e8e8-133">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="7e8e8-134">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="7e8e8-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="7e8e8-135">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="7e8e8-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="7e8e8-136">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="7e8e8-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
