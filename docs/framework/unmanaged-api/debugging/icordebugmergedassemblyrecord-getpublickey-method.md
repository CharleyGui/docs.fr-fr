---
title: ICorDebugMergedAssemblyRecord::GetPublicKey, méthode
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793115"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKey, méthode
Obtient la clé publique de l'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parameters  
 `cbPublicKey`  
 [in] Nombre maximal d'octets dans le tableau `pbPublicKey`.  
  
 `pcbPublicKey`  
 [out] Pointeur vers le nombre réel d'octets écrits dans le tableau `pbPublicKey`.  
  
 `pbPublicKey`  
 [in] Pointeur vers un tableau d'octets contenant la clé publique de l'assembly.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMergedAssemblyRecord, interface](icordebugmergedassemblyrecord-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
