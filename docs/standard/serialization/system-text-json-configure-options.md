---
title: Comment instancier JsonSerializerOptions avec System.Text.Json
description: Découvrez comment instancier des instances JsonSerializerOptions en copiant des instances existantes ou avec des valeurs par défaut Web.
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440002"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="71a80-103">Comment instancier des instances JsonSerializerOptions avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="71a80-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="71a80-104">Dans cet article, vous allez apprendre à instancier des <xref:System.Text.Json.JsonSerializerOptions> instances en copiant des instances existantes ou avec des valeurs par défaut Web.</span><span class="sxs-lookup"><span data-stu-id="71a80-104">In this article, you'll learn how to instantiate <xref:System.Text.Json.JsonSerializerOptions> instances by copying existing instances or with web defaults.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="71a80-105">Copier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="71a80-105">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="71a80-106">Il existe un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) qui vous permet de créer une nouvelle instance avec les mêmes options qu’une instance existante, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="71a80-106">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="71a80-107">Un `JsonSerializerOptions` constructeur qui prend une instance existante n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="71a80-107">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="71a80-108">Valeurs par défaut Web pour JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="71a80-108">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="71a80-109">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="71a80-109">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="71a80-110">Il y a un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults) ? View = net-5,0&Preserve-View = true) qui vous permet de créer une nouvelle instance avec les options par défaut que ASP.NET Core utilise pour Web Apps, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="71a80-110">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="71a80-111">Voici les options qui ont des valeurs par défaut différentes pour les applications Web :</span><span class="sxs-lookup"><span data-stu-id="71a80-111">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="71a80-112">Un `JsonSerializerOptions` constructeur qui spécifie un jeu de valeurs par défaut n’est pas disponible dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="71a80-112">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="71a80-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71a80-113">See also</span></span>

* [<span data-ttu-id="71a80-114">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="71a80-114">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="71a80-115">Activer la correspondance qui ne respecte pas la casse</span><span class="sxs-lookup"><span data-stu-id="71a80-115">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="71a80-116">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="71a80-116">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="71a80-117">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="71a80-117">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="71a80-118">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="71a80-118">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="71a80-119">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="71a80-119">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="71a80-120">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="71a80-120">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="71a80-121">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="71a80-121">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="71a80-122">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="71a80-122">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="71a80-123">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="71a80-123">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
