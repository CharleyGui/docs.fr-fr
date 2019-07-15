---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804329"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="963d2-101">Les appels à System.Windows.Input.PenContext.Disable sur des systèmes tactiles peuvent lever une exception ArgumentException</span><span class="sxs-lookup"><span data-stu-id="963d2-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="963d2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="963d2-102">Details</span></span>|<span data-ttu-id="963d2-103">Dans certaines circonstances, les appels à la méthode <strong>System.Windows.Intput.PenContext.Disable</strong> interne sur des systèmes tactiles peuvent lever une exception <code>T:System.ArgumentException</code> non gérée en raison de la réentrance.</span><span class="sxs-lookup"><span data-stu-id="963d2-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="963d2-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="963d2-104">Suggestion</span></span>|<span data-ttu-id="963d2-105">Ce problème a été résolu dans le .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="963d2-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="963d2-106">Pour éviter cette exception, effectuez une mise à niveau avec une version du .NET Framework supérieure ou égale à 4.7.</span><span class="sxs-lookup"><span data-stu-id="963d2-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="963d2-107">Portée</span><span class="sxs-lookup"><span data-stu-id="963d2-107">Scope</span></span>|<span data-ttu-id="963d2-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="963d2-108">Edge</span></span>|
|<span data-ttu-id="963d2-109">Version</span><span class="sxs-lookup"><span data-stu-id="963d2-109">Version</span></span>|<span data-ttu-id="963d2-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="963d2-110">4.6.1</span></span>|
|<span data-ttu-id="963d2-111">Type</span><span class="sxs-lookup"><span data-stu-id="963d2-111">Type</span></span>|<span data-ttu-id="963d2-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="963d2-112">Retargeting</span></span>|

