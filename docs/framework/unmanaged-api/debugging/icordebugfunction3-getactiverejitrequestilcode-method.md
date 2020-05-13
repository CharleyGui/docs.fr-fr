---
title: ICorDebugFunction3::GetActiveReJitRequestILCode, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 9e7f682752cfefae63b574655a4fc5e8964146a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213177"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Obtient un pointeur d’interface vers un [ICorDebugILCode](icordebugilcode-interface.md) qui contient le langage intermédiaire d’une requête ReJIT active.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppReJitedILCode`  
 Un pointeur depuis une demande ReJIT active vers le langage intermédiaire.  
  
## <a name="remarks"></a>Remarks  
 Si la méthode représentée par cet objet `ICorDebugFunction3` a une demande ReJIT active, `ppReJitedILCode` retourne un pointeur vers son langage intermédiaire. S’il n’y a aucune requête active, ce qui est un cas courant, `ppReJitedILCode` est **null**.  
  
 Une requête ReJIT devient active juste après le retour de l’exécution de l’appel de la méthode [ICorProfilerCallback4 :: getrejitparameters,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) . Il est possible qu'elle ne soit pas encore compilée en mode juste-à-temps et que des threads soient toujours en cours d'exécution dans la version d'origine du code. Une requête ReJIT devient inactive pendant l’appel du profileur à la méthode [ICorProfilerInfo4 :: requestrevert,](../profiling/icorprofilerinfo4-requestrevert-method.md) . Même après le rétablissement du langage intermédiaire, un thread peut toujours être en train d'exécuter le code ReJIT (recompilé en mode juste-à-temps).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugFunction3, interface](icordebugfunction3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [ReJIT : Guide pratique](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
