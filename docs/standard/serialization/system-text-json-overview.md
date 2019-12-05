---
title: Sérialiser et désérialiser JSON à C# l’aide de-.net
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b43c3f6fd8ca56aaa99fffd40317920ee7600a2c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802711"
---
# <a name="json-serialization-in-net---overview"></a><span data-ttu-id="efa8f-102">Sérialisation JSON dans .NET-vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="efa8f-102">JSON serialization in .NET - overview</span></span>

<span data-ttu-id="efa8f-103">L’espace de noms `System.Text.Json` fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="efa8f-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="efa8f-104">La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="efa8f-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="efa8f-105">La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="efa8f-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="efa8f-106">La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire.</span><span class="sxs-lookup"><span data-stu-id="efa8f-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="efa8f-107">Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="efa8f-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="efa8f-108">Obtention de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="efa8f-108">How to get the library</span></span>

* <span data-ttu-id="efa8f-109">La bibliothèque est intégrée dans le cadre de l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="efa8f-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="efa8f-110">Pour les autres frameworks cibles, installez le package NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="efa8f-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="efa8f-111">Le package prend en charge :</span><span class="sxs-lookup"><span data-stu-id="efa8f-111">The package supports:</span></span>
  * <span data-ttu-id="efa8f-112">.NET Standard 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="efa8f-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="efa8f-113">.NET Framework 4.6.1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="efa8f-113">.NET Framework 4.6.1 and later versions</span></span>
  * <span data-ttu-id="efa8f-114">.NET Core 2,0, 2,1 et 2,2</span><span class="sxs-lookup"><span data-stu-id="efa8f-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="efa8f-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="efa8f-115">Additional resources</span></span>

* [<span data-ttu-id="efa8f-116">Comment utiliser la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="efa8f-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="efa8f-117">Code source</span><span class="sxs-lookup"><span data-stu-id="efa8f-117">Source code</span></span>](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [<span data-ttu-id="efa8f-118">Informations de référence sur les API</span><span class="sxs-lookup"><span data-stu-id="efa8f-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="efa8f-119">Feuille de route</span><span class="sxs-lookup"><span data-stu-id="efa8f-119">Roadmap</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="efa8f-120">GitHub problèmes dans le référentiel dotnet/corefx</span><span class="sxs-lookup"><span data-stu-id="efa8f-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="efa8f-121">Discussion sur le développement de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="efa8f-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [<span data-ttu-id="efa8f-122">Tous les problèmes liés à System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="efa8f-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="efa8f-123">Problèmes relatifs à System. Text. JSON étiquetés JSON-fonctionnalité-doc</span><span class="sxs-lookup"><span data-stu-id="efa8f-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/runtime/labels/json-functionality-doc)
