---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619920"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="ef371-101">Les contrôles GridView avec la valeur true définie pour AllowCustomPaging peuvent déclencher l’événement PageIndexChanging en quittant la dernière page de la vue</span><span class="sxs-lookup"><span data-stu-id="ef371-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="ef371-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ef371-102">Details</span></span>

<span data-ttu-id="ef371-103">Un bogue dans .NET Framework 4.5 contraint parfois <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> à ne pas se déclencher pour les <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> qui ont activé <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ef371-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ef371-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ef371-104">Suggestion</span></span>

<span data-ttu-id="ef371-105">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef371-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="ef371-106">Comme solution de contournement, l’application peut effectuer une opération BindGrid explicite sur n’importe quel <code>Page_Load</code> qui répond à ces conditions (le contrôle <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> figure dans la dernière page et Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> est différent de <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="ef371-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="ef371-107">L’application peut également être modifiée pour autoriser la pagination (au lieu de la pagination personnalisée), comme ce scénario ne présente pas le problème.</span><span class="sxs-lookup"><span data-stu-id="ef371-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="ef371-108">Nom</span><span class="sxs-lookup"><span data-stu-id="ef371-108">Name</span></span>    | <span data-ttu-id="ef371-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ef371-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ef371-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="ef371-110">Scope</span></span>   |<span data-ttu-id="ef371-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ef371-111">Minor</span></span>|
|<span data-ttu-id="ef371-112">Version</span><span class="sxs-lookup"><span data-stu-id="ef371-112">Version</span></span>|<span data-ttu-id="ef371-113">4,5</span><span class="sxs-lookup"><span data-stu-id="ef371-113">4.5</span></span>|
|<span data-ttu-id="ef371-114">Type</span><span class="sxs-lookup"><span data-stu-id="ef371-114">Type</span></span>|<span data-ttu-id="ef371-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="ef371-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef371-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="ef371-116">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
