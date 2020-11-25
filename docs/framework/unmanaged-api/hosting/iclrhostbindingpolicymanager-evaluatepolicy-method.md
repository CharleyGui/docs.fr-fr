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
ms.openlocfilehash: 9840217abdf8b3e1d0917b7447572b6860c181c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720306"
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
 dans Taille de la `pbApplicationPolicy` mémoire tampon.  
  
 `pwzPostPolicyReferenceIdentity`  
 à Référence à l’assembly après l’évaluation des nouvelles données de stratégie.  
  
 `pcchPostPolicyReferenceIdentity`  
 [in, out] Pointeur vers la taille de la mémoire tampon de référence de l’identité de l’assembly après l’évaluation des nouvelles données de stratégie.  
  
 `pdwPoliciesApplied`  
 à Pointeur vers une combinaison logique ou de valeurs [EBindPolicyLevels,](ebindpolicylevels-enumeration.md) , indiquant les stratégies qui ont été appliquées.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’évaluation s’est terminée avec succès.|  
|E_INVALIDARG|`pwzReferenceIdentity`Ou `pbApplicationPolicy` est une référence null.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize` est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 La `EvaluatePolicy` méthode permet à l’hôte d’influencer la stratégie de liaison pour tenir à jour les exigences en matière de contrôle de version des assemblys spécifiques à l’hôte. Le moteur de stratégie lui-même reste à l’intérieur du CLR.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostBindingPolicyManager, interface](iclrhostbindingpolicymanager-interface.md)
