---
title: 'Modification avec rupture : modifications du comportement des API liées à l’assembly pour le format de publication à fichier unique'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où plusieurs API liées à l’emplacement des fichiers d’un assembly ont des modifications de comportement lorsqu’elles sont appelées dans un format de publication à fichier unique.
ms.date: 11/01/2020
ms.openlocfilehash: d77e30318040c8298065073a41caab56f2ca3875
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761022"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="590f5-103">Modifications du comportement des API liées à l’assembly pour le format de publication à fichier unique</span><span class="sxs-lookup"><span data-stu-id="590f5-103">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="590f5-104">Plusieurs API liées à l’emplacement des fichiers d’un assembly ont des modifications de comportement lorsqu’elles sont appelées dans un format de publication à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="590f5-104">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

## <a name="change-description"></a><span data-ttu-id="590f5-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="590f5-105">Change description</span></span>

<span data-ttu-id="590f5-106">Dans la publication de fichier unique pour .NET 5,0 et versions ultérieures, les assemblys regroupés sont chargés à partir de la mémoire au lieu d’être extraits sur le disque.</span><span class="sxs-lookup"><span data-stu-id="590f5-106">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="590f5-107">Pour les applications publiées sur un seul fichier, cela signifie que certaines API liées à l’emplacement retournent des valeurs différentes sur .NET 5,0 et versions ultérieures par rapport aux versions précédentes de .NET.</span><span class="sxs-lookup"><span data-stu-id="590f5-107">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="590f5-108">Les modifications sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="590f5-108">The changes are as follows:</span></span>

| <span data-ttu-id="590f5-109">API</span><span class="sxs-lookup"><span data-stu-id="590f5-109">API</span></span> | <span data-ttu-id="590f5-110">Versions précédentes</span><span class="sxs-lookup"><span data-stu-id="590f5-110">Previous versions</span></span> | <span data-ttu-id="590f5-111">.NET 5,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="590f5-111">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="590f5-112">Retourne le chemin du fichier DLL extrait</span><span class="sxs-lookup"><span data-stu-id="590f5-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="590f5-113">Retourne une chaîne vide pour les assemblys regroupés</span><span class="sxs-lookup"><span data-stu-id="590f5-113">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="590f5-114">Retourne le chemin du fichier DLL extrait</span><span class="sxs-lookup"><span data-stu-id="590f5-114">Returns extracted DLL file path</span></span> | <span data-ttu-id="590f5-115">Lève une exception pour les assemblys regroupés</span><span class="sxs-lookup"><span data-stu-id="590f5-115">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="590f5-116">Retourne `null` pour les assemblys regroupés</span><span class="sxs-lookup"><span data-stu-id="590f5-116">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="590f5-117">Lève une exception pour les assemblys regroupés</span><span class="sxs-lookup"><span data-stu-id="590f5-117">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="590f5-118">La valeur est le nom de la DLL de point d’entrée</span><span class="sxs-lookup"><span data-stu-id="590f5-118">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="590f5-119">La valeur est le nom de l’exécutable hôte</span><span class="sxs-lookup"><span data-stu-id="590f5-119">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="590f5-120">La valeur est le répertoire d’extraction temporaire</span><span class="sxs-lookup"><span data-stu-id="590f5-120">Value is the temporary extraction directory</span></span> | <span data-ttu-id="590f5-121">La valeur est le répertoire conteneur du fichier exécutable de l’hôte</span><span class="sxs-lookup"><span data-stu-id="590f5-121">Value is the containing directory of the host executable</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="590f5-122">Version introduite</span><span class="sxs-lookup"><span data-stu-id="590f5-122">Version introduced</span></span>

<span data-ttu-id="590f5-123">5.0</span><span class="sxs-lookup"><span data-stu-id="590f5-123">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="590f5-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="590f5-124">Recommended action</span></span>

<span data-ttu-id="590f5-125">Évitez les dépendances sur l’emplacement de fichier des assemblys lors de la publication sous la forme d’un fichier unique.</span><span class="sxs-lookup"><span data-stu-id="590f5-125">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="590f5-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="590f5-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
