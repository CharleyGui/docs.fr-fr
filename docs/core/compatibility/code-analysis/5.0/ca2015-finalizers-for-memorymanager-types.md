---
title: 'Modification avec rupture : ca2015 : ne définissez pas de finaliseurs pour les types dérivés de MemoryManager<T>'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2015.
ms.date: 09/03/2020
ms.openlocfilehash: 5d0ba0546b5a72363559f23713c8af4bb4e26e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760812"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="81f15-103">AVERTISSEMENT ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="81f15-103">Warning CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="81f15-104">La [règle de](/visualstudio/code-quality/ca2015) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="81f15-104">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="81f15-105">Il génère un avertissement de génération pour tous les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="81f15-105">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

## <a name="change-description"></a><span data-ttu-id="81f15-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="81f15-106">Change description</span></span>

<span data-ttu-id="81f15-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="81f15-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="81f15-108">Plusieurs de ces règles sont activées par défaut, y compris [ca2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="81f15-108">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="81f15-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="81f15-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="81f15-110">Règle ca2015 signale les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="81f15-110">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="81f15-111">L’ajout d’un finaliseur à un type qui dérive de <xref:System.Buffers.MemoryManager%601> est probablement une indication d’un bogue.</span><span class="sxs-lookup"><span data-stu-id="81f15-111">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="81f15-112">Elle suggère qu’une ressource native qui aurait pu être obtenue dans un est en cours de <xref:System.Span%601> nettoyage, éventuellement pendant qu’elle est toujours utilisée par le <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="81f15-112">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="81f15-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="81f15-113">Version introduced</span></span>

<span data-ttu-id="81f15-114">5.0</span><span class="sxs-lookup"><span data-stu-id="81f15-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="81f15-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="81f15-115">Recommended action</span></span>

- <span data-ttu-id="81f15-116">Supprimez la définition du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="81f15-116">Remove the finalizer definition.</span></span> <span data-ttu-id="81f15-117">Pour plus d’informations, consultez [ca2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="81f15-117">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="81f15-118">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="81f15-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="81f15-119">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="81f15-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="81f15-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="81f15-120">Affected APIs</span></span>

<span data-ttu-id="81f15-121">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="81f15-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
