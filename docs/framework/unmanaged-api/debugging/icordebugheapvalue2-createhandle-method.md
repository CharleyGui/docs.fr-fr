---
title: ICorDebugHeapValue2::CreateHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: b9eab1274f2d0ad562c0dec6adeddb85c6cfc458
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138389"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle, méthode
Crée un handle du type spécifié pour la valeur de tas représentée par cet objet ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `type`  
 dans Valeur de l’énumération CorDebugHandleType, qui spécifie le type de descripteur à créer.  
  
 `ppHandle`  
 à Pointeur vers l’adresse d’un objet ICorDebugHandleValue qui représente le nouveau handle pour cette valeur de tas.  
  
## <a name="remarks"></a>Notes  
 Le handle sera créé dans le domaine d’application associé à la valeur du tas et deviendra non valide si le domaine d’application est déchargé.  
  
 Plusieurs appels à cette fonction pour la même valeur de tas créeront plusieurs handles. Étant donné que les handles affectent les performances du garbage collector, le débogueur doit se limiter à un nombre relativement faible de handles (environ 256) qui sont actifs à la fois.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
