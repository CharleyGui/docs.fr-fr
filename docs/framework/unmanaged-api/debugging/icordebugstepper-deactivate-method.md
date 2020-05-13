---
title: ICorDebugStepper::Deactivate, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 760f69baf311cf320e9c358ba1c45c942934f1a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379394"
---
# <a name="icordebugstepperdeactivate-method"></a>ICorDebugStepper::Deactivate, méthode
Fait en sorte que ces ICorDebugStepper annulent la dernière commande d’étape qu’il a reçue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a>Notes   
 Une nouvelle commande pas à pas peut être émise après l’annulation de la dernière commande de l’étape reçue.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
