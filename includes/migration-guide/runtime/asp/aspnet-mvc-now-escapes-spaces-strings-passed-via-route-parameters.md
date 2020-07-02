---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619926"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="85cd3-101">ASP.NET MVC place désormais dans une séquence d’échappement les espaces dans les chaînes passées via des paramètres d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="85cd3-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="85cd3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="85cd3-102">Details</span></span>

<span data-ttu-id="85cd3-103">Pour des raisons de conformité à la norme RFC 2396, les espaces situés dans les itinéraires de routage sont désormais échappés lors du remplissage des paramètres d’action à partir d’un itinéraire.</span><span class="sxs-lookup"><span data-stu-id="85cd3-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="85cd3-104">Dans les versions précédentes, <code>/controller/action/some data</code> correspondait à l’itinéraire <code>/controller/action/{data}</code> et fournissait <code>some data</code> comme paramètre de données. Désormais, il fournit <code>some%20data</code> à la place.</span><span class="sxs-lookup"><span data-stu-id="85cd3-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85cd3-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="85cd3-105">Suggestion</span></span>

<span data-ttu-id="85cd3-106">Le code doit être mis à jour pour ne plus échapper les paramètres de chaîne à partir d’un itinéraire.</span><span class="sxs-lookup"><span data-stu-id="85cd3-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="85cd3-107">Si l’URI d’origine est nécessaire, vous pouvez y accéder avec l’API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.</span><span class="sxs-lookup"><span data-stu-id="85cd3-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="85cd3-108">Nom</span><span class="sxs-lookup"><span data-stu-id="85cd3-108">Name</span></span>    | <span data-ttu-id="85cd3-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="85cd3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85cd3-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="85cd3-110">Scope</span></span>   |<span data-ttu-id="85cd3-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="85cd3-111">Minor</span></span>|
|<span data-ttu-id="85cd3-112">Version</span><span class="sxs-lookup"><span data-stu-id="85cd3-112">Version</span></span>|<span data-ttu-id="85cd3-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="85cd3-113">4.5.2</span></span>|
|<span data-ttu-id="85cd3-114">Type</span><span class="sxs-lookup"><span data-stu-id="85cd3-114">Type</span></span>|<span data-ttu-id="85cd3-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="85cd3-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="85cd3-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="85cd3-116">Affected APIs</span></span>

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
