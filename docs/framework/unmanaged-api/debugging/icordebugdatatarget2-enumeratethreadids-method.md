---
title: ICorDebugDataTarget2::EnumerateThreadIDs, méthode
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 31a839076b34901ae1a8f3b43021f64f77629fc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713845"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>ICorDebugDataTarget2::EnumerateThreadIDs, méthode

Retourne une liste des ID de threads actifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 cThreadIDs  
 [in] Nombre maximal de threads dont les ID peuvent être retournés.  
  
 pcThreadIds  
 [out] Pointeur vers un `ULONG32` qui indique le nombre réel d'ID de threads ayant été écrits dans le tableau `pThreadIds`.  
  
 pThreadIDs  
 Tableau d'identificateurs de threads.  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration système requise](../../get-started/system-requirements.md). **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget2, interface](icordebugdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
