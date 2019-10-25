---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887766"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="0ffe9-101">Les appels à System.Windows.Input.PenContext.Disable sur des systèmes tactiles peuvent lever une exception ArgumentException</span><span class="sxs-lookup"><span data-stu-id="0ffe9-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0ffe9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="0ffe9-102">Details</span></span>|<span data-ttu-id="0ffe9-103">Dans certaines circonstances, les appels à la méthode **System.Windows.Intput.PenContext.Disable** interne sur des systèmes tactiles peuvent lever une exception <code>T:System.ArgumentException</code> non gérée en raison de la réentrance.</span><span class="sxs-lookup"><span data-stu-id="0ffe9-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="0ffe9-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="0ffe9-104">Suggestion</span></span>|<span data-ttu-id="0ffe9-105">Ce problème a été résolu dans le .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="0ffe9-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="0ffe9-106">Pour éviter cette exception, effectuez une mise à niveau avec une version du .NET Framework supérieure ou égale à 4.7.</span><span class="sxs-lookup"><span data-stu-id="0ffe9-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="0ffe9-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="0ffe9-107">Scope</span></span>|<span data-ttu-id="0ffe9-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0ffe9-108">Edge</span></span>|
|<span data-ttu-id="0ffe9-109">Version</span><span class="sxs-lookup"><span data-stu-id="0ffe9-109">Version</span></span>|<span data-ttu-id="0ffe9-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0ffe9-110">4.6.1</span></span>|
|<span data-ttu-id="0ffe9-111">Tapez</span><span class="sxs-lookup"><span data-stu-id="0ffe9-111">Type</span></span>|<span data-ttu-id="0ffe9-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="0ffe9-112">Retargeting</span></span>|
