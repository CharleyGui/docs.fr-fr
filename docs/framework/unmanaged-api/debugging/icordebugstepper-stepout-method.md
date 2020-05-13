---
title: ICorDebugStepper::StepOut, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 9f6962f987079da1ccb04ea368307d7c119910a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379507"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut, méthode
Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Notes   
 Une `StepOut` opération se termine après avoir été retournée normalement du frame actuel au frame appelant.  
  
 Si `StepOut` est appelé lorsque, dans du code non managé, l’étape se termine lorsque le frame actuel retourne au code managé qui l’a appelé.  
  
 Dans la version 2,0 de .NET Framework, n’utilisez pas `StepOut` avec l’indicateur STOP_UNMANAGED défini, car il échouera. (Utilisez [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) pour définir des indicateurs pour l’exécution pas à pas.) Les débogueurs d’interopérabilité doivent effectuer eux-mêmes un pas à pas sortant du code natif.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
