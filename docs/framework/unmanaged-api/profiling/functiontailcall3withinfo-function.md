---
title: FunctionTailcall3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: 202aed64de78675c79f998afb4483e0d19b811de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445967"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo, fonction
Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionTailcall3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionIDOrClientID`  
 dans Identificateur de la fonction en cours d’exécution qui va effectuer un appel tail.  
  
 `eltInfo`  
 [in] Handle opaque qui représente des informations sur un frame de pile donné. Ce handle est valide uniquement pendant le rappel auquel il est passé.  
  
## <a name="remarks"></a>Notes  
 La méthode de rappel `FunctionTailcall3WithInfo` informe le profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionTailcall3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour inspecter le frame de pile. Pour accéder aux informations de frame de pile, l’indicateur de `COR_PRF_ENABLE_FRAME_INFO` doit être défini. Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.  
  
 La fonction `FunctionTailcall3WithInfo` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec(naked)`.  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionTailcall3WithInfo` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall3WithInfo` retourne.  
  
 En outre, la fonction FunctionTailcall3WithInfo ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [Setenterleavefunctionhooks3,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withinfo,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
