---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: 9cc68e39dfef096b8ab6a8ba743f7a516cc349be
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210408"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode
Retourne le thread managé qui détient le verrou du moniteur sur cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppThread`  
 à Thread managé qui possède le verrou du moniteur sur cet objet.  
  
 `pAcquisitionCount`  
 à Nombre de fois que ce thread doit libérer le verrou avant qu’il ne soit plus propriétaire.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|S_FALSE|Aucun thread managé ne possède le verrou du moniteur sur cet objet.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarks  
 Si un thread managé possède le verrou du moniteur sur cet objet :  
  
- La méthode retourne S_OK.  
  
- L’objet thread est valide jusqu’à ce que le thread se termine.  
  
 Si aucun thread managé n’est propriétaire du verrou du moniteur sur cet objet, `ppThread` et que `pAcquisitionCount` la méthode retourne S_FALSE.  
  
 Si `ppThread` ou `pAcquisitionCount` n’est pas un pointeur valide, le résultat n’est pas défini.  
  
 Si une erreur se produit et qu’il est impossible de déterminer le thread qui, le cas échéant, détient le verrou du moniteur sur cet objet, la méthode retourne un HRESULT qui indique un échec.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
