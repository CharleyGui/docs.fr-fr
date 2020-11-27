---
title: Compteurs de performance d'opération
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 01f3ed7b2722f7ff4bdbb50e352920bdc277330f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295225"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="535b6-102">Compteurs de performance d'opération</span><span class="sxs-lookup"><span data-stu-id="535b6-102">Operation Performance Counters</span></span>

<span data-ttu-id="535b6-103">Les compteurs de performance d'opération se trouvent sous l'objet de performance `ServiceModelOperation 4.0.0.0` lors de l'affichage avec l'analyseur de performances (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="535b6-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="535b6-104">Chaque opération a une instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="535b6-104">Each operation has an individual instance.</span></span> <span data-ttu-id="535b6-105">Autrement dit, si un contrat donné a 10 opérations, 10 instances de compteur d'opération sont associées à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="535b6-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="535b6-106">Les instances d’objet sont nommées à l’aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="535b6-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="535b6-107">Ce compteur vous permet de mesurer la manière dont l'appel est utilisé et comment l'opération s'exécute.</span><span class="sxs-lookup"><span data-stu-id="535b6-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="535b6-108">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="535b6-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="535b6-109">Lorsqu’un nom d’instance de compteur Windows Communication Foundation (WCF) dépasse la longueur maximale, WCF remplace une partie du nom de l’instance par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="535b6-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535b6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="535b6-110">See also</span></span>

- [<span data-ttu-id="535b6-111">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="535b6-111">Performance Counters</span></span>](index.md)
