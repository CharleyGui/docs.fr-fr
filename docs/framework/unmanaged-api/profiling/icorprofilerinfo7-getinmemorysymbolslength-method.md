---
title: 'ICorProfilerInfo7 :: GetInMemorySymbolsLength, méthode'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 43d6bdeae5f522bd73b0bdf3a5c403ec69ee384c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495436"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7 :: GetInMemorySymbolsLength, méthode
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Retourne la longueur d’un flux de symboles en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleId`  
 dans Identificateur du module contenant le flux en mémoire.  
  
 pCountSymbolBytes  
 à Pointeur vers une `DWORD` valeur qui, lorsque la méthode est retournée, contient la longueur du flux en octets.  
  
## <a name="return-value"></a>Valeur renvoyée  
 La méthode retourne `S_OK` si la longueur du flux de mémoire peut être déterminée, même si elle est égale à zéro (0).  
  
 La méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC` si la méthode a été créée à l’aide de <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="remarks"></a>Remarques  
 Si le module contient des symboles en mémoire, la longueur du flux est placée dans `pCountSymbolBytes` . Si le module n’a pas de symboles en mémoire, `*pCountSymbolBytes = 0` .  
  
> [!NOTE]
> L’implémentation actuelle ne prend pas en charge la réflexion. Emit. Si le module a été créé à l’aide de Reflection. Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](icorprofilerinfo7-interface.md)
