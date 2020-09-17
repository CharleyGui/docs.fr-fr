---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738816"
---
### <a name="parameter-names-changed-in-rc1"></a><span data-ttu-id="44aca-101">Noms de paramètres modifiés dans RC1</span><span class="sxs-lookup"><span data-stu-id="44aca-101">Parameter names changed in RC1</span></span>

<span data-ttu-id="44aca-102">Certains noms de paramètres d’assembly de référence ont été modifiés pour correspondre aux noms de paramètres dans les assemblys d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="44aca-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="44aca-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="44aca-103">Change description</span></span>

<span data-ttu-id="44aca-104">Dans les versions antérieures de .NET 5,0 Preview et RC, certains noms de paramètres d' [assembly de référence](../../../../docs/standard/assembly/reference-assemblies.md) sont différents de leurs paramètres correspondants dans l’assembly d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="44aca-104">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="44aca-105">Cela peut provoquer des problèmes lors de l’utilisation d’arguments nommés et de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="44aca-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="44aca-106">Dans .NET 5,0 RC2, ces noms de paramètres incompatibles ont été mis à jour dans les assemblys de référence pour correspondre exactement aux noms de paramètres correspondants dans les assemblys d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="44aca-106">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="44aca-107">Le tableau suivant indique les API et les noms de paramètres qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="44aca-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="44aca-108">API</span><span class="sxs-lookup"><span data-stu-id="44aca-108">API</span></span> | <span data-ttu-id="44aca-109">Ancien nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="44aca-109">Old parameter name</span></span> | <span data-ttu-id="44aca-110">Nouveau nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="44aca-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a><span data-ttu-id="44aca-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="44aca-111">Reason for change</span></span>

<span data-ttu-id="44aca-112">Les noms de paramètres ont été modifiés pour des fins de cohérence et pour éviter des échecs lors de l’utilisation des arguments nommés et de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="44aca-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="44aca-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="44aca-113">Version introduced</span></span>

<span data-ttu-id="44aca-114">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="44aca-114">5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44aca-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="44aca-115">Recommended action</span></span>

<span data-ttu-id="44aca-116">Si vous rencontrez une erreur de compilation en raison d’un changement de nom de paramètre, mettez à jour le nom du paramètre en conséquence.</span><span class="sxs-lookup"><span data-stu-id="44aca-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="44aca-117">Category</span><span class="sxs-lookup"><span data-stu-id="44aca-117">Category</span></span>

<span data-ttu-id="44aca-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="44aca-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44aca-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="44aca-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
