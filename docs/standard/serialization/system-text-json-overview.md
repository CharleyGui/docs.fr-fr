---
title: Sérialiser et désérialiser JSON à C# l’aide de-.net
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c05783963ba521109fb542f247ec9e62fdb5c2d9
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904641"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="83b4f-102">Sérialisation et désérialisation JSON (marshaling et démarshaling) dans .NET-vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="83b4f-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="83b4f-103">L’espace de noms `System.Text.Json` fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="83b4f-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="83b4f-104">La conception de la bibliothèque met l’accent sur des performances élevées et une allocation de mémoire faible sur un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="83b4f-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="83b4f-105">La prise en charge UTF-8 intégrée optimise le processus de lecture et d’écriture du texte JSON encodé au format UTF-8, qui est l’encodage le plus courant pour les données sur le Web et les fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="83b4f-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="83b4f-106">La bibliothèque fournit également des classes pour l’utilisation d’un modèle DOM (Document Object Model) en mémoire.</span><span class="sxs-lookup"><span data-stu-id="83b4f-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="83b4f-107">Cette fonctionnalité permet un accès en lecture seule aléatoire des éléments dans un fichier JSON ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="83b4f-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="83b4f-108">Obtention de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="83b4f-108">How to get the library</span></span>

* <span data-ttu-id="83b4f-109">La bibliothèque est intégrée dans le cadre de l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="83b4f-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="83b4f-110">Pour les autres frameworks cibles, installez le package NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="83b4f-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="83b4f-111">Le package prend en charge :</span><span class="sxs-lookup"><span data-stu-id="83b4f-111">The package supports:</span></span>
  * <span data-ttu-id="83b4f-112">.NET Standard 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="83b4f-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="83b4f-113">.NET Framework 4.7.2 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="83b4f-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="83b4f-114">.NET Core 2,0, 2,1 et 2,2</span><span class="sxs-lookup"><span data-stu-id="83b4f-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="83b4f-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="83b4f-115">Additional resources</span></span>

* [<span data-ttu-id="83b4f-116">Comment utiliser la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="83b4f-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="83b4f-117">Migration à partir de Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="83b4f-117">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="83b4f-118">Comment écrire des convertisseurs</span><span class="sxs-lookup"><span data-stu-id="83b4f-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="83b4f-119">Code source System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="83b4f-119">System.Text.Json source code</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [<span data-ttu-id="83b4f-120">Informations de référence sur l’API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="83b4f-120">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="83b4f-121">Informations de référence sur l’API System. Text. JSON. Serialization</span><span class="sxs-lookup"><span data-stu-id="83b4f-121">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
