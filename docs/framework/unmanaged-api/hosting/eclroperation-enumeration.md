---
title: EClrOperation, énumération
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b000ed3d75ddb6a7882cb8f03ff2cec64fb9fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767877"
---
# <a name="eclroperation-enumeration"></a>EClrOperation, énumération
Décrit l’ensemble des opérations pour lesquelles un hôte peut appliquer des actions de stratégie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un <xref:System.AppDomain> est déchargé de façon non appropriée (non applicables).|  
|`OPR_AppDomainUnload`|L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un <xref:System.AppDomain> est déchargé.|  
|`OPR_FinalizerRun`|L’hôte peut spécifier des actions de stratégie à prendre lors de l’exécuteront des finaliseurs.|  
|`OPR_ProcessExit`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsque le processus se termine.|  
|`OPR_ThreadAbort`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’un thread est abandonné.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|L’hôte peut spécifier des actions à entreprendre lorsqu’un abandon de thread brutal se produit dans une région de code critique de stratégie.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un abandon de thread brutal se produit dans une région de code non critique.|  
  
## <a name="remarks"></a>Notes  
 L’infrastructure de fiabilité du common language runtime (CLR) fait la distinction entre les ressources et les abandons échecs d’allocation qui se produisent dans des zones critiques du code et ceux qui se produisent dans les régions non critiques de code. Cette distinction est conçue pour permettre aux hôtes de définir différentes stratégies en fonction de l’endroit où une défaillance se produit dans le code.  
  
 Un *région critique de code* est un espace où le CLR ne peut pas garantir que l’abandon d’une tâche ou ne parvient pas à terminer une demande de ressources affectera uniquement la tâche en cours. Par exemple, si une tâche maintient un verrou et reçoit un HRESULT qui indique un échec lors d’une demande d’allocation de mémoire, il est insuffisant simplement pour abandonner cette tâche pour garantir la stabilité de la <xref:System.AppDomain>, car le <xref:System.AppDomain> peut contenir d’autres tâches en attente pour le même verrou. Pour abandonner actuel tâche peut entraîner des autres tâches de cesser de répondre. Dans ce cas, l’hôte doit pouvoir décharger l’intégralité de <xref:System.AppDomain> plutôt que d’instabilité du risque.  
  
 Un *région non critique de code*, quant à eux, est une région où le CLR peut garantir qu’un abandon ou un échec affectera uniquement la tâche sur laquelle l’erreur se produit.  
  
 Le CLR fait également la distinction entre les abandons (non applicables) sans perte de données et non-sans perte de données. En général, un abandon normal ou correct fait en sorte d’exécuter des routines de gestion des exceptions et des finaliseurs avant d’abandonner une tâche, alors qu’un abandon brutal ne garantit pas ce type.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction, énumération](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
