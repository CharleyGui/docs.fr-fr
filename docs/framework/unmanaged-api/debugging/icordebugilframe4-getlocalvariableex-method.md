---
title: ICorDebugILFrame4::GetLocalVariableEx, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178779"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Extrait la valeur de la variable locale spécifiée dans ce frame de pile de langage intermédiaire, et peut aussi accéder à une variable ajoutée dans l'instrumentation ReJIT du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `flags`  
 [dans] Un membre de recensement [ILCodeKind](ilcodekind-enumeration.md) qui précise si une variable ajoutée dans l’instrumentation du profileur ReJIT est incluse dans le cadre.  
  
 `dwIndex`  
 [en entrée] L'index de la variable locale dans le frame de pile de langage intermédiaire.  
  
 `ppValue`  
 [out] Un pointeur à l’adresse d’un objet "ICorDebugValue" qui représente la valeur récupérée.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est similaire à la méthode [GetLocalVariable,](icordebugilframe-getlocalvariable-method.md) sauf qu’elle accède optionnellement à une variable ajoutée dans l’instrumentation profiler ReJIT. Appeler cette méthode `flags` avec `ILCODE_ORIGINAL_IL` une valeur de est équivalent à appeler [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); si la méthode est instrumentée avec d’autres variables locales, ces variables ne peuvent pas être consultées. `ILCODE_REJIT_IL` autorise le débogueur à accéder aux variables locales ajoutées dans l'instrumentation ReJIT du profileur. Si le langage intermédiaire n'est pas instrumenté, la méthode retourne `E_INVALIDARG`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugILFrame4, interface](icordebugilframe4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [ReJIT: Un guide de comment se passer](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
