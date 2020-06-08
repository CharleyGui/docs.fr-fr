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
ms.openlocfilehash: 235bae64fe5e6a534f2a650050c6c9ad4aa8fe84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500622"
---
# <a name="functionleave3withinfo-function"></a>FunctionLeave3WithInfo, fonction
Indique au profileur que le contrôle est retourné à partir d’une fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Paramètres

- `functionIDOrClientID`

  \[in] identificateur de la fonction à partir de laquelle le contrôle est retourné.

- `eltInfo`

  \[in] handle opaque qui représente des informations sur un frame de pile donné. Ce handle est valide uniquement pendant le rappel auquel il est passé.

## <a name="remarks"></a>Remarques  
 La `FunctionLeave3WithInfo` méthode de rappel indique au profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour inspecter la valeur de retour. Pour accéder aux informations de valeur de retour, l' `COR_PRF_ENABLE_FUNCTION_RETVAL` indicateur doit être défini. Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.  
  
 La `FunctionLeave3WithInfo` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l' `__declspec(naked)` attribut de classe de stockage.  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de ne `FunctionLeave3WithInfo` doit pas se bloquer, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave3WithInfo` retourne la valeur.  
  
 La `FunctionLeave3WithInfo` fonction ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Getfunctionleave3info,](icorprofilerinfo3-getfunctionleave3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Setenterleavefunctionhooks3,](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withinfo,](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2,](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)
