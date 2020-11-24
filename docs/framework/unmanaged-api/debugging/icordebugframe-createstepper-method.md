---
title: ICorDebugFrame::CreateStepper, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 5dfb64d0c440cbd2c8a8a65b2c18d78f02a7615e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679713"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper, méthode

Obtient une exécution pas à pas qui permet au débogueur d’effectuer des opérations pas à pas relatives à ce ICorDebugFrame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppStepper`  
 à Pointeur vers l’adresse d’un objet ICorDebugStepper qui permet au débogueur d’effectuer des opérations pas à pas relatives au frame actuel.  
  
## <a name="remarks"></a>Remarques  

 Si le frame n’est pas actif, l’objet de pas à pas devra généralement revenir au frame avant la fin de l’étape.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
