---
title: ICorProfilerInfo::GetILToNativeMapping, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: 1eb9b3af4c0e77fd1548de194d064eb85b86cdce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724154"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping, méthode

Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la fonction spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `functionId`  
 [in] ID de la fonction contenant le code.  
  
 `cMap`  
 [in] Taille maximale du tableau `map`.  
  
 `pcMap`  
 [out] Nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.  
  
 `map`  
 [out] Tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP` qui spécifient chacune les offsets. Suite au retour de la méthode `GetILToNativeMapping`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Remarques  

 La méthode `GetILToNativeMapping` retourne un tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP`. Pour indiquer que certaines plages d’instructions natives correspondent à des régions de code spéciales (par exemple, le prologue), le champ d’une entrée dans le tableau peut avoir `ilOffset` la valeur de l’énumération [CorDebugIlToNativeMappingTypes,](../debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Suite au retour de `GetILToNativeMapping`, vous devez vérifier que la mémoire tampon `map` est suffisamment grande pour contenir toutes les structures `COR_DEBUG_IL_TO_NATIVE_MAP`. Pour ce faire, comparez la valeur de `cMap` à celle du paramètre `pcMap`. Si la valeur `pcMap`, une fois multipliée par la taille d'une structure `COR_DEBUG_IL_TO_NATIVE_MAP`, est supérieure à `cMap`, allouez une mémoire tampon `map` plus grande, mettez à jour `cMap` pour refléter la nouvelle taille et rappelez `GetILToNativeMapping`.  
  
 Vous pouvez également commencer par appeler `GetILToNativeMapping` avec un tampon `map` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcMap` et rappeler `GetILToNativeMapping`.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [GetILToNativeMapping2, méthode](icorprofilerinfo4-getiltonativemapping2-method.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
