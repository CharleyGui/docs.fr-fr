---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178098"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode
Modifie la politique contraignante pour l’assemblage spécifié et crée une nouvelle version de la politique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzSourceAssemblyIdentity`  
 [dans] L’identité de l’assemblage à modifier.  
  
 `pwzTargetAssemblyIdentity`  
 [dans] La nouvelle identité de l’assemblage modifié.  
  
 `pbApplicationPolicy`  
 [dans] Pointeur d’un tampon qui contient les données de stratégie contraignantes que l’assemblage doit modifier.  
  
 `cbAppPolicySize`  
 [dans] L’ampleur de la politique contraignante à remplacer.  
  
 `dwPolicyModifyFlags`  
 [dans] Une combinaison de produits [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) logique, indiquant le contrôle de la redirection.  
  
 `pbNewApplicationPolicy`  
 [out] Un pointeur vers un tampon qui contient les nouvelles données de stratégie contraignantes.  
  
 `pcbNewAppPolicySize`  
 [dans, dehors] Un pointeur sur la taille du nouveau tampon de politique contraignante.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La politique a été modifiée avec succès.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` était une référence nulle.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel s’est fait chronométrer.|  
|HOST_E_NOT_OWNER|L’appelant n’est pas propriétaire de la serrure.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois qu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes   
 La `ModifyApplicationPolicy` méthode peut être appelée deux fois. Le premier appel doit fournir `pbNewApplicationPolicy` une valeur nulle pour le paramètre. Cet appel sera de retour `pcbNewAppPolicySize`avec la valeur nécessaire pour . Le deuxième appel devrait `pcbNewAppPolicySize`fournir cette valeur pour , `pbNewApplicationPolicy`et pointer vers un tampon de cette taille pour .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostBindingPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
