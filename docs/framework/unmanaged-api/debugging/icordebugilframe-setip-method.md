---
title: ICorDebugILFrame::SetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788555"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP, méthode
Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `nOffset`  
 Emplacement de décalage dans le code MSIL.  
  
## <a name="remarks"></a>Notes  
 Les appels à `SetIP` invalident immédiatement tous les frames et chaînes pour le thread actuel. Si le débogueur a besoin d’informations de frame après un appel à `SetIP`, il doit effectuer une nouvelle trace de la pile.  
  
 [ICorDebug](icordebug-interface.md) tente de conserver le frame de pile dans un état valide. Toutefois, même si le frame est dans un état valide, il peut y avoir des problèmes tels que les variables locales non initialisées. L’appelant est chargé de garantir la cohérence du programme en cours d’exécution.  
  
 Sur les plateformes 64 bits, le pointeur d’instruction ne peut pas être déplacé hors d’un bloc `catch` ou `finally`. Si `SetIP` est appelé pour effectuer ce déplacement sur une plateforme 64 bits, un HRESULT indiquant un échec est retourné.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
