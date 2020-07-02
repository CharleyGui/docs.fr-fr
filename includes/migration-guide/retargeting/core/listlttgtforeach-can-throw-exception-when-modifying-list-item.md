---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617217"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="c4071-101">List&lt;T&gt;.ForEach peut lever une exception quand vous modifiez un élément de la liste</span><span class="sxs-lookup"><span data-stu-id="c4071-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="c4071-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c4071-102">Details</span></span>

<span data-ttu-id="c4071-103">À compter de .NET Framework 4.5, un énumérateur <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> lève une exception <xref:System.InvalidOperationException?displayProperty=fullName> si un élément de la collection appelante est modifié.</span><span class="sxs-lookup"><span data-stu-id="c4071-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="c4071-104">Avant, il ne levait pas d’exception, mais pouvait entraîner des conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="c4071-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c4071-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c4071-105">Suggestion</span></span>

<span data-ttu-id="c4071-106">Dans l’idéal, le code doit être corrigé de manière à ne pas modifier les listes pendant l’énumération de leurs éléments, car cela n’est jamais une opération sûre.</span><span class="sxs-lookup"><span data-stu-id="c4071-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="c4071-107">Cependant, pour restaurer le comportement précédent, une application peut cibler .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="c4071-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="c4071-108">Nom</span><span class="sxs-lookup"><span data-stu-id="c4071-108">Name</span></span>    | <span data-ttu-id="c4071-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="c4071-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c4071-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="c4071-110">Scope</span></span>   | <span data-ttu-id="c4071-111">Edge</span><span class="sxs-lookup"><span data-stu-id="c4071-111">Edge</span></span>        |
| <span data-ttu-id="c4071-112">Version</span><span class="sxs-lookup"><span data-stu-id="c4071-112">Version</span></span> | <span data-ttu-id="c4071-113">4,5</span><span class="sxs-lookup"><span data-stu-id="c4071-113">4.5</span></span>         |
| <span data-ttu-id="c4071-114">Type</span><span class="sxs-lookup"><span data-stu-id="c4071-114">Type</span></span>    | <span data-ttu-id="c4071-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="c4071-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c4071-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="c4071-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
