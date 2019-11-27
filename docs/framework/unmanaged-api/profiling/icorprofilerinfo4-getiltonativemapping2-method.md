---
title: ICorProfilerInfo4::GetILToNativeMapping2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: dfce86e95ba41a65e72524546072244a47f8360c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442925"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2, méthode
Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la version recompilée juste-à-temps de la fonction spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] ID de la fonction contenant le code.  
  
 `pReJitId`  
 [in] Identité de la fonction recompilée juste-à-temps. L’identité doit être égale à zéro dans le .NET Framework 4,5.  
  
 `cMap`  
 [in] Taille maximale du tableau `map`.  
  
 `pcMap`  
 [out] Nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.  
  
 `map`  
 [out] Tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP` qui spécifient chacune les offsets. Suite au retour de la méthode `GetILToNativeMapping2`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Notes  
 `GetILToNativeMapping2` est semblable à la méthode [ICorProfilerInfo :: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) , à la différence qu’elle permet au profileur de spécifier l’ID de la fonction recompilée dans les versions ultérieures.  
  
> [!NOTE]
> La méthode [ICorProfilerFunctionControl :: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) n’est pas implémentée dans le .NET Framework 4,5. par conséquent, les fonctions qui ont été recompilées juste-à-temps ne peuvent pas avoir un mappage il-à-natif qui diffère de la fonction initialement compilée. Par conséquent, `GetILToNativeMapping2` ne peut pas être appelée avec un ID recompilé juste-à-temps dans le .NET Framework 4,5.  
  
 La méthode `GetILToNativeMapping2` retourne un tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP`. Pour indiquer que certaines plages d’instructions natives correspondent à des régions de code spéciales (par exemple, le prologue), le champ `ilOffset` de l’entrée du tableau peut être défini sur une valeur de l’énumération [CorDebugIlToNativeMappingTypes,](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Suite au retour de `GetILToNativeMapping2`, vous devez vérifier que la mémoire tampon `map` est suffisamment grande pour contenir toutes les structures `COR_DEBUG_IL_TO_NATIVE_MAP`. Pour ce faire, comparez la valeur de `cMap` à celle du paramètre `pcMap`. Si la valeur `pcMap`, une fois multipliée par la taille d'une structure `COR_DEBUG_IL_TO_NATIVE_MAP`, est supérieure à `cMap`, allouez une mémoire tampon `map` plus grande, mettez à jour `cMap` pour refléter la nouvelle taille et rappelez `GetILToNativeMapping2`.  
  
 Vous pouvez également commencer par appeler `GetILToNativeMapping2` avec un tampon `map` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcMap` et rappeler `GetILToNativeMapping2`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetILToNativeMapping, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
