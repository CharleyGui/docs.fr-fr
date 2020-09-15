---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065150"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="ea2b0-101">CA2015 : Ne pas définir de finaliseurs pour les types dérivés de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="ea2b0-101">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="ea2b0-102">La [règle de](/visualstudio/code-quality/ca2015) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-102">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="ea2b0-103">Il génère un avertissement de génération pour tous les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-103">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ea2b0-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ea2b0-104">Change description</span></span>

<span data-ttu-id="ea2b0-105">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="ea2b0-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="ea2b0-106">Plusieurs de ces règles sont activées par défaut, y compris [ca2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="ea2b0-106">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="ea2b0-107">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="ea2b0-108">Règle ca2015 signale les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-108">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="ea2b0-109">L’ajout d’un finaliseur à un type qui dérive de <xref:System.Buffers.MemoryManager%601> est probablement une indication d’un bogue.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-109">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="ea2b0-110">Elle suggère qu’une ressource native qui aurait pu être obtenue dans un est en cours de <xref:System.Span%601> nettoyage, éventuellement pendant qu’elle est toujours utilisée par le <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="ea2b0-110">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ea2b0-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ea2b0-111">Version introduced</span></span>

<span data-ttu-id="ea2b0-112">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="ea2b0-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ea2b0-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ea2b0-113">Recommended action</span></span>

- <span data-ttu-id="ea2b0-114">Supprimez la définition du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-114">Remove the finalizer definition.</span></span> <span data-ttu-id="ea2b0-115">Pour plus d’informations, consultez [ca2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="ea2b0-115">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="ea2b0-116">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="ea2b0-117">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="ea2b0-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="ea2b0-118">Category</span><span class="sxs-lookup"><span data-stu-id="ea2b0-118">Category</span></span>

<span data-ttu-id="ea2b0-119">Analyse du code</span><span class="sxs-lookup"><span data-stu-id="ea2b0-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ea2b0-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="ea2b0-120">Affected APIs</span></span>

<span data-ttu-id="ea2b0-121">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="ea2b0-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
