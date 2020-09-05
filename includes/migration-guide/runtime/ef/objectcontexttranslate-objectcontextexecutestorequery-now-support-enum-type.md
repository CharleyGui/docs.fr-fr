---
ms.openlocfilehash: 81992e57d7e92b4df92ce68870c0272d6cd5b220
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496423"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="24cbb-101">ObjectContext.Translate et ObjectContext.ExecuteStoreQuery prennent maintenant en charge le type enum</span><span class="sxs-lookup"><span data-stu-id="24cbb-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="24cbb-102">Détails</span><span class="sxs-lookup"><span data-stu-id="24cbb-102">Details</span></span>

<span data-ttu-id="24cbb-103">Dans .NET Framework 4.0, le paramètre générique <code>T</code> des méthodes <code>ObjectContext.Translate</code> et <code>ObjectContext.ExecuteStoreQuery</code> ne pouvait pas être une énumération.</span><span class="sxs-lookup"><span data-stu-id="24cbb-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="24cbb-104">Ce scénario est désormais pris en charge.</span><span class="sxs-lookup"><span data-stu-id="24cbb-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="24cbb-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="24cbb-105">Suggestion</span></span>

<span data-ttu-id="24cbb-106">Si Translate ou ExecuteStoreQuery était appelé sur un type enum dans .NET Framework 4.0, la valeur « 0 » était retournée.</span><span class="sxs-lookup"><span data-stu-id="24cbb-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="24cbb-107">Si ce comportement était celui souhaité, les appels devaient être remplacés par une constante 0 (ou l’équivalent enum de celle-ci).</span><span class="sxs-lookup"><span data-stu-id="24cbb-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="24cbb-108">Name</span><span class="sxs-lookup"><span data-stu-id="24cbb-108">Name</span></span>    | <span data-ttu-id="24cbb-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="24cbb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="24cbb-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="24cbb-110">Scope</span></span>   |<span data-ttu-id="24cbb-111">Edge</span><span class="sxs-lookup"><span data-stu-id="24cbb-111">Edge</span></span>|
|<span data-ttu-id="24cbb-112">Version</span><span class="sxs-lookup"><span data-stu-id="24cbb-112">Version</span></span>|<span data-ttu-id="24cbb-113">4,5</span><span class="sxs-lookup"><span data-stu-id="24cbb-113">4.5</span></span>|
|<span data-ttu-id="24cbb-114">Type</span><span class="sxs-lookup"><span data-stu-id="24cbb-114">Type</span></span>|<span data-ttu-id="24cbb-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="24cbb-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="24cbb-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="24cbb-116">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

<!--

#### Affected APIs

- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader)``
- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.Object[])``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])``

-->
