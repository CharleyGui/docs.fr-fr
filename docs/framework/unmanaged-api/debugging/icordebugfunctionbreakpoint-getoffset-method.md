---
title: ICorDebugFunctionBreakpoint::GetOffset, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
ms.openlocfilehash: 0f6fe5d7eb5926d48809bb6490ba75df9d4a5033
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213149"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a>ICorDebugFunctionBreakpoint::GetOffset, méthode
Obtient l’offset du point d’arrêt dans la fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pnOffset`  
 à Pointeur vers l’offset du point d’arrêt.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
