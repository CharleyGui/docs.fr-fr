---
title: FunctionLeave3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 495ed887126f0b569acc1309609a0c132d0766eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763308"
---
# <a name="functionleave3withinfo-function"></a>FunctionLeave3WithInfo, fonction
Notifie le profileur que le contrôle a été renvoyé à partir d’une fonction et fournit un handle qui peut être passé à la [ICorProfilerInfo3::GetFunctionLeave3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionIDOrClientID`  
 [in] L’identificateur de la fonction à partir de laquelle le contrôle est retourné.  
  
 `eltInfo`  
 [in] Handle opaque qui représente des informations sur un frame de pile donné. Ce handle est valide uniquement pendant le rappel auquel il est passé.  
  
## <a name="remarks"></a>Notes  
 Le `FunctionLeave3WithInfo` méthode de rappel notifie le profileur que les fonctions sont appelées et permet au profileur d’utiliser le [ICorProfilerInfo3::GetFunctionLeave3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour inspecter la valeur de retour. Pour accéder aux informations de valeur de retour, le `COR_PRF_ENABLE_FUNCTION_RETVAL` indicateur doit être défini. Le profileur peut utiliser le [ICorProfilerInfo::SetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser le [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.  
  
 Le `FunctionLeave3WithInfo` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser le `__declspec(naked)` attribut de classe de stockage.  
  
 Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris celles dans l’unité de virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionLeave3WithInfo` ne doivent pas bloquer, car il sera retarder le garbage collection. L’implémentation ne doit pas tenter un garbage collection, car la pile est peut-être pas dans un état de la collection convivial garbage. Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionLeave3WithInfo` retourne.  
  
 Le `FunctionLeave3WithInfo` (fonction) ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée en aucune façon.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
