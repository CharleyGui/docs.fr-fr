---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622030"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="7e92d-101">Le profilage des applications ASP.NET MVC4 peut aboutir à une erreur irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="7e92d-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="7e92d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7e92d-102">Details</span></span>

<span data-ttu-id="7e92d-103">Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="7e92d-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7e92d-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7e92d-104">Suggestion</span></span>

<span data-ttu-id="7e92d-105">Ce problème a été résolu dans .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="7e92d-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="7e92d-106">Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.</span><span class="sxs-lookup"><span data-stu-id="7e92d-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="7e92d-107">Nom</span><span class="sxs-lookup"><span data-stu-id="7e92d-107">Name</span></span>    | <span data-ttu-id="7e92d-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="7e92d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7e92d-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="7e92d-109">Scope</span></span>   |<span data-ttu-id="7e92d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7e92d-110">Edge</span></span>|
|<span data-ttu-id="7e92d-111">Version</span><span class="sxs-lookup"><span data-stu-id="7e92d-111">Version</span></span>|<span data-ttu-id="7e92d-112">4,5</span><span class="sxs-lookup"><span data-stu-id="7e92d-112">4.5</span></span>|
|<span data-ttu-id="7e92d-113">Type</span><span class="sxs-lookup"><span data-stu-id="7e92d-113">Type</span></span>|<span data-ttu-id="7e92d-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="7e92d-114">Runtime</span></span>|
