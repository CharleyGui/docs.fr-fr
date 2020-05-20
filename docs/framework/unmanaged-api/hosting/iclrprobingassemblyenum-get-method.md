---
title: ICLRProbingAssemblyEnum::Get, méthode
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: ea66c142afc097d1003df4e7f5f5b960a91e2ab0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703385"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get, méthode
Obtient l’identité de l’assembly au niveau de l’index spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwIndex`  
 dans Index de base zéro de l’identité de l’assembly à retourner.  
  
 `pwzBuffer`  
 à Mémoire tampon contenant les données d’identité de l’assembly.  
  
 `pcchBufferSize`  
 [in, out] Taille de la `pwzBuffer` mémoire tampon.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Get`retourné avec succès.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` est trop petite.|  
|ERROR_NO_MORE_ITEMS|L’énumération ne contient plus d’éléments.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants à toutes les méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 L’identité à l’index 0 est l’identité propre à l’architecture du processeur. L’identité à l’index 1 est l’assembly indépendant de l’architecture pour le langage MSIL (Microsoft Intermediate Language). L’identité à l’index 2 ne contient aucune information d’architecture.  
  
 `Get`est généralement appelée deux fois. Le premier appel fournit une valeur null pour `pwzBuffer` et définit `pcchBufferSize` la taille appropriée pour `pwzBuffer` . Le deuxième appel fournit une taille appropriée `pwzBuffer` et contient les données d’identité de l’assembly canonique à l’achèvement.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRProbingAssemblyEnum, interface](iclrprobingassemblyenum-interface.md)
- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
