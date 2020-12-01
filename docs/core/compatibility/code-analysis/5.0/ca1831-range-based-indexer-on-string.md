---
title: 'Modification avec rupture : CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour une chaîne'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code CA1831.
ms.date: 08/21/2020
ms.openlocfilehash: 850916b804ae29dba8d2bd05c6e4fb06fe667296
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437886"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="f643f-103">AVERTISSEMENT CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour une chaîne</span><span class="sxs-lookup"><span data-stu-id="f643f-103">Warning CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="f643f-104">La règle de l’analyseur de code .NET [CA1831](/visualstudio/code-quality/ca1831) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="f643f-104">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="f643f-105">Il génère un avertissement de génération pour tout code où un <xref:System.Range> indexeur de based est utilisé sur une chaîne, mais aucune copie n’était prévue.</span><span class="sxs-lookup"><span data-stu-id="f643f-105">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

## <a name="change-description"></a><span data-ttu-id="f643f-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f643f-106">Change description</span></span>

<span data-ttu-id="f643f-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="f643f-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="f643f-108">Plusieurs de ces règles sont activées, par défaut, y compris [CA1831](/visualstudio/code-quality/ca1831).</span><span class="sxs-lookup"><span data-stu-id="f643f-108">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="f643f-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="f643f-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="f643f-110">La règle CA1831 trouve des instances où un <xref:System.Range> indexeur de base est utilisé sur une chaîne, mais qu’aucune copie n’était prévue.</span><span class="sxs-lookup"><span data-stu-id="f643f-110">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="f643f-111">Si l' <xref:System.Range> indexeur de base est utilisé directement sur une chaîne pour produire un cast implicite, une copie inutile de la partie demandée de la chaîne est créée.</span><span class="sxs-lookup"><span data-stu-id="f643f-111">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="f643f-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f643f-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="f643f-113">CA1831 suggère d’utiliser à la <xref:System.Range> place l’indexeur basé sur une *étendue* de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="f643f-113">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="f643f-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f643f-114">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a><span data-ttu-id="f643f-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f643f-115">Version introduced</span></span>

<span data-ttu-id="f643f-116">5.0</span><span class="sxs-lookup"><span data-stu-id="f643f-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f643f-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f643f-117">Recommended action</span></span>

- <span data-ttu-id="f643f-118">Pour corriger votre code et éviter les allocations inutiles, appelez <xref:System.MemoryExtensions.AsSpan(System.String)> ou <xref:System.MemoryExtensions.AsMemory(System.String)> avant d’utiliser l' <xref:System.Range> indexeur basé sur.</span><span class="sxs-lookup"><span data-stu-id="f643f-118">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="f643f-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f643f-119">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="f643f-120">Si vous ne souhaitez pas modifier votre code, vous pouvez désactiver la règle en affectant à sa gravité la valeur `suggestion` ou `none` .</span><span class="sxs-lookup"><span data-stu-id="f643f-120">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="f643f-121">Pour plus d’informations, consultez [configurer des règles d’analyse du code](../../../../fundamentals/code-analysis/configuration-options.md).</span><span class="sxs-lookup"><span data-stu-id="f643f-121">For more information, see [Configure code analysis rules](../../../../fundamentals/code-analysis/configuration-options.md).</span></span>

- <span data-ttu-id="f643f-122">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="f643f-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="f643f-123">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="f643f-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f643f-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="f643f-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
