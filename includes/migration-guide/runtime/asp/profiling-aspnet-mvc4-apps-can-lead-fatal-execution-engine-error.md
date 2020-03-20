---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803167"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="39ea5-101">Le profilage des applications ASP.NET MVC4 peut aboutir à une erreur irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="39ea5-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="39ea5-102">Détails</span><span class="sxs-lookup"><span data-stu-id="39ea5-102">Details</span></span>|<span data-ttu-id="39ea5-103">Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="39ea5-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="39ea5-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="39ea5-104">Suggestion</span></span>|<span data-ttu-id="39ea5-105">Ce problème a été résolu dans .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="39ea5-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="39ea5-106">Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.</span><span class="sxs-lookup"><span data-stu-id="39ea5-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="39ea5-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="39ea5-107">Scope</span></span>|<span data-ttu-id="39ea5-108">Edge</span><span class="sxs-lookup"><span data-stu-id="39ea5-108">Edge</span></span>|
|<span data-ttu-id="39ea5-109">Version</span><span class="sxs-lookup"><span data-stu-id="39ea5-109">Version</span></span>|<span data-ttu-id="39ea5-110">4.5</span><span class="sxs-lookup"><span data-stu-id="39ea5-110">4.5</span></span>|
|<span data-ttu-id="39ea5-111">Type</span><span class="sxs-lookup"><span data-stu-id="39ea5-111">Type</span></span>|<span data-ttu-id="39ea5-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="39ea5-112">Runtime</span></span>|
