---
ms.openlocfilehash: 8b70df0fb2072fd5243d9e46a4a20c22cc7fd677
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607788"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="8539e-101">Le profilage des applications MVC4 ASP.NET peut provoquer une erreur irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="8539e-101">Profiling ASP.NET MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="8539e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8539e-102">Details</span></span>

<span data-ttu-id="8539e-103">Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="8539e-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8539e-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8539e-104">Suggestion</span></span>

<span data-ttu-id="8539e-105">Ce problème a été résolu dans .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="8539e-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="8539e-106">Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.</span><span class="sxs-lookup"><span data-stu-id="8539e-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="8539e-107">Name</span><span class="sxs-lookup"><span data-stu-id="8539e-107">Name</span></span>    | <span data-ttu-id="8539e-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="8539e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8539e-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="8539e-109">Scope</span></span>   |<span data-ttu-id="8539e-110">Edge</span><span class="sxs-lookup"><span data-stu-id="8539e-110">Edge</span></span>|
|<span data-ttu-id="8539e-111">Version</span><span class="sxs-lookup"><span data-stu-id="8539e-111">Version</span></span>|<span data-ttu-id="8539e-112">4.5</span><span class="sxs-lookup"><span data-stu-id="8539e-112">4.5</span></span>|
|<span data-ttu-id="8539e-113">Type</span><span class="sxs-lookup"><span data-stu-id="8539e-113">Type</span></span>|<span data-ttu-id="8539e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8539e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8539e-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="8539e-115">Affected APIs</span></span>

<span data-ttu-id="8539e-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="8539e-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
