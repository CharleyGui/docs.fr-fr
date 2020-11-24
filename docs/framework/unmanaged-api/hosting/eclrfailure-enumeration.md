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
ms.openlocfilehash: d2794b53ed17640413928b3af0d1ed3656e25f22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675761"
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
|`FAIL_OrphanedLock`|Un thread n’a pas réussi à libérer un verrou lors du retour d’un <xref:System.AppDomain> objet. L’hôte ne peut pas définir cet échec pour provoquer l’abandon d’un thread.|  
|`FAIL_StackOverflow`|Un dépassement de capacité de la pile s’est produit.|  
|`FAIL_AccessViolation`|Une tentative de lecture ou d’écriture de mémoire protégée a été effectuée. Non pris en charge dans le .NET Framework 4.|  
|`FAIL_CodeContract`|Un échec de contrat de code s’est produit. Consultez la section [contrats de code](../../debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Remarques  

 Consultez la méthode [ICLRPolicyManager :: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) pour obtenir la liste des valeurs [EPolicyAction](epolicyaction-enumeration.md) que l’hôte peut utiliser pour spécifier les actions de stratégie pour les conditions d’échec. Pour plus d’informations sur les régions de code critiques et non critiques, consultez [EClrOperation](eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)
- [SetActionOnFailure, méthode](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager, interface](ihostpolicymanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
