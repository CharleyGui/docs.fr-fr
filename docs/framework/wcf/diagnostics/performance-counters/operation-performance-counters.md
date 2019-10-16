---
title: Compteurs de performance d'opération
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 59c75dacb2a01f1b85d67d5cc1651dbc55b6aa8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320176"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="ff836-102">Compteurs de performance d'opération</span><span class="sxs-lookup"><span data-stu-id="ff836-102">Operation Performance Counters</span></span>
<span data-ttu-id="ff836-103">Les compteurs de performance d'opération se trouvent sous l'objet de performance `ServiceModelOperation 4.0.0.0` lors de l'affichage avec l'analyseur de performances (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="ff836-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="ff836-104">Chaque opération a une instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="ff836-104">Each operation has an individual instance.</span></span> <span data-ttu-id="ff836-105">Autrement dit, si un contrat donné a 10 opérations, 10 instances de compteur d'opération sont associées à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="ff836-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="ff836-106">Les instances d’objet sont nommées à l’aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="ff836-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="ff836-107">Ce compteur vous permet de mesurer la manière dont l'appel est utilisé et comment l'opération s'exécute.</span><span class="sxs-lookup"><span data-stu-id="ff836-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ff836-108">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="ff836-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="ff836-109">Lorsqu’un nom d’instance de compteur Windows Communication Foundation (WCF) dépasse la longueur maximale, WCF remplace une partie du nom de l’instance par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="ff836-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff836-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff836-110">See also</span></span>

- [<span data-ttu-id="ff836-111">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="ff836-111">Performance Counters</span></span>](index.md)
