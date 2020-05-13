---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: d2e54f0b16300673409eb2f5757338dfa3011e61
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212995"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags, méthode
Obtient les paramètres d’indicateur de compilateur en cours que le common language runtime (CLR) utilise pour sélectionner l’image précompilée (autrement dit, native) appropriée à charger dans ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwFlags`  
 à Pointeur vers une combinaison d’opérations de bits des valeurs d’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) utilisées pour sélectionner l’image précompilée appropriée à charger.  
  
## <a name="remarks"></a>Remarks  
 Utilisez la méthode [ICorDebugProcess2 :: SetDesiredNGENCompilerFlags,](icordebugprocess2-setdesiredngencompilerflags-method.md) pour définir les indicateurs que le CLR utilisera pour sélectionner l’image précompilée appropriée à charger.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
