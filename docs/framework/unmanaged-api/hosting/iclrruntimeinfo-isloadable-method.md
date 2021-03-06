---
title: ICLRRuntimeInfo::IsLoadable, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 2236e815211168d8e7105375b75f30128f7f209a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714965"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable, méthode

Indique si le runtime associé à cette interface peut être chargé dans le processus en cours, en tenant compte d’autres runtimes qui peuvent déjà être chargés dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pbLoadable`  
 [out] `true` Si ce runtime a pu être chargé dans le processus en cours ; Sinon, `false` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pbLoadable` a la valeur null.|  
  
## <a name="remarks"></a>Remarques  

 Si un autre Runtime est déjà chargé dans le processus et que le runtime associé à cette interface peut être chargé pour l’exécution côte à côte in-process, `pbLoadable` retourne `true` . Si les deux runtimes ne peuvent pas s’exécuter côte à côte in-process, `pbLoadable` retourne `false` . Par exemple, le common language runtime (CLR) version 4 peut s’exécuter côte à côte dans le même processus avec CLR version 2,0 ou CLR version 1,1. Toutefois, CLR version 1,1 et CLR version 2,0 ne peuvent pas s’exécuter côte à côte in-process.  
  
 Si aucun Runtime n’est chargé dans le processus, cette méthode retourne toujours `true` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
