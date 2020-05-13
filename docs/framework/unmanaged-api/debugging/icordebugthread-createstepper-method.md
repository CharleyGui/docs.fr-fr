---
title: ICorDebugThread::CreateStepper, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: a74d32478bc88ee634fa5ff9b61ac2059bc8e302
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379714"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper, méthode
Crée un objet ICorDebugStepper qui permet d’effectuer un pas à pas détaillé dans le frame actif de ce ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppStepper`  
 à Pointeur vers l’adresse d’un `ICorDebugStepper` objet qui permet d’effectuer un pas à pas détaillé dans le frame actif de ce thread.  
  
## <a name="remarks"></a>Remarks  
 Le frame actif peut être du code non managé.  
  
 L' `ICorDebugStepper` interface doit être utilisée pour exécuter le pas à pas réel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
