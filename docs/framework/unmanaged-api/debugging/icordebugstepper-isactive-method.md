---
title: ICorDebugStepper::IsActive, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791776"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive, méthode
Obtient une valeur qui indique si ces ICorDebugStepper exécutent actuellement une étape.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pbActive`  
 à Retourne `true` si le pas à pas exécute actuellement une étape ; Sinon, retourne `false`.  
  
## <a name="remarks"></a>Notes  
 Toute action d’étape reste active jusqu’à ce que le débogueur reçoive un appel [ICorDebugManagedCallback :: StepComplete](icordebugmanagedcallback-stepcomplete-method.md) , qui désactive automatiquement le pas à pas. Une exécution pas à pas peut également être désactivée prématurément en appelant [ICorDebugStepper ::D eactivate](icordebugstepper-deactivate-method.md) avant que la condition de rappel soit atteinte.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
