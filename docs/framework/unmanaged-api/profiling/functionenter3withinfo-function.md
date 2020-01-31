---
title: FunctionEnter3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: 75a9a7174f105d99e9d1c9b220cfc5bf928d46ec
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866968"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo, fonction
Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parameters

- `functionIDOrClientID`

  \[in] identificateur de la fonction vers laquelle le contrôle est passé.

- `eltInfo`

  \[dans] handle opaque qui représente des informations sur un frame de pile donné. Ce handle est valide uniquement pendant le rappel auquel il est passé.

## <a name="remarks"></a>Notes  
 La méthode de rappel `FunctionEnter3WithInfo` informe le profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour inspecter les valeurs des arguments. Pour accéder aux informations d’argument, l’indicateur de `COR_PRF_ENABLE_FUNCTION_ARGS` doit être défini. Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.  
  
 La fonction `FunctionEnter3WithInfo` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec(naked)`.  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionEnter3WithInfo` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter3WithInfo` retourne.  
  
 La fonction `FunctionEnter3WithInfo` ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [Fonctions statiques globales de profilage](profiling-global-static-functions.md)
