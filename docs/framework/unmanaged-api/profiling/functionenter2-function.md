---
title: FunctionEnter2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177057"
---
# <a name="functionenter2-function"></a>FunctionEnter2 (fonction)
Informe le profileur que le contrôle est passé à une fonction et fournit des informations sur le cadre de pile et les arguments de fonction. Cette fonction remplace la fonction [FunctionEnter.](functionenter-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcId`

  \[dans] l’identifiant de la fonction à laquelle le contrôle est passé.

- `clientData`

  \[dans] L’identifiant de fonction remapped, que le profileur a précédemment spécifié en utilisant la fonction [FunctionIDMapper.](functionidmapper-function.md)
  
- `func`

  \[dans] `COR_PRF_FRAME_INFO` Une valeur qui indique des informations sur le cadre de pile.
  
  Le profileur doit traiter cela comme une poignée opaque qui peut être transmis au moteur d’exécution dans la méthode [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- `argumentInfo`

  \[dans] Un pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) qui spécifie les emplacements en mémoire des arguments de la fonction.

  Afin d’accéder aux `COR_PRF_ENABLE_FUNCTION_ARGS` informations d’argumentation, le drapeau doit être fixé. Le profileur peut utiliser la méthode [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les drapeaux de l’événement.

## <a name="remarks"></a>Notes   
 Les valeurs `func` et `argumentInfo` les paramètres ne `FunctionEnter2` sont pas valides après le retour de la fonction parce que les valeurs peuvent changer ou être détruites.  
  
 La `FunctionEnter2` fonction est un rappel; vous devez le mettre en œuvre. La mise en `__declspec``naked`œuvre doit utiliser l’attribut de la classe de stockage.  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à point flottant (FPU).  
  
- À la sortie, vous devez restaurer la pile en sortant de tous les paramètres qui ont été poussés par son appelant.  
  
 La mise `FunctionEnter2` en œuvre de ne devrait pas bloquer parce qu’elle retardera la collecte des ordures. La mise en œuvre ne devrait pas tenter une collecte des ordures parce que la pile peut ne pas être dans un état de collecte des ordures. Si une collecte d’ordures est tentée, le temps d’exécution se bloque jusqu’à ce que `FunctionEnter2` le retour.  
  
 En outre, la `FunctionEnter2` fonction ne doit pas appeler dans le code géré ou en aucune façon provoquer une allocation de mémoire gérée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [FunctionTailcall2 (fonction)](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)
