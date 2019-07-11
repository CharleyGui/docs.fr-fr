---
title: ICorDebugRemoteTarget, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e2e6a4624403dcab30bdb7b6d3af0226204cac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744648"
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget, interface
Fournit des méthodes qui permettent aux développeurs de déboguer les applications Silverlight dans l’environnement du common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Retourne le nom d’hôte ou l’adresse IP d’un ordinateur distant.|  
  
## <a name="remarks"></a>Notes  
 Le débogage en mode mixte (autrement dit, code managé et natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows ME, ou sur les plateformes non x86 (par exemple, IA-64 et AMD64).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl  
  
 **Bibliothèque :** : CorGuids.lib  
  
 **Versions du .NET framework :** 3.5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemote, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
