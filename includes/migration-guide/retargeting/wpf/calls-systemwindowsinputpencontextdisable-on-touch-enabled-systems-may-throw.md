---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617530"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="e79b3-101">Les appels à System.Windows.Input.PenContext.Disable sur des systèmes tactiles peuvent lever une exception ArgumentException</span><span class="sxs-lookup"><span data-stu-id="e79b3-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="e79b3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e79b3-102">Details</span></span>

<span data-ttu-id="e79b3-103">Dans certaines circonstances, les appels à la méthode **System.Windows.Intput.PenContext.Disable** interne sur des systèmes tactiles peuvent lever une exception `T:System.ArgumentException` non gérée en raison de la réentrance.</span><span class="sxs-lookup"><span data-stu-id="e79b3-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e79b3-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e79b3-104">Suggestion</span></span>

<span data-ttu-id="e79b3-105">Ce problème a été résolu dans le .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="e79b3-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="e79b3-106">Pour éviter cette exception, effectuez une mise à niveau avec une version du .NET Framework supérieure ou égale à 4.7.</span><span class="sxs-lookup"><span data-stu-id="e79b3-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="e79b3-107">Nom</span><span class="sxs-lookup"><span data-stu-id="e79b3-107">Name</span></span>    | <span data-ttu-id="e79b3-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e79b3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e79b3-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="e79b3-109">Scope</span></span>   | <span data-ttu-id="e79b3-110">Edge</span><span class="sxs-lookup"><span data-stu-id="e79b3-110">Edge</span></span>        |
| <span data-ttu-id="e79b3-111">Version</span><span class="sxs-lookup"><span data-stu-id="e79b3-111">Version</span></span> | <span data-ttu-id="e79b3-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="e79b3-112">4.6.1</span></span>       |
| <span data-ttu-id="e79b3-113">Type</span><span class="sxs-lookup"><span data-stu-id="e79b3-113">Type</span></span>    | <span data-ttu-id="e79b3-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="e79b3-114">Retargeting</span></span> |
