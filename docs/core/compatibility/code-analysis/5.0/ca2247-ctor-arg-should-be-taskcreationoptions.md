---
title: 'Modification avec rupture : CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code CA2247.
ms.date: 09/03/2020
ms.openlocfilehash: 323fd5a05da4dfeb68ef75d88d5d293ba01c8ade
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761033"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="fd2c3-103">AVERTISSEMENT CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="fd2c3-103">Warning CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="fd2c3-104">La règle de l’analyseur de code .NET [CA2247](/visualstudio/code-quality/ca2247) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-104">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="fd2c3-105">Il génère un avertissement de génération pour les appels au <xref:System.Threading.Tasks.TaskCompletionSource%601> constructeur qui passent un argument de type <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="fd2c3-105">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

## <a name="change-description"></a><span data-ttu-id="fd2c3-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fd2c3-106">Change description</span></span>

<span data-ttu-id="fd2c3-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd2c3-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="fd2c3-108">Plusieurs de ces règles sont activées, par défaut, y compris [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="fd2c3-108">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="fd2c3-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="fd2c3-110">La règle CA2247 recherche les appels au <xref:System.Threading.Tasks.TaskCompletionSource%601> constructeur qui passent un argument de type <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="fd2c3-110">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="fd2c3-111">Le <xref:System.Threading.Tasks.TaskCompletionSource%601> type a un constructeur qui accepte une <xref:System.Threading.Tasks.TaskCreationOptions> valeur, et un autre constructeur qui accepte un <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="fd2c3-111">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="fd2c3-112">Si vous transmettez une <xref:System.Threading.Tasks.TaskContinuationOptions> valeur par inadvertance au lieu d’une <xref:System.Threading.Tasks.TaskCreationOptions> valeur, le constructeur avec le <xref:System.Object> paramètre est appelé au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-112">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="fd2c3-113">Votre code sera compilé et exécuté, mais n’aura pas le comportement prévu.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-113">Your code will compile and run but won't have the intended behavior.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fd2c3-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fd2c3-114">Version introduced</span></span>

<span data-ttu-id="fd2c3-115">5.0</span><span class="sxs-lookup"><span data-stu-id="fd2c3-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fd2c3-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fd2c3-116">Recommended action</span></span>

- <span data-ttu-id="fd2c3-117">Remplacez l' <xref:System.Threading.Tasks.TaskContinuationOptions> argument par la <xref:System.Threading.Tasks.TaskCreationOptions> valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-117">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="fd2c3-118">Ne supprimez pas cet avertissement, car il met presque toujours en évidence un bogue dans votre code.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-118">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="fd2c3-119">Pour plus d’informations, consultez [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="fd2c3-119">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="fd2c3-120">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="fd2c3-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="fd2c3-121">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="fd2c3-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fd2c3-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="fd2c3-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
