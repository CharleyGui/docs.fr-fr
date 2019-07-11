---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords, méthode
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b436bd844f917aab3c653428c7cd38809be870b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771385"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a>ICorDebugSymbolProvider::GetMergedAssemblyRecords, méthode
Obtient les enregistrements de symbole de tous les assemblys fusionnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cRequestedRecords`  
 [in] Nombre d'enregistrements de symbole demandé.  
  
 `pcFetchedRecords`  
 [out] Pointeur vers le nombre d'enregistrements de symbole récupéré par la méthode.  
  
 `pRecords`  
 Un pointeur vers un tableau de [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objets.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugSymbolProvider, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
