---
title: Compteurs de performance de service
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 929ddcb2f271b7488270ea39e7a3a0037158c855
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320029"
---
# <a name="service-performance-counters"></a><span data-ttu-id="27ee6-102">Compteurs de performance de service</span><span class="sxs-lookup"><span data-stu-id="27ee6-102">Service Performance Counters</span></span>
<span data-ttu-id="27ee6-103">Les compteurs de performance de service mesurent le comportement du service dans son ensemble et peuvent être utilisés pour diagnostiquer les performances de la totalité du service.</span><span class="sxs-lookup"><span data-stu-id="27ee6-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="27ee6-104">Ils se trouvent sous l'objet de performance `ServiceModelService 4.0.0.0` dans l'affichage de l'analyseur de performances (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="27ee6-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="27ee6-105">Les instances sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="27ee6-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="27ee6-106">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="27ee6-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="27ee6-107">Lorsqu’un nom d’instance de compteur Windows Communication Foundation (WCF) dépasse la longueur maximale, WCF remplace une partie du nom de l’instance par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="27ee6-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ee6-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27ee6-108">See also</span></span>

- [<span data-ttu-id="27ee6-109">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="27ee6-109">Performance Counters</span></span>](index.md)
