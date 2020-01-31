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
ms.openlocfilehash: e77344a99189ec8e234129262d45698c794dc249
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788512"
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
  
## <a name="parameters"></a>Parameters  
 `flags`  
 dans Membre de l’énumération [ILCodeKind](ilcodekind-enumeration.md) qui spécifie si le langage intermédiaire (il) défini par la demande ReJIT du profileur est inclus dans le frame.  
  
 `ppCode`  
 à Pointeur vers l’adresse d’un objet « ICorDebugCode » qui représente le code exécuté par ce frame de pile.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est similaire à la méthode [ICorDebugFrame :: GetCode](icordebugframe-getcode-method.md) , à ceci près qu’elle accède éventuellement au code défini par la requête ReJIT du profileur. L’appel de cette méthode avec une valeur `flags` de `ILCODE_ORIGINAL_IL` équivaut à appeler [GetCode](icordebugframe-getcode-method.md); Si la méthode est instrumentée, son IL n’est pas accessible. `ILCODE_REJIT_IL` permet au débogueur d'accéder au langage intermédiaire défini par la demande ReJIT du profileur. Si le langage intermédiaire n’est pas instrumenté, `ppCode` a la **valeur null**et la méthode retourne `S_OK`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugILFrame4, interface](icordebugilframe4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [ReJIT : Guide pratique](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
