---
title: ICorDebugFunctionBreakpoint::GetFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
ms.openlocfilehash: 79a6c70399d5059d6959ac6127f22807138c00fa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213112"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a>ICorDebugFunctionBreakpoint::GetFunction, méthode
Obtient un pointeur d’interface vers un ICorDebugFunction qui fait référence à la fonction dans laquelle le point d’arrêt est défini.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppFunction`  
 à Pointeur vers l’adresse de la fonction dans laquelle le point d’arrêt est défini.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
