---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176407"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode
Appelle la méthode spécifiée du type spécifié dans l’assemblage géré spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAssemblyPath`  
 [dans] Le chemin <xref:System.Reflection.Assembly> vers celui <xref:System.Type> qui définit la méthode à invoquer.  
  
 `pwzTypeName`  
 [dans] Le nom <xref:System.Type> de celui qui définit la méthode à invoquer.  
  
 `pwzMethodName`  
 [dans] Le nom de la méthode à invoquer.  
  
 `pwzArgument`  
 [dans] Le paramètre de chaîne pour passer à la méthode.  
  
 `pReturnValue`  
 [out] La valeur de l’intégriste retournée par la méthode invoquée.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel s’est fait chronométrer.|  
|HOST_E_NOT_OWNER|L’appelant n’est pas propriétaire de la serrure.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode revient E_FAIL, la LCR n’est plus utilisable dans le processus. Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes   
 La méthode invoquée doit avoir la signature suivante :  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 où `pwzMethodName` représente le nom de `pwzArgument` la méthode invoquée, et représente la valeur de la chaîne transmise comme paramètre à cette méthode. Si la valeur HRESULT est réglée `pReturnValue` pour S_OK, est réglée à la valeur integer retournée par la méthode invoquée. Sinon, `pReturnValue` n’est pas fixé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
