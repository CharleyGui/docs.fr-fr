---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: c3174e70d42385923674a3db5f696a0f64eda29f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295356"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="82c74-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="82c74-102">CoordinatorRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="82c74-103">ID : 139</span><span class="sxs-lookup"><span data-stu-id="82c74-103">Id: 139</span></span>  
  
 <span data-ttu-id="82c74-104">Gravité : Erreur</span><span class="sxs-lookup"><span data-stu-id="82c74-104">Severity: Error</span></span>  
  
 <span data-ttu-id="82c74-105">Catégorie : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="82c74-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="82c74-106">Description</span><span class="sxs-lookup"><span data-stu-id="82c74-106">Description</span></span>  

 <span data-ttu-id="82c74-107">Cet événement indique qu'une entrée de journal de récupération de coordinateur a été endommagée et n'a pas pu être désérialisée.</span><span class="sxs-lookup"><span data-stu-id="82c74-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="82c74-108">Cette erreur risque d'entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="82c74-108">Data loss may result from this error.</span></span> <span data-ttu-id="82c74-109">L’événement répertorie l’ID de transaction, les données de récupération (encodage Base64), l’exception, le nom de processus et l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="82c74-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c74-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82c74-110">See also</span></span>

- [<span data-ttu-id="82c74-111">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="82c74-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="82c74-112">Référence générale relative aux événements</span><span class="sxs-lookup"><span data-stu-id="82c74-112">Events General Reference</span></span>](events-general-reference.md)
