---
title: Sérialiser et désérialiser JSON à l’aide de C#-.NET
description: Cette vue d’ensemble décrit les System.Text.Json fonctionnalités d’espace de noms pour sérialiser vers et désérialiser à partir de JSON dans .net.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: cb5c15c2a5c336e2d5b4a3754fa7a02a370602f3
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009883"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="6e0f9-103">Sérialisation et désérialisation JSON (marshaling et démarshaling) dans .NET-vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="6e0f9-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="6e0f9-104">L' `System.Text.Json` espace de noms fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="6e0f9-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="6e0f9-105">La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="6e0f9-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="6e0f9-106">La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="6e0f9-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="6e0f9-107">La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire.</span><span class="sxs-lookup"><span data-stu-id="6e0f9-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="6e0f9-108">Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="6e0f9-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="6e0f9-109">Obtention de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="6e0f9-109">How to get the library</span></span>

* <span data-ttu-id="6e0f9-110">La bibliothèque est intégrée dans le cadre de l’infrastructure partagée pour .NET Core 3,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6e0f9-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="6e0f9-111">Pour les versions antérieures du Framework, installez le [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) package NuGet.</span><span class="sxs-lookup"><span data-stu-id="6e0f9-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="6e0f9-112">Le package prend en charge :</span><span class="sxs-lookup"><span data-stu-id="6e0f9-112">The package supports:</span></span>

  * <span data-ttu-id="6e0f9-113">.NET Standard 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6e0f9-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="6e0f9-114">.NET Framework 4.7.2 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6e0f9-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="6e0f9-115">.NET Core 2,0, 2,1 et 2,2</span><span class="sxs-lookup"><span data-stu-id="6e0f9-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6e0f9-116">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="6e0f9-116">Additional resources</span></span>

* [<span data-ttu-id="6e0f9-117">Comment utiliser la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="6e0f9-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="6e0f9-118">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="6e0f9-118">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="6e0f9-119">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="6e0f9-119">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="6e0f9-120">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="6e0f9-120">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="6e0f9-121">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="6e0f9-121">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="6e0f9-122">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="6e0f9-122">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="6e0f9-123">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="6e0f9-123">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="6e0f9-124">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="6e0f9-124">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="6e0f9-125">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="6e0f9-125">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="6e0f9-126">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="6e0f9-126">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="6e0f9-127">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="6e0f9-127">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="6e0f9-128">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="6e0f9-128">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="6e0f9-129">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="6e0f9-129">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="6e0f9-130">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="6e0f9-130">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="6e0f9-131">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e0f9-131">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="6e0f9-132">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="6e0f9-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="6e0f9-133">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="6e0f9-133">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
