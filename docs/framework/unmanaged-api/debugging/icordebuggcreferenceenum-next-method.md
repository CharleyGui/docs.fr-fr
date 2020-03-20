---
title: ICorDebugGCReferenceEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178866"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next, méthode
Obtient le nombre spécifié de [cas COR_GC_REFERENCE](cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui seront collectés à ordures.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 celt  
 [dans] Le nombre de racines à récupérer.  
  
 Racines  
 [out] Un tableau de pointeurs, chacun pointant vers un [objet COR_GC_REFERENCE](cor-gc-reference-structure.md) qui représente la racine d’un objet à collecter des ordures.  
  
 pceltFetched  
 [out] Un pointeur sur le nombre d’objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) effectivement retourné dans `roots`. Cette valeur peut être `null` si `celt` est égal à 1.  
  
## <a name="remarks"></a>Notes   
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugGCReferenceEnum, interface](icordebuggcreferenceenum-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
