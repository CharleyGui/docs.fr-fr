---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: d22d789724a62cebb0136b9b01be22d6825384ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714534"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a>ICorProfilerFunctionControl::SetILInstrumentedCodeMap, méthode

Définit une carte de code pour la fonction spécifiée à l’aide des entrées de mappage CIL (Common Intermediate Language) spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cILMapEntries`  
 [en entrée] Le nombre d'entrées de la mappe.  
  
 `rgILMapEntries`  
 [en entrée] Le tableau alloué par l'appelant, contenant des entrées COR_IL_MAP. L’interprétation de ces entrées est la même que pour la méthode [ICorProfilerInfo :: SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) .  
  
## <a name="remarks"></a>Remarques  

 La définition du mappage en appelant cette méthode permet au débogueur de récupérer le mappage en appelant [ICorDebugILCode2 :: getinstrumentedilmap,](../debugging/icordebugilcode2-getinstrumentedilmap-method.md). Elle permet aussi au débogueur d'utiliser le mappage en interne lors du calcul des décalages du langage intermédiaire pour les traces de pile et les cycles de vie des variables.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
