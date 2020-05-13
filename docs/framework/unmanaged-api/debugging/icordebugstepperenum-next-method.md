---
title: ICorDebugStepperEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: 293d1a9cd93b5ce45105427e7df864ad8bfbe77a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379190"
---
# <a name="icordebugstepperenumnext-method"></a>ICorDebugStepperEnum::Next, méthode
Obtient le nombre spécifié d’instances de ICorDebugStepper à partir de l’énumération, en commençant à la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `celt`  
 dans Nombre d' `ICorDebugStepper` instances à récupérer.  
  
 `steppers`  
 à Tableau de pointeurs, chacun pointant vers un `ICorDebugStepper` objet.  
  
 `pceltFetched`  
 à Pointeur vers le nombre d' `ICorDebugStepper` instances réellement retournées. Cette valeur peut être null si `celt` est un.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
