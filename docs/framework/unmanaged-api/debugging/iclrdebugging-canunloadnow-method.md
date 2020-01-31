---
title: ICLRDebugging::CanUnloadNow, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 41b2e009f8f017a72147232015ea2357ae922ca1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793654"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow, méthode
Détermine si une bibliothèque qui a été fournie par une interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) est toujours en cours d’utilisation ou si elle peut être déchargée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a>Parameters  
 `hmodule`  
 dans Adresse de base d’un module dans le processus cible.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le module référencé par `hmodule` peut être déchargé.|  
|S_FALSE|Le module référencé par `hmodule` est toujours en cours d’utilisation.|  
|COR_E_NOT_CLR|Le module indiqué n’est pas un module CLR.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Cette méthode vérifie si toutes les instances d' `ICorDebug*` interfaces ont été libérées et qu’aucun thread n’est actuellement dans un appel à la méthode [ICLRDebugging :: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
