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
ms.openlocfilehash: 0aa43954c3e10d04524bf976d0dd3b29d2bc724c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866815"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo, fonction
Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parameters  

- `functionIDOrClientID`

  \[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.

- `eltInfo`

  \[dans] handle opaque qui représente des informations sur un frame de pile donné. Ce handle est valide uniquement pendant le rappel auquel il est passé.

## <a name="remarks"></a>Notes  
 La méthode de rappel `FunctionTailcall3WithInfo` informe le profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour inspecter le frame de pile. Pour accéder aux informations de frame de pile, l’indicateur de `COR_PRF_ENABLE_FRAME_INFO` doit être défini. Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.  
  
 La fonction `FunctionTailcall3WithInfo` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec(naked)`.  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionTailcall3WithInfo` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall3WithInfo` retourne.  
  
 En outre, la fonction FunctionTailcall3WithInfo ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functiontailcall3-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Fonctions statiques globales de profilage](profiling-global-static-functions.md)
