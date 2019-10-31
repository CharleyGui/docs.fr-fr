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
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131163"
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
|`OPR_AppDomainRudeUnload`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’un <xref:System.AppDomain> est déchargé en mode non normal (impropre).|  
|`OPR_AppDomainUnload`|L’hôte peut spécifier des actions de stratégie à entreprendre lors du déchargement d’un <xref:System.AppDomain>.|  
|`OPR_FinalizerRun`|L’hôte peut spécifier des actions de stratégie à effectuer lors de l’exécution des finaliseurs.|  
|`OPR_ProcessExit`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsque le processus se termine.|  
|`OPR_ThreadAbort`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’un thread est abandonné.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’une interruption de thread impropre se produit dans une zone critique de code.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’une interruption de thread impropre se produit dans une région de code non critique.|  
  
## <a name="remarks"></a>Notes  
 L’infrastructure de fiabilité du common language runtime (CLR) distingue les abandons et les échecs d’allocation de ressources qui se produisent dans les régions de code critiques et ceux qui se produisent dans les régions de code non critiques. Cette distinction est conçue pour permettre aux hôtes de définir différentes stratégies en fonction de l’endroit où une défaillance se produit dans le code.  
  
 Une *région critique de code* est un espace où le CLR ne peut pas garantir que l’abandon d’une tâche ou l’échec de la réalisation d’une demande de ressources affectera uniquement la tâche en cours. Par exemple, si une tâche détient un verrou et reçoit un HRESULT qui indique un échec lors de l’exécution d’une demande d’allocation de mémoire, il est insuffisant simplement d’abandonner cette tâche pour garantir la stabilité du <xref:System.AppDomain>, car le <xref:System.AppDomain> peut contenir d’autres tâches en attente du même verrou. L’abandon de la tâche en cours peut entraîner le blocage de ces autres tâches. Dans ce cas, l’hôte a besoin de pouvoir décharger l’ensemble du <xref:System.AppDomain> plutôt que de risquer une instabilité potentielle.  
  
 Une *région de code non critique*, en revanche, est une région dans laquelle le CLR peut garantir qu’un abandon ou un échec affectera uniquement la tâche sur laquelle l’erreur se produit.  
  
 Le CLR distingue également les abandons normaux et non normaux (brutal). En général, un abandon normal ou normal fait tout son possible pour exécuter des routines de gestion des exceptions et des finaliseurs avant d’abandonner une tâche, tandis qu’un abandon impropre n’apporte aucune garantie de ce type.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction, énumération](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
