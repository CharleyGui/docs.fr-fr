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
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178876"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle, méthode
Crée une poignée du type spécifié pour la valeur de tas représentée par cet objet ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `type`  
 [dans] Une valeur du recensement CorDebugHandleType qui spécifie le type de poignée à créer.  
  
 `ppHandle`  
 [out] Un pointeur à l’adresse d’un objet ICorDebugHandleValue qui représente la nouvelle poignée pour cette valeur de tas.  
  
## <a name="remarks"></a>Notes   
 La poignée sera créée dans le domaine de l’application qui est associée à la valeur du tas, et deviendra invalide si le domaine d’application est déchargé.  
  
 Plusieurs appels à cette fonction pour la même valeur de tas créeront plusieurs poignées. Étant donné que les poignées affectent la performance du éboueur, le débagénaire devrait se limiter à un nombre relativement faible de poignées (environ 256) qui sont actives à la fois.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
