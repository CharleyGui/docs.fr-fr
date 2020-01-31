---
title: ICorProfilerInfo::GetCodeInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 583189cd667af142ab7d0934be34411644dac936
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863918"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo, méthode
Obtient l'étendue de code natif associée à l'ID de la fonction spécifiée.  
  
 Cette méthode est obsolète. Utilisez la méthode [ICorProfilerInfo2 :: GetCodeInfo2,](icorprofilerinfo2-getcodeinfo2-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parameters  
 `functionId`  
 [in] ID de la fonction à laquelle le code natif est associé.  
  
 `pStart`  
 [out] Pointeur vers un tableau d'octets qui composent le code natif de la fonction.  
  
 `pcSize`  
 [out] Pointeur vers un entier qui spécifie la taille, en octets, du code natif.  
  
## <a name="remarks"></a>Notes  
 Pour optimiser la performance, le runtime dans la version 2.0 du .NET Framework fractionne le code natif précompilé d'une fonction en plusieurs régions. Par conséquent, la méthode `GetCodeInfo` est obsolète dans .NET Framework 2.0, car elle ne peut pas gérer l'étendue du code natif d'une fonction. Les profileurs doivent utiliser la méthode `ICorProfilerInfo2::GetCodeInfo2` plus générale à la place.  
  
 Cette fonction utilise des mémoires tampons allouées par l'appelant.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,0  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
