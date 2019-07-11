---
title: ICorDebugFrame::GetStackRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9f58e66286f5e3e169507efd2f87ce10e9d323b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754858"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange, méthode
Obtient la plage d’adresses absolues de ce frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pStart`  
 [out] Un pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de départ du frame de pile représenté par cet `ICorDebugFrame` objet.  
  
 `pEnd`  
 [out] Un pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de fin du frame de pile représenté par cet `ICorDebugFrame` objet.  
  
## <a name="remarks"></a>Notes  
 La plage d’adresses de la pile est utile pour rassembler des traces de pile entrelacées à partir de plusieurs moteurs de débogage. La plage numérique ne fournit aucune information sur le contenu du frame de pile. Il est pertinent uniquement pour la comparaison des emplacements de frame de pile.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
