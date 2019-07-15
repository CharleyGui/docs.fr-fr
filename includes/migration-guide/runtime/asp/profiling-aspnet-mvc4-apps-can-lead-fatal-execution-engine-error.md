---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803167"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="52350-101">Le profilage des applications ASP.NET MVC4 peut aboutir à une erreur irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="52350-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="52350-102">Détails</span><span class="sxs-lookup"><span data-stu-id="52350-102">Details</span></span>|<span data-ttu-id="52350-103">Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution</span><span class="sxs-lookup"><span data-stu-id="52350-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="52350-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="52350-104">Suggestion</span></span>|<span data-ttu-id="52350-105">Ce problème a été résolu dans .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="52350-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="52350-106">Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.</span><span class="sxs-lookup"><span data-stu-id="52350-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="52350-107">Portée</span><span class="sxs-lookup"><span data-stu-id="52350-107">Scope</span></span>|<span data-ttu-id="52350-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="52350-108">Edge</span></span>|
|<span data-ttu-id="52350-109">Version</span><span class="sxs-lookup"><span data-stu-id="52350-109">Version</span></span>|<span data-ttu-id="52350-110">4.5</span><span class="sxs-lookup"><span data-stu-id="52350-110">4.5</span></span>|
|<span data-ttu-id="52350-111">Type</span><span class="sxs-lookup"><span data-stu-id="52350-111">Type</span></span>|<span data-ttu-id="52350-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="52350-112">Runtime</span></span>|

