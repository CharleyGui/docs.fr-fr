---
title: ICorDebugILFrame4::GetCodeEx, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178792"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Obtient un pointeur vers le code exécuté par ce frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `flags`  
 [dans] Un membre de l’énumération [ILCodeKind](ilcodekind-enumeration.md) qui précise si le langage intermédiaire (IL) défini par la demande ReJIT du profileur est inclus dans le cadre.  
  
 `ppCode`  
 [out] Un pointeur à l’adresse d’un objet "ICorDebugCode" qui représente le code que ce cadre de pile exécute.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est similaire à la méthode [ICorDebugFrame::GetCode,](icordebugframe-getcode-method.md) sauf qu’elle accède optionnellement au code défini par la demande ReJIT du profileur. Appeler cette méthode `flags` avec `ILCODE_ORIGINAL_IL` une valeur de est équivalent à appeler [GetCode](icordebugframe-getcode-method.md); si la méthode est instrumentée, son IL ne sera pas accessible. `ILCODE_REJIT_IL` permet au débogueur d'accéder au langage intermédiaire défini par la demande ReJIT du profileur. Si l’IL n’est pas `ppCode` instrumenté, `S_OK`est **nul,** et la méthode revient .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugILFrame4, interface](icordebugilframe4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [ReJIT: Un guide de comment se passer](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
