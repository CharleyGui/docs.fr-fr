---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: bffa6361df5a50748f45aa3004f7a307ad516d7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580487"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="b675c-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="b675c-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="b675c-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="b675c-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="b675c-104">Description</span><span class="sxs-lookup"><span data-stu-id="b675c-104">Description</span></span>  
 <span data-ttu-id="b675c-105">Le système a atteint la limite définie pour l'accélérateur ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="b675c-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="b675c-106">La valeur d'accélérateur peut être modifiée via la propriété ManualFlowControlLimit sur ServiceHost ou InstanceContext, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="b675c-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="b675c-107">Cette trace est émise lorsque la limite de contrôle de flux manuelle est initialement réduite à 0.</span><span class="sxs-lookup"><span data-stu-id="b675c-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="b675c-108">Les modifications ultérieures apportées à 0 ne sont pas suivies.</span><span class="sxs-lookup"><span data-stu-id="b675c-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="b675c-109">La limite de contrôle de flux sur le contexte d'instance est suivie une fois pour chaque contexte.</span><span class="sxs-lookup"><span data-stu-id="b675c-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b675c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b675c-110">See also</span></span>

- [<span data-ttu-id="b675c-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="b675c-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="b675c-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="b675c-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b675c-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="b675c-113">Administration and Diagnostics</span></span>](../index.md)
