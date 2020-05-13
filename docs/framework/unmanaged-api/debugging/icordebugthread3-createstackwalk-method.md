---
title: ICorDebugThread3::CreateStackWalk, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: f2850e6c9cbb2250a08ab4a0e34c69e377d3a23d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375847"
---
# <a name="icordebugthread3createstackwalk-method"></a>ICorDebugThread3::CreateStackWalk, méthode
Crée un objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppStackWalk`  
 à Pointeur vers l’adresse de l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L' `ICorDebugStackWalk` objet a été créé avec succès.|  
|E_FAIL|L' `ICorDebugStackWalk` objet n’a pas été créé.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarks  
 Si la `CreateStackWalk` méthode est réussie, le `ICorDebugStackWalk` contexte de l’objet retourné est défini sur le contexte actuel du thread.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
