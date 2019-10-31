---
title: EClrFailure, énumération
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: 7d935bff023d806cf8cfb6d87bde0f82666b51b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131124"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure, énumération
Décrit l’ensemble des échecs pour lesquels un hôte peut définir des actions de stratégie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Une erreur s’est produite lors d’une tentative d’allocation d’une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une zone de code non critique.|  
|`FAIL_CriticalResource`|Une erreur s’est produite lors d’une tentative d’allocation d’une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une zone critique de code.|  
|`FAIL_FatalRuntime`|Le common language runtime (CLR) n’est plus en mesure d’exécuter du code managé dans le processus. Désormais, les appels à toutes les fonctions d’hébergement retournent une valeur HRESULT de HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Un thread n’a pas réussi à libérer un verrou lors du retour d’un objet <xref:System.AppDomain>. L’hôte ne peut pas définir cet échec pour provoquer l’abandon d’un thread.|  
|`FAIL_StackOverflow`|Un dépassement de capacité de la pile s’est produit.|  
|`FAIL_AccessViolation`|Une tentative de lecture ou d’écriture de mémoire protégée a été effectuée. Non pris en charge dans le .NET Framework 4.|  
|`FAIL_CodeContract`|Un échec de contrat de code s’est produit. Consultez la section [contrats de code](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Notes  
 Consultez la méthode [ICLRPolicyManager :: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) pour obtenir la liste des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) que l’hôte peut utiliser pour spécifier les actions de stratégie pour les conditions d’échec. Pour plus d’informations sur les régions de code critiques et non critiques, consultez [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnFailure, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
