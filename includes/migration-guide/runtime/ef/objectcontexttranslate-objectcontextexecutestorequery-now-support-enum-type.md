---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620028"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="6ce2d-101">ObjectContext.Translate et ObjectContext.ExecuteStoreQuery prennent maintenant en charge le type enum</span><span class="sxs-lookup"><span data-stu-id="6ce2d-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="6ce2d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6ce2d-102">Details</span></span>

<span data-ttu-id="6ce2d-103">Dans .NET Framework 4.0, le paramètre générique <code>T</code> des méthodes <code>ObjectContext.Translate</code> et <code>ObjectContext.ExecuteStoreQuery</code> ne pouvait pas être une énumération.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="6ce2d-104">Ce scénario est désormais pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6ce2d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6ce2d-105">Suggestion</span></span>

<span data-ttu-id="6ce2d-106">Si Translate ou ExecuteStoreQuery était appelé sur un type enum dans .NET Framework 4.0, la valeur « 0 » était retournée.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="6ce2d-107">Si ce comportement était celui souhaité, les appels devaient être remplacés par une constante 0 (ou l’équivalent enum de celle-ci).</span><span class="sxs-lookup"><span data-stu-id="6ce2d-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="6ce2d-108">Nom</span><span class="sxs-lookup"><span data-stu-id="6ce2d-108">Name</span></span>    | <span data-ttu-id="6ce2d-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="6ce2d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ce2d-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="6ce2d-110">Scope</span></span>   |<span data-ttu-id="6ce2d-111">Edge</span><span class="sxs-lookup"><span data-stu-id="6ce2d-111">Edge</span></span>|
|<span data-ttu-id="6ce2d-112">Version</span><span class="sxs-lookup"><span data-stu-id="6ce2d-112">Version</span></span>|<span data-ttu-id="6ce2d-113">4,5</span><span class="sxs-lookup"><span data-stu-id="6ce2d-113">4.5</span></span>|
|<span data-ttu-id="6ce2d-114">Type</span><span class="sxs-lookup"><span data-stu-id="6ce2d-114">Type</span></span>|<span data-ttu-id="6ce2d-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="6ce2d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6ce2d-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="6ce2d-116">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
