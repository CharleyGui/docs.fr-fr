---
ms.openlocfilehash: a84d72813a46d6bb39f4710b35d2c9dc859e30ef
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497874"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="a1874-101">L’événement Page.LoadComplete n’entraîne plus l’appel d’une liaison de données par le contrôle System.Web.UI.WebControls.EntityDataSource</span><span class="sxs-lookup"><span data-stu-id="a1874-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="a1874-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a1874-102">Details</span></span>

<span data-ttu-id="a1874-103">L'événement <xref:System.Web.UI.Page.LoadComplete> ne force plus le contrôle <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> à appeler une liaison de données pour les modifications dans le but de créer/mettre à jour/supprimer des paramètres.</span><span class="sxs-lookup"><span data-stu-id="a1874-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="a1874-104">Cette modification supprime un aller-retour superflu vers la base de données, empêche la réinitialisation des valeurs des contrôles et produit un comportement cohérent avec les autres contrôles de données, tels que <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> et <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a1874-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="a1874-105">Elle produit un comportement différent dans le cas peu probable où les applications dépendraient de l'appel de la liaison de données dans l'événement <xref:System.Web.UI.Page.LoadComplete>.</span><span class="sxs-lookup"><span data-stu-id="a1874-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a1874-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a1874-106">Suggestion</span></span>

<span data-ttu-id="a1874-107">Si une liaison de données est nécessaire, appelez manuellement la méthode databind dans un événement situé plus haut dans la publication (postback).</span><span class="sxs-lookup"><span data-stu-id="a1874-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="a1874-108">Name</span><span class="sxs-lookup"><span data-stu-id="a1874-108">Name</span></span>    | <span data-ttu-id="a1874-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="a1874-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a1874-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="a1874-110">Scope</span></span>   |<span data-ttu-id="a1874-111">Edge</span><span class="sxs-lookup"><span data-stu-id="a1874-111">Edge</span></span>|
|<span data-ttu-id="a1874-112">Version</span><span class="sxs-lookup"><span data-stu-id="a1874-112">Version</span></span>|<span data-ttu-id="a1874-113">4,5</span><span class="sxs-lookup"><span data-stu-id="a1874-113">4.5</span></span>|
|<span data-ttu-id="a1874-114">Type</span><span class="sxs-lookup"><span data-stu-id="a1874-114">Type</span></span>|<span data-ttu-id="a1874-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="a1874-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a1874-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="a1874-116">Affected APIs</span></span>

<span data-ttu-id="a1874-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="a1874-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
