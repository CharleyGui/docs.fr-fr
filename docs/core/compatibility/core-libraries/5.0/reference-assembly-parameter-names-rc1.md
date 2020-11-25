---
title: 'Modification avec rupture : noms de paramètres modifiés dans RC2'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où certains noms de paramètres d’assembly de référence ont changé par rapport aux versions Preview et Release candidate de .NET 5,0.
ms.date: 11/01/2020
ms.openlocfilehash: 554a4fa9e08fdb504f380465496d7e7e9df85814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760991"
---
# <a name="parameter-names-changed-in-rc2"></a><span data-ttu-id="47818-103">Noms de paramètres modifiés dans RC2</span><span class="sxs-lookup"><span data-stu-id="47818-103">Parameter names changed in RC2</span></span>

<span data-ttu-id="47818-104">Certains noms de paramètres d’assembly de référence ont été modifiés pour correspondre aux noms de paramètres dans les assemblys d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="47818-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="47818-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="47818-105">Change description</span></span>

<span data-ttu-id="47818-106">Dans les versions antérieures de .NET 5,0 Preview et RC, certains noms de paramètres d' [assembly de référence](../../../../standard/assembly/reference-assemblies.md) sont différents de leurs paramètres correspondants dans l’assembly d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="47818-106">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="47818-107">Cela peut provoquer des problèmes lors de l’utilisation d’arguments nommés et de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="47818-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="47818-108">Dans .NET 5,0 RC2, ces noms de paramètres incompatibles ont été mis à jour dans les assemblys de référence pour correspondre exactement aux noms de paramètres correspondants dans les assemblys d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="47818-108">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="47818-109">Le tableau suivant indique les API et les noms de paramètres qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="47818-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="47818-110">API</span><span class="sxs-lookup"><span data-stu-id="47818-110">API</span></span> | <span data-ttu-id="47818-111">Ancien nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="47818-111">Old parameter name</span></span> | <span data-ttu-id="47818-112">Nouveau nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="47818-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a><span data-ttu-id="47818-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="47818-113">Reason for change</span></span>

<span data-ttu-id="47818-114">Les noms de paramètres ont été modifiés pour des fins de cohérence et pour éviter des échecs lors de l’utilisation des arguments nommés et de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="47818-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="47818-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="47818-115">Version introduced</span></span>

<span data-ttu-id="47818-116">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="47818-116">5.0 RC2</span></span>

## <a name="recommended-action"></a><span data-ttu-id="47818-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="47818-117">Recommended action</span></span>

<span data-ttu-id="47818-118">Si vous rencontrez une erreur de compilation en raison d’un changement de nom de paramètre, mettez à jour le nom du paramètre en conséquence.</span><span class="sxs-lookup"><span data-stu-id="47818-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="47818-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="47818-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
