---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
ms.openlocfilehash: bc6543b46200dd611e13bdf55aabfabd8302e70a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793334"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode
Notifie le débogueur que l’exécution du code a atteint un point de séquence dans une version antérieure d’une fonction modifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la fonction modifiée.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel le point d’arrêt de remappage a été rencontré.  
  
 `pOldFunction`  
 dans Pointeur vers un objet ICorDebugFunction qui représente la version de la fonction en cours d’exécution sur le thread.  
  
 `pNewFunction`  
 dans Pointeur vers un objet ICorDebugFunction qui représente la version la plus récente de la fonction.  
  
 `oldILOffset`  
 dans Offset MSIL (Microsoft Intermediate Language) du pointeur d’instruction dans l’ancienne version de la fonction.  
  
## <a name="remarks"></a>Notes  
 Ce rappel permet au débogueur d’avoir la possibilité de remapper le pointeur d’instruction à son emplacement approprié dans la nouvelle version de la fonction spécifiée en appelant la méthode [ICorDebugILFrame2 :: RemapFunction,](icordebugilframe2-remapfunction-method.md) . Si le débogueur n’appelle pas `RemapFunction` avant d’appeler la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) , le runtime continuera à exécuter l’ancien code et déclenchera un autre rappel `FunctionRemapOpportunity` au point de séquence suivant.  
  
 Ce rappel sera appelé pour chaque frame qui exécute une version antérieure de la fonction donnée jusqu’à ce que le débogueur retourne S_OK.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
