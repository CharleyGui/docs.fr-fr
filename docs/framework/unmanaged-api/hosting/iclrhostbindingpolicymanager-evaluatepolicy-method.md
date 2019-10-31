---
title: ICLRHostBindingPolicyManager::EvaluatePolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: 9600573a0a730cee10247d5644d587e75856cdd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141176"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy, méthode
Évalue la stratégie de liaison pour le compte de l’hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzReferenceIdentity`  
 dans Référence à l’assembly avant l’évaluation de la stratégie.  
  
 `pbApplicationPolicy`  
 dans Pointeur vers une mémoire tampon qui contient les données de stratégie.  
  
 `cbAppPolicySize`  
 dans Taille de la mémoire tampon de `pbApplicationPolicy`.  
  
 `pwzPostPolicyReferenceIdentity`  
 à Référence à l’assembly après l’évaluation des nouvelles données de stratégie.  
  
 `pcchPostPolicyReferenceIdentity`  
 [in, out] Pointeur vers la taille de la mémoire tampon de référence de l’identité de l’assembly après l’évaluation des nouvelles données de stratégie.  
  
 `pdwPoliciesApplied`  
 à Pointeur vers une combinaison logique ou de valeurs [EBindPolicyLevels,](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) , indiquant les stratégies qui ont été appliquées.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’évaluation s’est terminée avec succès.|  
|E_INVALIDARG|`pwzReferenceIdentity` ou `pbApplicationPolicy` est une référence null.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize` est trop petit.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 La méthode `EvaluatePolicy` permet à l’hôte d’influencer la stratégie de liaison pour tenir à jour les exigences en matière de contrôle de version des assemblys spécifiques à l’hôte. Le moteur de stratégie lui-même reste à l’intérieur du CLR.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostBindingPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
