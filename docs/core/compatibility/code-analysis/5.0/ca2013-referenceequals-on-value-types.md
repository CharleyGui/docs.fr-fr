---
title: 'Modification avec rupture : ca2013 : n’utilisez pas ReferenceEquals avec les types valeur'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2013.
ms.date: 09/03/2020
ms.openlocfilehash: ca2b845427eff547b996b577394c6859e30f50bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760816"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="63695-103">AVERTISSEMENT ca2013 : n’utilisez pas ReferenceEquals avec les types valeur</span><span class="sxs-lookup"><span data-stu-id="63695-103">Warning CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="63695-104">La [règle de](/visualstudio/code-quality/ca2013) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="63695-104">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="63695-105">Il génère un avertissement de génération pour tout code où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité.</span><span class="sxs-lookup"><span data-stu-id="63695-105">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

## <a name="change-description"></a><span data-ttu-id="63695-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="63695-106">Change description</span></span>

<span data-ttu-id="63695-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="63695-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="63695-108">Plusieurs de ces règles sont activées par défaut, y compris [ca2013](/visualstudio/code-quality/ca2013).</span><span class="sxs-lookup"><span data-stu-id="63695-108">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="63695-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="63695-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="63695-110">La règle ca2013 recherche des instances où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité.</span><span class="sxs-lookup"><span data-stu-id="63695-110">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="63695-111">La comparaison des types valeur pour l’égalité de cette façon peut entraîner des résultats incorrects, car les valeurs sont converties avant d’être comparées.</span><span class="sxs-lookup"><span data-stu-id="63695-111">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="63695-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> retourne `false` même si les valeurs comparées représentent la même instance d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="63695-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="63695-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="63695-113">Version introduced</span></span>

<span data-ttu-id="63695-114">5.0</span><span class="sxs-lookup"><span data-stu-id="63695-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="63695-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="63695-115">Recommended action</span></span>

- <span data-ttu-id="63695-116">Modifiez le code pour utiliser un opérateur d’égalité approprié, tel que `==` .</span><span class="sxs-lookup"><span data-stu-id="63695-116">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="63695-117">Vous ne devez pas supprimer cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="63695-117">You should not suppress this warning.</span></span>

- <span data-ttu-id="63695-118">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="63695-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="63695-119">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="63695-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="63695-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="63695-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
