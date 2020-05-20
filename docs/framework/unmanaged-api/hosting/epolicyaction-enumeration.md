---
title: EPolicyAction, énumération
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: 8788d6e2220778a3f0926d5ed3dd59142487bcca
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616188"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction, énumération
Décrit les actions de stratégie que l’hôte peut définir pour les opérations décrites par [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) et les échecs décrits par [EClrFailure](eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAbortThread`|Spécifie que le common language runtime (CLR) doit abandonner le thread normalement. Une annulation appropriée comprend les tentatives d’exécution de tous les `finally` blocs, tous les `catch` blocs liés aux abandons de thread et les finaliseurs.|  
|`eDisableRuntime`|Spécifie que le CLR doit entrer dans un état désactivé. Aucun code managé supplémentaire ne peut être exécuté dans le processus affecté, et les threads ne peuvent pas accéder au CLR.|  
|`eExitProcess`|Spécifie que le CLR doit tenter une sortie normale du processus, y compris l’exécution des finaliseurs et l’exécution des opérations de nettoyage et de journalisation.|  
|`eFastExitProcess`|Spécifie que le CLR doit quitter le processus immédiatement, sans exécuter de finaliseurs ou effectuer des opérations de nettoyage et de journalisation. Toutefois, la notification est envoyée au débogueur.|  
|`eNoAction`|Spécifie qu’aucune action ne doit être effectuée.|  
|`eRudeAbortThread`|Spécifie que le CLR doit effectuer une interruption de thread impropre. Seuls les `catch` `finally` blocs et marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutés.|  
|`eRudeExitProcess`|Spécifie que le CLR doit quitter le processus sans exécuter de finaliseurs ni d’opérations de journalisation.|  
|`eRudeUnloadAppDomain`|Spécifie que le CLR doit effectuer un déchargement impropre de <xref:System.AppDomain> . Seuls les finaliseurs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutés. De même, tous les threads avec ce <xref:System.AppDomain> dans leur pile reçoivent un `ThreadAbortException` , mais seuls ceux `catch` et les `finally` blocs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutés.|  
|`eThrowException`|Spécifie qu’une exception appropriée à la condition, telle que la mémoire insuffisante, le dépassement de capacité de la mémoire tampon, etc., doit être levée.|  
|`eUnloadAppDomain`|Spécifie que <xref:System.AppDomain> doit être déchargé. Le CLR tente d’exécuter des finaliseurs.|  
  
## <a name="remarks"></a>Notes  
 L’hôte définit des actions de stratégie en appelant des méthodes de l’interface [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) . Pour plus d’informations sur les abandons brutaux et normaux, consultez l’énumération [EClrOperation](eclroperation-enumeration.md) .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](eclrfailure-enumeration.md)
- [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)
- [IHostPolicyManager, interface](ihostpolicymanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
