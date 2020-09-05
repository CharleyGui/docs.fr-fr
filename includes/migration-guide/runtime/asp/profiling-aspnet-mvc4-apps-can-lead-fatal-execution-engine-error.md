---
ms.openlocfilehash: c679cb2603d39f580203d9373d76481e904e6c1d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497546"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="da992-101">Le profilage des applications ASP.NET MVC4 peut aboutir à une erreur irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="da992-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="da992-102">Détails</span><span class="sxs-lookup"><span data-stu-id="da992-102">Details</span></span>

<span data-ttu-id="da992-103">Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="da992-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="da992-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="da992-104">Suggestion</span></span>

<span data-ttu-id="da992-105">Ce problème a été résolu dans .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="da992-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="da992-106">Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.</span><span class="sxs-lookup"><span data-stu-id="da992-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="da992-107">Name</span><span class="sxs-lookup"><span data-stu-id="da992-107">Name</span></span>    | <span data-ttu-id="da992-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="da992-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="da992-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="da992-109">Scope</span></span>   |<span data-ttu-id="da992-110">Edge</span><span class="sxs-lookup"><span data-stu-id="da992-110">Edge</span></span>|
|<span data-ttu-id="da992-111">Version</span><span class="sxs-lookup"><span data-stu-id="da992-111">Version</span></span>|<span data-ttu-id="da992-112">4,5</span><span class="sxs-lookup"><span data-stu-id="da992-112">4.5</span></span>|
|<span data-ttu-id="da992-113">Type</span><span class="sxs-lookup"><span data-stu-id="da992-113">Type</span></span>|<span data-ttu-id="da992-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="da992-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="da992-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="da992-115">Affected APIs</span></span>

<span data-ttu-id="da992-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="da992-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
