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
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83380135"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="49b4c-103">Sérialisation et désérialisation JSON (marshaling et démarshaling) dans .NET-vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="49b4c-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="49b4c-104">L' `System.Text.Json` espace de noms fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="49b4c-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="49b4c-105">La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="49b4c-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="49b4c-106">La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="49b4c-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="49b4c-107">La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire.</span><span class="sxs-lookup"><span data-stu-id="49b4c-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="49b4c-108">Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="49b4c-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="49b4c-109">Obtention de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="49b4c-109">How to get the library</span></span>

* <span data-ttu-id="49b4c-110">La bibliothèque est intégrée dans le cadre de l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="49b4c-110">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="49b4c-111">Pour les autres frameworks cibles, installez le [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) package NuGet.</span><span class="sxs-lookup"><span data-stu-id="49b4c-111">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="49b4c-112">Le package prend en charge :</span><span class="sxs-lookup"><span data-stu-id="49b4c-112">The package supports:</span></span>
  * <span data-ttu-id="49b4c-113">.NET Standard 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="49b4c-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="49b4c-114">.NET Framework 4.7.2 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="49b4c-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="49b4c-115">.NET Core 2,0, 2,1 et 2,2</span><span class="sxs-lookup"><span data-stu-id="49b4c-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="49b4c-116">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="49b4c-116">Additional resources</span></span>

* [<span data-ttu-id="49b4c-117">Comment utiliser la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="49b4c-117">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="49b4c-118">[Migration à partir deNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="49b4c-118">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="49b4c-119">Comment écrire des convertisseurs</span><span class="sxs-lookup"><span data-stu-id="49b4c-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="49b4c-120">[System.Text.Jsoncode source](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="49b4c-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="49b4c-121">[System.Text.JsonRéférence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="49b4c-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="49b4c-122">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="49b4c-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
