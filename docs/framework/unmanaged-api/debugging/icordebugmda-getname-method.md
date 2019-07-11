---
title: ICorDebugMDA::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca5d96e51c3809c6652d1a1fd75b80efb0b34222
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761910"
---
# <a name="icordebugmdagetname-method"></a>ICorDebugMDA::GetName, méthode
Obtient une chaîne contenant le nom de l’assistant débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] Taille du tableau `szName`.  
  
 `pcchName`  
 [out] Pointeur vers la longueur du nom.  
  
 `szName`  
 [out] Tableau dans lequel stocker le nom.  
  
## <a name="remarks"></a>Notes  
 Noms de l’Assistant Débogage MANAGÉ sont des valeurs uniques. Le `GetName` méthode constitue une alternative de performance appropriée pour obtenir le flux XML et extraire le nom à partir du flux en fonction du schéma.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMDA, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
