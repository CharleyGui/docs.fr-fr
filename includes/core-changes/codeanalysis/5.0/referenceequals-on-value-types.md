---
ms.openlocfilehash: b01424c63d6e7956127bf889c53422b60ba2f219
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598084"
---
### <a name="ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="24932-101">CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur</span><span class="sxs-lookup"><span data-stu-id="24932-101">CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="24932-102">La [règle de](/visualstudio/code-quality/ca2013) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="24932-102">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="24932-103">Il génère un avertissement de génération pour tout code où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité.</span><span class="sxs-lookup"><span data-stu-id="24932-103">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

#### <a name="change-description"></a><span data-ttu-id="24932-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="24932-104">Change description</span></span>

<span data-ttu-id="24932-105">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="24932-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="24932-106">Plusieurs de ces règles sont activées par défaut, y compris [ca2013](/visualstudio/code-quality/ca2013).</span><span class="sxs-lookup"><span data-stu-id="24932-106">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="24932-107">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="24932-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="24932-108">La règle ca2013 recherche des instances où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité.</span><span class="sxs-lookup"><span data-stu-id="24932-108">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="24932-109">La comparaison des types valeur pour l’égalité de cette façon peut entraîner des résultats incorrects, car les valeurs sont converties avant d’être comparées.</span><span class="sxs-lookup"><span data-stu-id="24932-109">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="24932-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> retourne `false` même si les valeurs comparées représentent la même instance d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="24932-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24932-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="24932-111">Version introduced</span></span>

<span data-ttu-id="24932-112">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="24932-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24932-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="24932-113">Recommended action</span></span>

- <span data-ttu-id="24932-114">Modifiez le code pour utiliser un opérateur d’égalité approprié, tel que `==` .</span><span class="sxs-lookup"><span data-stu-id="24932-114">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="24932-115">Vous ne devez pas supprimer cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="24932-115">You should not suppress this warning.</span></span>

- <span data-ttu-id="24932-116">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="24932-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="24932-117">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="24932-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="24932-118">Category</span><span class="sxs-lookup"><span data-stu-id="24932-118">Category</span></span>

<span data-ttu-id="24932-119">Analyse du code</span><span class="sxs-lookup"><span data-stu-id="24932-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24932-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="24932-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

-->
