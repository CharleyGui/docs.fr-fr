---
title: FunctionTailcall2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175185"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 (fonction)
Informe le profileur que la fonction d’exécution actuelle est sur le point d’effectuer un appel de queue à une autre fonction et fournit des informations sur le cadre de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcId`

  \[dans] L’identifiant de la fonction d’exécution actuelle qui est sur le point de faire un appel de queue.

- `clientData`

  \[dans] L’identifiant de fonction remapped, que le profileur précédemment spécifié via [FunctionIDMapper](functionidmapper-function.md), de la fonction d’exécution actuellement qui est sur le point de faire un appel de queue.
  
- `func`

  \[dans] `COR_PRF_FRAME_INFO` Une valeur qui indique des informations sur le cadre de pile.

  Le profileur doit traiter cela comme une poignée opaque qui peut être transmis au moteur d’exécution dans la méthode [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)

## <a name="remarks"></a>Notes   
 La fonction cible de l’appel de queue utilisera le cadre de pile actuel, et retournera directement à l’appelant de la fonction qui a fait l’appel de queue. Cela signifie qu’un rappel [FunctionLeave2](functionleave2-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel de queue.  
  
 La valeur `func` du paramètre n’est pas valide après le retour de la `FunctionTailcall2` fonction parce que la valeur peut changer ou être détruite.  
  
 La `FunctionTailcall2` fonction est un rappel; vous devez le mettre en œuvre. La mise en `__declspec``naked`œuvre doit utiliser l’attribut de la classe de stockage.  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à point flottant (FPU).  
  
- À la sortie, vous devez restaurer la pile en sortant de tous les paramètres qui ont été poussés par son appelant.  
  
 La mise `FunctionTailcall2` en œuvre de ne devrait pas bloquer parce qu’elle retardera la collecte des ordures. La mise en œuvre ne devrait pas tenter une collecte des ordures parce que la pile peut ne pas être dans un état de collecte des ordures. Si une collecte d’ordures est tentée, le temps d’exécution se bloque jusqu’à ce que `FunctionTailcall2` le retour.  
  
 En outre, la `FunctionTailcall2` fonction ne doit pas appeler dans le code géré ou en aucune façon provoquer une allocation de mémoire gérée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2 (fonction)](functionenter2-function.md)
- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)
