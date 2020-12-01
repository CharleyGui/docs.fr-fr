---
title: Comment utiliser des types immuables et des accesseurs non publics avec System.Text.Json
description: Découvrez comment utiliser des types immuables et des accesseurs non publics lors de la sérialisation et de la désérialisation de JSON dans .NET.
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
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439962"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a><span data-ttu-id="d7ae0-103">Comment utiliser des types immuables et des accesseurs non publics avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d7ae0-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="d7ae0-104">Dans cet article, vous allez apprendre à utiliser des types immuables, tels que des enregistrements, avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-104">In this article, you will learn how to use immutable types, such as Records, with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="d7ae0-105">Enregistrements et types immuables</span><span class="sxs-lookup"><span data-stu-id="d7ae0-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="d7ae0-106">`System.Text.Json` peut utiliser un constructeur paramétrable, ce qui rend possible la désérialisation d’une classe ou d’un struct immuable.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-106">`System.Text.Json` can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="d7ae0-107">Pour une classe, si le seul constructeur est un constructeur paramétrable, ce constructeur sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="d7ae0-108">Pour un struct ou une classe avec plusieurs constructeurs, spécifiez celui-ci à utiliser en appliquant l’attribut [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) .</span><span class="sxs-lookup"><span data-stu-id="d7ae0-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="d7ae0-109">Lorsque l’attribut n’est pas utilisé, un constructeur sans paramètre public est toujours utilisé, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="d7ae0-110">L’attribut peut uniquement être utilisé avec des constructeurs publics.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="d7ae0-111">L’exemple suivant utilise l' `[JsonConstructor]` attribut :</span><span class="sxs-lookup"><span data-stu-id="d7ae0-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="d7ae0-112">Les enregistrements en C# 9 sont également pris en charge, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d7ae0-112">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="d7ae0-113">Pour les types immuables, car tous leurs accesseurs set de propriété sont non publics, consultez la section suivante à propos des [accesseurs de propriété non publics](#non-public-property-accessors).</span><span class="sxs-lookup"><span data-stu-id="d7ae0-113">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="d7ae0-114">`JsonConstructorAttribute` et la prise en charge des enregistrements C# 9 ne sont pas disponibles dans .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-114">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="d7ae0-115">Accesseurs de propriété non publics</span><span class="sxs-lookup"><span data-stu-id="d7ae0-115">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="d7ae0-116">Pour activer l’utilisation d’un accesseur de propriété non public, utilisez l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d7ae0-116">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="d7ae0-117">Les accesseurs de propriété non publics ne sont pas pris en charge dans .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="d7ae0-117">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="d7ae0-118">Pour plus d’informations, consultez [l' Newtonsoft.Json article migrer à partir de](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="d7ae0-118">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="d7ae0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7ae0-119">See also</span></span>

* [<span data-ttu-id="d7ae0-120">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="d7ae0-120">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d7ae0-121">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="d7ae0-121">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="d7ae0-122">Activer la correspondance qui ne respecte pas la casse</span><span class="sxs-lookup"><span data-stu-id="d7ae0-122">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="d7ae0-123">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="d7ae0-123">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="d7ae0-124">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="d7ae0-124">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="d7ae0-125">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="d7ae0-125">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="d7ae0-126">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="d7ae0-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="d7ae0-127">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="d7ae0-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="d7ae0-128">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="d7ae0-128">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="d7ae0-129">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d7ae0-129">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
