---
title: ICLRMetaHost::GetRuntime, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: d482e25c7bf0f028e2478c8e7b7863bc54d7aeb9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504190"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime, méthode
Obtient l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui correspond à une version particulière du Common Language Runtime (CLR). Cette méthode remplace la fonction [CorBindToRuntimeEx](corbindtoruntimeex-function.md) utilisée avec l’indicateur [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzVersion`  
 dans Version de compilation .NET Framework stockée dans les métadonnées, au format «v*A*. *B*[.* X*]». *A*, *B*et *X* sont des nombres décimaux qui correspondent à la version principale, à la version mineure et au numéro de Build.  
  
> [!NOTE]
> Ce paramètre doit correspondre au nom de répertoire de la version .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.  
  
 Les exemples de valeurs sont « v 1.0.3705 », « v 1.1.4322 », « v 2.0.50727 » et « v 4.0 ». *X*», où *x* dépend du numéro de Build installé. Le préfixe « v » est obligatoire.  
  
 `riid`  
 dans Identificateur de l’interface souhaitée. Actuellement, la seule valeur valide pour ce paramètre est IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 à Pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui correspond au runtime demandé.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzVersion` ou `ppRuntime` est null.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode interagit de manière cohérente avec les interfaces héritées telles que l’interface [ICorRuntimeHost](icorruntimehost-interface.md) et les fonctions héritées telles que les fonctions déconseillées `CorBindTo*` (consultez [fonctions d’hébergement CLR dépréciées](deprecated-clr-hosting-functions.md) dans l’API d’hébergement .NET Framework 2,0). Autrement dit, les runtimes chargés avec l’API héritée sont visibles par la nouvelle API, et les runtimes chargés avec la nouvelle API sont visibles par l’API héritée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetaHost, interface](iclrmetahost-interface.md)
- [Interfaces d'hébergement du CLR et coclasses déconseillées](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [Interfaces d'hébergement du CLR](clr-hosting-interfaces.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
- [Hosting](index.md)
